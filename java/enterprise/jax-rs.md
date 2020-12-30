
# jax-rs




# timeouts

http://www.adam-bien.com/roller/abien/entry/setting_timeout_for_the_jax


# REST security

[Securing RESTful Web Services](https://docs.oracle.com/cd/E24329_01/web.1211/e24983/secure.htm#RESTF115)

Securing RESTful Web Services Using web.xml

Securing RESTful Web Services Using SecurityContext

Securing RESTful Web Services Using Annotations

OAuth / OAuth2  
* Using Jersey OAuth libraries to sign and verify requests.
* maven: com.auth0 / java-jwt / 3.3.0
* maven: org.bitbucket.b_c / jose4j / 0.6.3
* maven: com.nimbusds / nimbus-jose-jwt / 5.7
* maven: io.jsonwebtoken / jjwt-root / 0.11.1
* maven: io.fusionauth / fusionauth-jwt / 4.0.0
* maven: io.vertx / vertx-auth-jwt / 3.5.1

microprofile jwt  
https://www.eclipse.org/community/eclipse_newsletter/2017/september/article2.php  
https://github.com/eclipse/microprofile-jwt-auth

[Advanced JAX-RS 24 - Implementing REST API Authorization](https://www.youtube.com/watch?v=W5jm4E0TTlA)

[Deconstructing REST Security by David Blevins, April 2017](https://www.youtube.com/watch?v=9CJ_BAeOmW0)

[Deconstructing and Evolving REST Security 1/2 by David Blevins, Jan 2018](https://www.youtube.com/watch?v=_wWxfZxCQfQ)

[Deconstructing and Evolving REST Security 2/2 by David Blevins, Jan 2018](https://www.youtube.com/watch?v=osQmFNm0YDU)

[Deconstructing and Evolving REST Security by David Blevins, Feb 2018](https://www.recallact.com/presentation/deconstructing-and-evolving-rest-security)  
https://vimeo.com/260488042

# CORS


```
package com.airhacks.cors;

/*
 * #%L
 * jaxrs-cors
 * %%
 * Copyright (C) 2014 Adam Bien
 * %%
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 * 
 *      http://www.apache.org/licenses/LICENSE-2.0
 * 
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 * #L%
 */
import java.io.IOException;
import java.util.List;
import javax.ws.rs.container.ContainerRequestContext;
import javax.ws.rs.container.ContainerResponseContext;
import javax.ws.rs.container.ContainerResponseFilter;
import javax.ws.rs.core.MultivaluedMap;
import javax.ws.rs.ext.Provider;

/**
 * See http://www.w3.org/TR/cors/
 *
 * @author airhacks.com
 */
@Provider
public class CorsResponseFilter implements ContainerResponseFilter {

    public static final String ALLOWED_METHODS = "GET, POST, PUT, DELETE, OPTIONS, HEAD";
    public final static int MAX_AGE = 42 * 60 * 60;
    public final static String DEFAULT_ALLOWED_HEADERS = "origin,accept,content-type";
    public final static String DEFAULT_EXPOSED_HEADERS = "location,info";

    @Override
    public void filter(ContainerRequestContext requestContext, ContainerResponseContext responseContext) throws IOException {
        final MultivaluedMap<String, Object> headers = responseContext.getHeaders();
        headers.add("Access-Control-Allow-Origin", "*");
        headers.add("Access-Control-Allow-Headers", getRequestedAllowedHeaders(requestContext));
        headers.add("Access-Control-Expose-Headers", getRequestedExposedHeaders(requestContext));
        headers.add("Access-Control-Allow-Credentials", "true");
        headers.add("Access-Control-Allow-Methods", ALLOWED_METHODS);
        headers.add("Access-Control-Max-Age", MAX_AGE);
        headers.add("x-responded-by", "cors-response-filter");
    }

    String getRequestedAllowedHeaders(ContainerRequestContext responseContext) {
        List<String> headers = responseContext.getHeaders().get("Access-Control-Allow-Headers");
        return createHeaderList(headers, DEFAULT_ALLOWED_HEADERS);
    }

    String getRequestedExposedHeaders(ContainerRequestContext responseContext) {
        List<String> headers = responseContext.getHeaders().get("Access-Control-Expose-Headers");
        return createHeaderList(headers, DEFAULT_EXPOSED_HEADERS);
    }

    String createHeaderList(List<String> headers, String defaultHeaders) {
        if (headers == null || headers.isEmpty()) {
            return defaultHeaders;
        }
        StringBuilder retVal = new StringBuilder();
        for (int i = 0; i < headers.size(); i++) {
            String header = (String) headers.get(i);
            retVal.append(header);
            retVal.append(',');
        }
        retVal.append(defaultHeaders);
        return retVal.toString();
    }

}
```


# links

https://www.gitbook.com/book/dennis-xlc/restful-java-with-jax-rs-2-0-2rd-edition/details

https://github.com/AdamBien/cors/blob/master/src/main/java/com/airhacks/cors/CorsResponseFilter.java​

https://www.javaworld.com/article/2824163/application-performance/stability-patterns-applied-in-a-restful-architecture.html
