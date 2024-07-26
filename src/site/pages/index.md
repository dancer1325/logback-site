* == successor to log4j
  * as soon as "log4j 1.x" is deprecated
* architecture
  * == logback-core + logback-classic + logback-access
    * logback-core
      * basis -- for -- other 2 modules
      * == general-purpose module
        * 👁️ -> NO notion of loggers 👁️
    * logback-classic
      * == improved version of log4j 1.x
      * extends logback-core
      * 👁️ implements natively [SLF4J API](http://www.slf4j.org) 👁️
        * -> you can switch back and forth between logging frameworks (logback, log4j 1.x, java.util.logging)
    * logback-access
      * -- integrates with -- Servlet containers (_Example:_ Tomcat and Jetty)
      * provide
        * HTTP-access log functionality
      * check '../access.html'
  * you can create your own module | logback-core