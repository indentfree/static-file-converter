#static-file-converter
Simple static file server with ANSI color to HTML converter

Simple static file server converter :
 - convert ANSI code color like '\033[31m;' to HTML ( foreground and background color only)
 - convert authorized_path detected in content to hyperlink
 - allow basic authentification
 multi path are allowed and each  must be a valid regex, exemple :
 ``` 
 --path /var/\S*/logs/\S* /home/specific_user/log/\S* /environnements/\S*/logs/\S*
 ``` 

![alt tag](https://github.com/indentfree/static-file-converter/blob/master/expected_ansi_html.png)


