# static-file-converter
Simple static file server with ANSI color to HTML converter

Simple static file server converter :
 - convert ANSI code color like '\033[31m;' to HTML ( foreground and background color only)
 - convert authorized_path detected in content to hyperlink
 - allow basic authentification
 multi path are allowed and each  must be a valid regex, exemple :
 ``` 
 --path /var/\S*/logs/\S* /home/specific_user/log/\S* /environnements/\S*/logs/\S*
 ```


<pre style="font:normal 16px/1 Lucida Console;DarkSlateGray:white;background:Ivory;"><span style="color:DarkSlateGray;background-color:Ivory">                    40m       41m       42m       43m       44m       45m       46m       47m
    m  </span><span style="color:DarkSlateGray;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
   1m  </span><span style="color:DarkSlateGray;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
  30m  </span><span style="color:Ivory;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Ivory;background-color:Ivory"></span><span style="color:Ivory;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Ivory;background-color:Ivory"></span><span style="color:Ivory;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Ivory;background-color:Ivory"></span><span style="color:Ivory;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Ivory;background-color:Ivory"></span><span style="color:Ivory;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Ivory;background-color:Ivory"></span><span style="color:Ivory;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Ivory;background-color:Ivory"></span><span style="color:Ivory;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Ivory;background-color:Ivory"></span><span style="color:Ivory;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Ivory;background-color:Ivory"></span><span style="color:Ivory;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
1;30m  </span><span style="color:Ivory;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Ivory;background-color:Ivory"></span><span style="color:Ivory;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Ivory;background-color:Ivory"></span><span style="color:Ivory;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Ivory;background-color:Ivory"></span><span style="color:Ivory;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Ivory;background-color:Ivory"></span><span style="color:Ivory;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Ivory;background-color:Ivory"></span><span style="color:Ivory;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Ivory;background-color:Ivory"></span><span style="color:Ivory;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Ivory;background-color:Ivory"></span><span style="color:Ivory;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Ivory;background-color:Ivory"></span><span style="color:Ivory;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
  31m  </span><span style="color:FireBrick;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:FireBrick;background-color:Ivory"></span><span style="color:FireBrick;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:FireBrick;background-color:Ivory"></span><span style="color:FireBrick;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:FireBrick;background-color:Ivory"></span><span style="color:FireBrick;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:FireBrick;background-color:Ivory"></span><span style="color:FireBrick;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:FireBrick;background-color:Ivory"></span><span style="color:FireBrick;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:FireBrick;background-color:Ivory"></span><span style="color:FireBrick;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:FireBrick;background-color:Ivory"></span><span style="color:FireBrick;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:FireBrick;background-color:Ivory"></span><span style="color:FireBrick;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
1;31m  </span><span style="color:FireBrick;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:FireBrick;background-color:Ivory"></span><span style="color:FireBrick;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:FireBrick;background-color:Ivory"></span><span style="color:FireBrick;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:FireBrick;background-color:Ivory"></span><span style="color:FireBrick;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:FireBrick;background-color:Ivory"></span><span style="color:FireBrick;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:FireBrick;background-color:Ivory"></span><span style="color:FireBrick;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:FireBrick;background-color:Ivory"></span><span style="color:FireBrick;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:FireBrick;background-color:Ivory"></span><span style="color:FireBrick;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:FireBrick;background-color:Ivory"></span><span style="color:FireBrick;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
  32m  </span><span style="color:SeaGreen;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SeaGreen;background-color:Ivory"></span><span style="color:SeaGreen;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SeaGreen;background-color:Ivory"></span><span style="color:SeaGreen;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SeaGreen;background-color:Ivory"></span><span style="color:SeaGreen;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SeaGreen;background-color:Ivory"></span><span style="color:SeaGreen;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SeaGreen;background-color:Ivory"></span><span style="color:SeaGreen;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SeaGreen;background-color:Ivory"></span><span style="color:SeaGreen;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SeaGreen;background-color:Ivory"></span><span style="color:SeaGreen;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SeaGreen;background-color:Ivory"></span><span style="color:SeaGreen;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
1;32m  </span><span style="color:SeaGreen;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SeaGreen;background-color:Ivory"></span><span style="color:SeaGreen;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SeaGreen;background-color:Ivory"></span><span style="color:SeaGreen;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SeaGreen;background-color:Ivory"></span><span style="color:SeaGreen;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SeaGreen;background-color:Ivory"></span><span style="color:SeaGreen;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SeaGreen;background-color:Ivory"></span><span style="color:SeaGreen;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SeaGreen;background-color:Ivory"></span><span style="color:SeaGreen;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SeaGreen;background-color:Ivory"></span><span style="color:SeaGreen;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SeaGreen;background-color:Ivory"></span><span style="color:SeaGreen;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
  33m  </span><span style="color:Gold;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Gold;background-color:Ivory"></span><span style="color:Gold;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Gold;background-color:Ivory"></span><span style="color:Gold;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Gold;background-color:Ivory"></span><span style="color:Gold;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Gold;background-color:Ivory"></span><span style="color:Gold;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Gold;background-color:Ivory"></span><span style="color:Gold;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Gold;background-color:Ivory"></span><span style="color:Gold;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Gold;background-color:Ivory"></span><span style="color:Gold;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Gold;background-color:Ivory"></span><span style="color:Gold;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
1;33m  </span><span style="color:Gold;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Gold;background-color:Ivory"></span><span style="color:Gold;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Gold;background-color:Ivory"></span><span style="color:Gold;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Gold;background-color:Ivory"></span><span style="color:Gold;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Gold;background-color:Ivory"></span><span style="color:Gold;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Gold;background-color:Ivory"></span><span style="color:Gold;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Gold;background-color:Ivory"></span><span style="color:Gold;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Gold;background-color:Ivory"></span><span style="color:Gold;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Gold;background-color:Ivory"></span><span style="color:Gold;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
  34m  </span><span style="color:SteelBlue;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SteelBlue;background-color:Ivory"></span><span style="color:SteelBlue;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SteelBlue;background-color:Ivory"></span><span style="color:SteelBlue;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SteelBlue;background-color:Ivory"></span><span style="color:SteelBlue;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SteelBlue;background-color:Ivory"></span><span style="color:SteelBlue;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SteelBlue;background-color:Ivory"></span><span style="color:SteelBlue;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SteelBlue;background-color:Ivory"></span><span style="color:SteelBlue;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SteelBlue;background-color:Ivory"></span><span style="color:SteelBlue;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SteelBlue;background-color:Ivory"></span><span style="color:SteelBlue;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
1;34m  </span><span style="color:SteelBlue;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SteelBlue;background-color:Ivory"></span><span style="color:SteelBlue;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SteelBlue;background-color:Ivory"></span><span style="color:SteelBlue;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SteelBlue;background-color:Ivory"></span><span style="color:SteelBlue;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SteelBlue;background-color:Ivory"></span><span style="color:SteelBlue;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SteelBlue;background-color:Ivory"></span><span style="color:SteelBlue;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SteelBlue;background-color:Ivory"></span><span style="color:SteelBlue;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SteelBlue;background-color:Ivory"></span><span style="color:SteelBlue;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:SteelBlue;background-color:Ivory"></span><span style="color:SteelBlue;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
  35m  </span><span style="color:Purple;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Purple;background-color:Ivory"></span><span style="color:Purple;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Purple;background-color:Ivory"></span><span style="color:Purple;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Purple;background-color:Ivory"></span><span style="color:Purple;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Purple;background-color:Ivory"></span><span style="color:Purple;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Purple;background-color:Ivory"></span><span style="color:Purple;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Purple;background-color:Ivory"></span><span style="color:Purple;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Purple;background-color:Ivory"></span><span style="color:Purple;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Purple;background-color:Ivory"></span><span style="color:Purple;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
1;35m  </span><span style="color:Purple;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Purple;background-color:Ivory"></span><span style="color:Purple;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Purple;background-color:Ivory"></span><span style="color:Purple;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Purple;background-color:Ivory"></span><span style="color:Purple;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Purple;background-color:Ivory"></span><span style="color:Purple;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Purple;background-color:Ivory"></span><span style="color:Purple;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Purple;background-color:Ivory"></span><span style="color:Purple;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Purple;background-color:Ivory"></span><span style="color:Purple;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:Purple;background-color:Ivory"></span><span style="color:Purple;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
  36m  </span><span style="color:LightSeaGreen;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:LightSeaGreen;background-color:Ivory"></span><span style="color:LightSeaGreen;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:LightSeaGreen;background-color:Ivory"></span><span style="color:LightSeaGreen;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:LightSeaGreen;background-color:Ivory"></span><span style="color:LightSeaGreen;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:LightSeaGreen;background-color:Ivory"></span><span style="color:LightSeaGreen;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:LightSeaGreen;background-color:Ivory"></span><span style="color:LightSeaGreen;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:LightSeaGreen;background-color:Ivory"></span><span style="color:LightSeaGreen;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:LightSeaGreen;background-color:Ivory"></span><span style="color:LightSeaGreen;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:LightSeaGreen;background-color:Ivory"></span><span style="color:LightSeaGreen;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
1;36m  </span><span style="color:LightSeaGreen;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:LightSeaGreen;background-color:Ivory"></span><span style="color:LightSeaGreen;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:LightSeaGreen;background-color:Ivory"></span><span style="color:LightSeaGreen;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:LightSeaGreen;background-color:Ivory"></span><span style="color:LightSeaGreen;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:LightSeaGreen;background-color:Ivory"></span><span style="color:LightSeaGreen;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:LightSeaGreen;background-color:Ivory"></span><span style="color:LightSeaGreen;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:LightSeaGreen;background-color:Ivory"></span><span style="color:LightSeaGreen;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:LightSeaGreen;background-color:Ivory"></span><span style="color:LightSeaGreen;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
  37m  </span><span style="color:DarkSlateGray;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
1;37m  </span><span style="color:DarkSlateGray;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:FireBrick">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:SeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:Gold">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:SteelBlue">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:Purple">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:LightSeaGreen">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory"> </span><span style="color:DarkSlateGray;background-color:Ivory"></span><span style="color:DarkSlateGray;background-color:Ivory">  Color  </span><span style="color:DarkSlateGray;background-color:Ivory">
</span><span style="color:DarkSlateGray;background-color:Ivory"></span></pre>
