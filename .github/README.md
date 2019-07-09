# plaform-spring-boot
The parent POM for all HighWire Platform Spring Boot project POMs.

Add user credentials for our Nexus-based repo by adding these servers to your personal settings.xml file (usually located on your development machine at ~/.m2/settings.xml):

```        
<servers>
  ...
  <server>
    <id>platform-snapshots</id>
    <username>${nexus-user}</username>
    <password>${nexus-password}</password>
  </server>
  <server>
    <id>platform-releases</id>
    <username>${nexus-user}</username>
    <password>${nexus-password}</password>
  </server>
</servers>
```
And get the cedential values from your team leader or SysOps.

You may want to add the cert for the Nexus server to your JDK's truststore, you can do that like this:

```
$ keytool -J-Djava.net.useSystemProxies=true -printcert -rfc -sslserver bk-nexus-dev-01.highwire.org:443 > ~/.m2/nexus-cert.pem
$ sudo keytool -importcert -file ~/.m2/nexus-cert.pem -alias nexus -storepass changeit -keystore $(/usr/libexec/java_home)/lib/security/cacerts
```

If that is problematic, then you can tell Maven to just shutup-already and trust the server like so:

```
$ ./mvnw -Dmaven.wagon.http.ssl.insecure=true -Pjar deploy -DskipTests
```
