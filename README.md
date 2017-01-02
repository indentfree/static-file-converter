# static-file-converter
Simple static file server with ANSI color to HTML converter written in a single python script.

Very useful to read unix text file containing color using web browser :
 - convert ANSI code color like '\033[31m;' to HTML ( foreground and background color only)
 - convert authorized_path detected in content to hyperlink (easy to follow file with full path)
 
 [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code#Colors)
 
Security options :
 - allow basic authentification
 - path restriction using regex 
 
 ## exemple
 
 ### to see usage :
 ``` 
 python static-file-converter.py --help
 ``` 
 
 ### to serve default folder (~/log) using specific port 8888
 ``` 
 python static-file-converter.py --port 8888
 ``` 
 
 ### to serve specific folders
 ``` 
 python static-file-converter.py --path /var/\S*/log/\S* /home/specific_user/log/\S* /environnements/\S*/logs/\S*
 ``` 
  
 ### to serve specific folders with basic authentification
 ``` 
 python static-file-converter.py --path /var/\S*/log/\S* /home/specific_user/log/\S* /environnements/\S*/logs/\S* --auth admin:sEcReT
  ``` 
 
 ## 3 styles are available using option --style : 
 - custom
 - dark (defaut unix terminal)
 - light (invert black and white color)

![alt tag](https://github.com/indentfree/static-file-converter/blob/master/expected_ansi_html.png)


