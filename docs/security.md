# Security

### Configuration Options
1. server.xml
    * Information Leak
        * <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false />
    * Access Control
        * <Valve className="org.apache.catalina.valves.RemoteAddrValve" allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1"/>

2. web.xml
    * listings
        * false
    * debug
        * 0
	* Example
    ```
     <servlet>
       <servlet-name>default</servlet-name>
       <servlet-class>org.apache.catalina.servlets.DefaultServlet</servlet-class>
       <init-param>
       <!-- Disable debug -->
         <param-name>debug</param-name>
         <param-value>0</param-value>
       </init-param>
       <!-- Not listing file -->
       <init-param>
         <param-name>listings</param-name>
         <param-value>false</param-value>  <!-- make sure this is false -->
       </init-param>
       <load-on-startup>1</load-on-startup>
     </servlet>


     <!-- Show error.jso while RuntimeException -->
     <error-page>
       <exception-type>java.lang.Throwable</exception-type>
       <location>/error.jsp</location>
     </error-page>
    ```

3. CATALINA_BASE/lib/org/apache/catalina/util/ServerInfo.properties
    * server.info=Apache Tomcat/8.0.x

### Reference
1. https://www.owasp.org/index.php/Securing_tomcat
2. https://tomcat.apache.org/tomcat-8.0-doc/security-howto.html

