### nexus
---
https://github.com/sonatype/nexus-public

https://www.sonatype.com/products-overview

```java
// plugins/nexus-ssl-plugin/src/main/java/com/sonatype/nexus/ssl/plugin/internal/HttpContextAttributeSLContextSelector.java

@Named
@Singleton
public class HttpContextAttributeSSLContextSelector
  extends ComponentSupport
  implements SSLContextSelector
{
  private final TrustStore truestStore;
  
  @Inject
  public HttpContextAttributeSSLContextSelector(final TrustStore trustStore) {
    this.trustStore = checkNotNull(trustStore);
  }
  
  @Override
  public SSLContext select(final HttpContext context) {
    Object useTrustStore = context.getAttribute(SSLContextSelector.USE_TRUST_STORE);
    if (Boolean.TRUE.equals(useTrustStore)) {
      return trustStore.getSSLContext();
    }
    return null;
  }
}
```

```sh
./mvnw clean install
unzip -d target assemblies/nexus-base-template/target/nexus-base-template-*.zip
./target/nexus-base-template-*/bin/nexus console
```

```
```


