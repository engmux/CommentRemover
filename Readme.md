# CommentRemover

CommentRemover is a source code comment removing library for Java&trade; 7 and above.<br><br>
It also supports JavaScript , HTML , CSS , Properties , JSP and XML Comments.

# Requirements

Projects that include CommentRemover need to target Java 1.7 at minimum.<br>
Please increase your stack size to 40m.<br>
VM option command is: -Xss40m if you need to increase more -Xss{size}m<br><br>

CommentRemover does _not_  depend on any libraries, you can easily add it as standalone .jar to your classpath.


# Installation - Maven
In your `pom.xml`, you must add **Repository** and **Dependency** for **CommentRemover**.<br><br>
After adding dependency run `mvn clean install` command and make sure that maven clean and install processes are completed. 

```xml
	<repository>
	    <id>jitpack.io</id>
	    <url>https:// jitpack.io</url>
	</repository>
	
	<dependency>
    	    <groupId>com.github.ertugrulcetin</groupId>
    	    <artifactId>CommentRemover</artifactId>
    	    <version>1.0</version>
    </dependency>
    	
```

# Usage

~~~~~ java

public class InternalPathExample {
    
 public static void main(String[] args) throws CommentRemoverException {
        
 // root dir is: /Users/user/Projects/MyProject
 // example for startInternalPath
    
 CommentRemover commentRemover = new CommentRemover.CommentRemoverBuilder()
        .removeJava(true) // Remove Java file Comments....
        .removeJavaScript(true) // Remove JavaScript file Comments....
        .removeJSP(true) // etc.. goes like that
        .removeTodos(false) //  Do Not Touch Todos (leave them alone)
        .removeSingleLines(true) // Remove single line type comments
        .removeMultiLines(true) // Remove multiple type comments
        .startInternalPath("src.main.app") // Starts from rootDir/src/main/app , leave it empty string when you want to start from root dir
        .setExcludePackages(new String[]{"src.main.java.app.pattern"}) // Refers to rootDir/src/main/java/app/pattern and skips this directory
        .build();
        
 CommentProcessor commentProcessor = new CommentProcessor(commentRemover);
                  commentProcessor.start();        
  }
}

~~~~~

~~~~~ java

public class ExternalPathExample {
    
 public static void main(String[] args) throws CommentRemoverException {

 // example for externalInternalPath
    
 CommentRemover commentRemover = new CommentRemover.CommentRemoverBuilder()
        .removeJava(true) // Remove Java file Comments....
        .removeJavaScript(true) // Remove JavaScript file Comments....
        .removeJSP(true) // etc..
        .removeTodos(true) // Remove todos
        .removeSingleLines(false) // Do not remove single line type comments
        .removeMultiLines(true) // Remove multiple type comments
        .startExternalPath("/Users/user/Projects/MyOtherProject")// Give it full path for external directories
        .setExcludePackages(new String[]{"src.main.java.model"}) // Refers to /Users/user/Projects/MyOtherProject/src/main/java/model and skips this directory.
        .build();
        
 CommentProcessor commentProcessor = new CommentProcessor(commentRemover);
                  commentProcessor.start();        
  }
}

~~~~~



