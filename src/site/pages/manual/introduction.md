* Logback vs other logging systems
  * faster
  * smaller footprint
  * check "../reasonsToSwitch.html"
* requirements
  * | classpath
    * slf4j-api.jar
      * -- required by -- logback-classic's
      * shipped by SLF4J
    * logback-core.jar
      * -- required by -- logback-classic's
    * logback-classic.jar
* allows
  * 👁️reporting information about its internal state 👁️
    * Check `StatusManager`
    * if there is an error -> internal state is printed automatically | console   
* steps to enable logging | application
  * configure logback environment
  * retrieve a `Logger` instance
    * `org.slf4j.LoggerFactory.getLogger("currentClassName")`
  * `loggerInstance.printingMethods()`
    * _Example:_ `logger.info("MesasgeToAddOnTheConfiguredAppender")`
* relied on Maven -- as -- build tool
  * `mvn install`
    * build logback project / ALL its modules
* _Examples:_
  * Check [logbackRepo](https://github.com/dancer1325/logback/tree/master/logback-examples)