* log requests coded | application -- needs -- planning and effort
* configure logback
  * ways
    * programmatically OR
    * script
      * in
        * xml
        * groovy or
        * serialized model format -- the fastest one --
    * [PropertiesTranslator web application](http://logback.qos.ch/translator/)
      * log4j.properties -- can be converted to -- logback.xml
  * steps / followed by logback -- to -- configure itself
    * search custom `Configurator` providers / use `java.util.ServiceLoader` | "META-INF/services/ch.qos.logback.classic.spi.Configurator"
    * if a custom one is found -> precedence over logback's own (Check the implementations of `Configurator`)
    * if NO custom one is found -> logback instantiate `SerializedModelConfigurator`
      * if `logback.scmoFile` is set -> `SerializedModelConfigurator` tries to locate the serialized configuration model file | `logback.scmoFile`  
      * if `logback.scmoFile` is NOT set -> `SerializedModelConfigurator` tries to locate the serialized configuration model file "logback-test.scmo" | classpath
      * if previous serialized configuration model file is NOT found -> tries to locate `logback.scmo` | classpath
    * if NO serialized configuration model found for `SerializedModelConfigurator` -> logback instantiate `DefaultJoranConfigurator`
      * if `logback.configurationFile` is set -> `DefaultJoranConfigurator` tries to locate the serialized configuration model file | `logback.configurationFile`
      * if previous step fails -> `DefaultJoranConfigurator` tries to locate `logback-test.xml` | classpath
    * if NO serialized configuration model found for `DefaultJoranConfigurator` -> logback instantiate `BasicConfigurator`
      * -> logging output -- are directed to the -- console
    * TODO:
  * Joran
    * == configuration framework
    * check 'Joran/'
* configuration file location -- is set via -- system property
  * TODO:
* stop logback-classic
  * TODO:
* configure file syntax
  * TODO:
* add a context listener
  * TODO: