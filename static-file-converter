# -*- coding: utf-8 -*-
import os,sys,re,itertools,BaseHTTPServer,SimpleHTTPServer,urlparse,base64,argparse

description=r"""Simple static file server converter :
 - convert ANSI code color like '\033[31m;' to HTML ( foreground and background color only)
 - convert authorized_path detected in content to hyperlink
 - allow basic authentification
 multi path are allowed and each  must be a valid regex, exemple :
 --path /var/\S*/logs/\S* /home/specific_user/log/\S* /environnements/\S*/logs/\S*
"""

style={           # https://en.wikipedia.org/wiki/ANSI_escape_code    
    'dark'  : {   # 39=default text color, 49 default background color, 0=reset all
        'fgcolor' : {'30':'black','31':'red','32':'green','33':'yellow','34':'blue','35':'magenta','36':'cyan','37':'white','39':'white','0':'white'},
        'bgcolor' : {'40':'black','41':'red','42':'green','43':'yellow','44':'blue','45':'magenta','46':'cyan','47':'black','49':'black','0':'black'},
        'name'    : 'dark'},
    'light'  : {
        'fgcolor' : {'30':'white','31':'red','32':'green','33':'yellow','34':'blue','35':'magenta','36':'cyan','37':'black','39':'black','0':'black'},
        'bgcolor' : {'40':'white','41':'red','42':'green','43':'yellow','44':'blue','45':'magenta','46':'cyan','47':'white','49':'white','0':'white'},
        'name'    : 'light'},
    'custom'  : {
        'fgcolor' : {'30':'Ivory','31':'FireBrick','32':'SeaGreen','33':'Gold','34':'SteelBlue','35':'Purple','36':'LightSeaGreen','37':'DarkSlateGray','39':'DarkSlateGray','0':'DarkSlateGray'},
        'bgcolor' : {'40':'Ivory','41':'FireBrick','42':'SeaGreen','43':'Gold','44':'SteelBlue','45':'Purple','46':'LightSeaGreen','47':'Ivory','49':'Ivory','0':'Ivory'},
        'name'    : 'custom'},
}
default_style=style['custom']

# on compile la regex 1 seule fois au lancement
regexp_split=re.compile(r'''# permet de trouver les codes ansi du style : \033[36m, \033[36;42m ou \033[m
    (?P<ansicode>           # debut du groupe 1 nommé ansicode (re.split ne gère par les groupes nommés)
    %(esc)s                 # valeur du code "escape" injecte par template
    \[                      # le caratere crochet
        (?P<codes>          # debut du groupe 2 nommé codes
        [0-9;]*             # les codes ansi (pouvant être multiple et séparé par de ;)
        )                   # fin du groupe 2
    m                       # le caractere m de fin
    )                       # fin du groupe 1
'''%{'esc':'\033'},
    re.MULTILINE|re.VERBOSE|re.DOTALL
)

def grouper(iterable, n, fillvalue=None):
    "Collect data into fixed-length chunks or blocks"
    # grouper('ABCDEFG', 3, 'x') --> ABC DEF Gxx
    args = [iter(iterable)] * n
    return itertools.izip_longest(fillvalue=fillvalue, *args)

def colorizeAll(text,style=default_style):
    fgcolor=style['fgcolor']['39']#default white
    bgcolor=style['bgcolor']['49']#default black

    result='<span style="color:%(fgcolor)s;background-color:%(bgcolor)s">' %vars()

    # re.split retourne les éléments entre les séparateurs + le separateur capturé (groupe positionnel et pas nommé)
    for (subtext,ansicode,codes) in grouper(regexp_split.split(text),3,fillvalue='') :
        for code in codes.split(";") :
            fgcolor=style['fgcolor'].get(code) or fgcolor
            bgcolor=style['bgcolor'].get(code) or bgcolor
            if (code=='7') :
                (fgcolor,bgcolor)=(bgcolor,fgcolor)

        span=r'''</span><span style="color:%(fgcolor)s;background-color:%(bgcolor)s">''' % vars()
        result=result+subtext+span

    return result+'</span>'

def addLink(content,style=default_style) :
    style_name=style['name']
    return authorized_path.sub(
    r'''<a href="./?filename=\g<filename>&style=%(style_name)s">\g<filename></a>'''%vars()
    ,content)

def toHTML(content,style=default_style) :
    fgcolor=style['fgcolor']['39']#default white
    bgcolor=style['bgcolor']['49']#default black
    return """<html><head></head>
    <body link="%(fgcolor)s" vlink="%(fgcolor)s" alink="%(fgcolor)s" style="background:%(bgcolor)s;">
        <pre style="font:normal 16px/1 Lucida Console;%(fgcolor)s:white;background:%(bgcolor)s;">%(content)s</pre>
    </body></html>"""%vars()

class GetHandler(SimpleHTTPServer.SimpleHTTPRequestHandler):

    def do_GET(self):
        global key
        if key != None and self.headers.getheader('Authorization') == None :
            self.do_AUTHHEAD()
            self.wfile.write('no auth header received')
            pass
        elif key == None or self.headers.getheader('Authorization') == 'Basic '+key :
            self.do_AUTHGET()
            pass
        else:
            self.do_AUTHHEAD()
            self.wfile.write(self.headers.getheader('Authorization'))
            self.wfile.write('not authenticated')
            pass

    def do_AUTHHEAD(self):
        self.send_response(401)
        self.send_header('WWW-Authenticate', 'Basic realm="Identification"')
        self.send_header('Content-type', 'text/html')
        self.end_headers()

    def do_AUTHGET(self):
        parsed_path = urlparse.urlparse(self.path)
        parsed_query= urlparse.parse_qs(parsed_path[4]) # indice 4 ==query

        self.custom_style=default_style
        if (parsed_query.has_key("style")) :
            if parsed_query["style"][0] in style.keys() :
                self.custom_style=style[parsed_query["style"][0]]
        if (parsed_query.has_key("filename")) :
            filename=parsed_query["filename"][0]
            print filename
            if (not authorized_path.match(filename)) :
                self.sendForbidden(filename)
            elif (os.path.isdir(filename)) :
                self.sendListDir(filename)
            elif (not os.path.isfile(filename)) :
                self.sendNotFound(filename)
            else :
                self.sendFile(filename)
        return

    def sendForbidden(self,filename,message="Resources Forbidden : %(filename)s") :
        self.sendError(403,message%vars())
        return

    def sendNotFound(self,filename,message="Resources not found : %(filename)s") :
        self.sendError(404,message%vars())
        return

    def sendError(self,code,message) :
        print message
        self.send_response(code)
        self.end_headers()
        self.wfile.write(message)
        return

    def sendListDir(self,filename,onlyfile=False) :
        files=[os.path.join(filename, f) for f in os.listdir(filename) if (not onlyfile or os.path.isfile(os.path.join(filename, f)))]
        files.sort()
        files.reverse()
        content = "\n".join(files)

        content=addLink(content,self.custom_style)
        self.sendContent(content)

    def sendFile(self,filename) :
        # lecture du contenu du fichier
        fo = open(filename, "r")
        content = "".join(fo.readlines())
        content = re.sub(' *\r','',content)
        try :
            content=content.decode("utf8")
        except Exception as e:
            print "WARN : %(filename)s not in UTF8 (read) %(e)s"%vars()
        fo.close()

        content=colorizeAll(content,self.custom_style)
        content=addLink(content,self.custom_style)
        self.sendContent(content)

    def sendContent(self,content) :
        self.send_response(200)
        self.send_header("Content-type", "text/html; charset=UTF-8")
        self.end_headers()
        self.wfile.write(toHTML(content,self.custom_style).encode("utf8"))

try:    
    parser = argparse.ArgumentParser(description=description,formatter_class=argparse.RawDescriptionHelpFormatter)        
    parser.add_argument("--port",  help="Specifies the port on which the server listens for connections",default=2178, type=int)    
    parser.add_argument("--style", help="Color style",                                                   default="custom", choices=style.keys())
    parser.add_argument("--auth",  help="basic authentication, username:password",                       default=None )
    parser.add_argument("--path",  help="regex to authorized path,by default ~/log ",                    default=[os.path.expanduser("~")+r"/log/\S*"], nargs='*')
    args = parser.parse_args()    
    print args   
    pattern=r'''(?P<filename>(?:'''+("|".join(args.path))+'''))'''
    try :        
        authorized_path=re.compile(pattern)
    except Exception as e:        
        print "%(e)s\nCheck your PATHS, unable to compile pattern :%(pattern)s"%vars()
        sys.exit(255)        
    
    default_style=style[args.style]
    key = None if args.auth==None else base64.b64encode(args.auth)            
    print 'Server running on port %(port)s ...' % vars(args)
    server = BaseHTTPServer.HTTPServer(('', args.port), GetHandler)
    server.serve_forever()

except KeyboardInterrupt:
    server.socket.close()
    
