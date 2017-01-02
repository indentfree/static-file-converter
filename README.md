# static-file-converter
Simple static file server with ANSI color to HTML converter writting in a single python script.

Very usefull to read unix text file containing color using web browser :
 - convert ANSI code color like '\033[31m;' to HTML ( foreground and background color only)
 - convert authorized_path detected in content to hyperlink (easy to follow file with full path)
 
For security :
 - allow basic authentification
 - path restriction using regex 
 
 ## exemple
 
 ### to see usage :
 ``` 
 python static-file-converter.py --help
 ``` 
 
 ### to serve default folder (~/log) using port 8888
 ``` 
 python static-file-converter.py --port 8888
 ``` 
 
 ### to serve specifics folders
 ``` 
 python static-file-converter.py --path /var/\S*/log/\S* /home/specific_user/log/\S* /environnements/\S*/logs/\S*
 ``` 
  
 ### to serve specifics folders with basic authentification
 ``` 
 python static-file-converter.py --path /var/\S*/log/\S* /home/specific_user/log/\S* /environnements/\S*/logs/\S* --auth admin:sEcReT
  ``` 
 
 ## 3 styles are available using option --style : 
 - custom
 - dark (defaut unix terminal)
 - light (invert black and white color)

![alt tag](https://github.com/indentfree/static-file-converter/blob/master/expected_ansi_html.png)


