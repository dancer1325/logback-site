* | classpath
  * required .jar -- Find them in maven repository --
    * if logback 1.5.x / target Jakarta EE
      * logback-core-1.5.6.jar
      * logback-classic-1.5.6.jar
      * logback-examples-1.5.6.jar
      * slf4j-api-2.0.13.jar
    * if logback 1.3 / target Java EE
      * logback-core-1.3.14.jar
      * logback-classic-1.3.14.jar
      * logback-examples-1.3.14.jar
      * slf4j-api-2.0.13.jar
  * `java -cp lib/slf4j-api-2.1.0.alpha1.jar;../logback-core-1.5.6.jar;\
      ../logback-classic-1.5.6.jar;target/logback-examples-1.5.6.jar\
      packageName.FileName`
    * _Example:_

        ```
        java -cp lib/slf4j-api-2.0.13.jar;../logback-core-1.5.6.jar;\
         ../logback-classic-1.5.6.jar;logback-examples-1.5.6.jar\       
         chapters.introduction.HelloWorld1
        ```

        * Problems:
          * Problem1: "zsh: no such file or directory: ../logback-core-1.5.6.jar" & "zsh: no such file or directory: ../logback-classic-1.5.6.jar" & "zsh: no such file or directory: ../logback-examples-1.5.6.jar"
            * Solution: Add copy resources for ALL to "/lib"
          * Problem2: "java.lang.ClassNotFoundException: chapters.introduction.HelloWorld1"
            * Attempt1: `....HelloWorld1.class`
            * Solution: `...:target/classes chapters.introduction.HelloWorld1`
          * Problem3: "NoClassDefFoundError: org/slf4j/LoggerFactory"
            * ⭐ Solution: GOOD one ⭐
            
                ```
              java -classpath lib/slf4j-api-2.1.0-alpha1.jar:lib/logback-core-1.5.6.jar:lib/logback-classic-1.5.6.jar:logback-examples-1.5.6.jar:target/classes chapters.introduction.HelloWorld1
                ```
* Maven dependency declaration
  * if you add "ch.qos.logback:logback-classic" -- by transitive rules -- will add
    * slf4j-api.jar
    * logback-core.jar
  * optional dependencies
    * ch.qos.logback:logback-access
    * javax.mail:mail
      * uses
        * `SMTPAppender`
    * org.codehaus.janino:janino
      * uses
        * conditional processing | configuration files
* Building Logback
  * "JRE"
    * ONLY required dependency | runtime
  * logback v1.5.X
    * Java v21 to build
    * Java v11 | JRE