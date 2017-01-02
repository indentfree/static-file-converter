#static-file-converter
Simple static file server with ANSI color to HTML converter writting in single python script.

Very usefull to read unix log file using web browser :
 - convert ANSI code color like '\033[31m;' to HTML ( foreground and background color only)
 - convert authorized_path detected in content to hyperlink (easy to follow file log)
 
For security :
 - allow basic authentification
 - path restriction using regex 
 
 multi path are allowed and each must be a valid regex, exemple : 
 ``` 
 --path /var/\S*/logs/\S* /home/specific_user/log/\S* /environnements/\S*/logs/\S*
 ``` 
 
 #3 styles are available : 
 - custom
 - dark (defaut unix terminal)
 - light (invert black and white color)

![alt tag](https://github.com/indentfree/static-file-converter/blob/master/expected_ansi_html.png)


