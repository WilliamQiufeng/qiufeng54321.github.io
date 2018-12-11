# JarLoader  
  *JarLoader* is a repository that builds a jar file and loads it to the VM.It supports all the platforms.Even on android it works properly,
but needs a special support which is included in this project.
### How it works
#### Compile
1. compile java files to .class files
#### Build
1. encrypt .class files with custom key
2. push encrypted .class files into a jar file.
#### Load
##### Win/Linux
1. pull out .class files
2. decrypt .class files
3. load the .class files into VM
##### Android
1. pull out .class files
2. decrypt .class files
3. push .class files into .dex file
4. load .dex file

### Feature
1. use en/decryption for .class files to increase security.
2. compatible with all platforms.
3. easy to use.

## How to use
### Compile
<code class="java">
  JavaCompiler.compile([input file],[lib file],[output dir]);
<code>
