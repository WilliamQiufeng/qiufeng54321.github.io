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
```java
JavaCompiler.compile([input file],[lib file],[output dir]);
```
### Load
If you are on Win/Linux:
```java
JarLoader jl=new JarLoader([jar InputStream]);
jl.load("class name");
jl.loadAll();
```
If you are on Android,use _AndroidJarLoader_ insdead.
### Build
`AndroidJarBuilder` actually does not behave differently as `JarBuilder` except it adds a MANIFEST\.MF.I will remove this soon.
```java
JarBuilder jb=new JarBuilder([output]);
jb.write("path","data here".getBytes());
jb.close();
```
or `JarFileBuilder`
```java
JarFileBuilder jfb=new JarFileBuilder(new File("file name here"),/*OutputStream*/);
jfb.build();
jfb.close();
```
