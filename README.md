Java-Runtime-Compiler
=====================

This takes a String, compiles it and loads it returning you a class from what you built.  
By default it uses the current ClassLoader.  It supports nested classes, but otherwise builds one class at a time.

## On maven central

You can include in your project with

    <dependency>
        <groupId>net.openhft</groupId>
        <artifactId>compiler</artifactId>
        <version>2.1</version>
    </dependency>
    
## Simple example

You needa CachedCompiler and access to you JDK's tools.jar.

     private final CachedCompiler cc = new CachedCompiler(null, null);
     
     // dynamically you can call
     Class aClass = cc.loadFromJava(className, javaCode);
     KnownInterface o = (KnownInterface) aClass.nextInstance();
     
I suggest making you class implement a "KnownInterface" as this will allow you to call/manipuate instances of you generated class.

Another more hacky way is to use this to override a class, provided it hasn't been loaded already.  
This means you can redefine an existing class and provided the methods and fields used match,
you have compiler redefine a class and code alreeady compiled to use the class will still work.

       
