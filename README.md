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
