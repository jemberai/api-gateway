# API Gateway
The API Gateway is a Spring Boot application that acts as a reverse proxy for the Data Intake and Chat services. 
It is responsible for routing requests to the appropriate service.

## Environment Variables
### Security Configuration
* SPRING_SECURITY_OAUTH2_RESOURCESERVER_JWT_ISSUER_URI - The URI of the authorization server that issued the JWT token.
* SPRING_SECURITY_OAUTH2_RESOURCESERVER_JWT_JWK_SET_URI - The URI of the authorization server's JWK set.

### Gateway Configuration
* AUTH_SERVER - The URI of the authorization server.
* AUTH_SERVER_PORT - The port of the authorization server.
* DATA_INTAKE_SERVER - The URI of the data intake server.
* DATA_INTAKE_SERVER_PORT - The port of the data intake server.
* DATA_INTAKE_OA3_SERVER - The URI of the data intake oa3 server.
* DATA_INTAKE_OA3_SERVER_PORT - The port of the data intake oa3 server.
* CHAT_SERVER - The URI of the chat server.
* CHAT_SERVER_PORT - The port of the chat server.

### OpenShift Configuration
This application has been configured with Spring Boot Actuator. This provides readiness and liveness probes for OpenShift.

This application will start on port 8080. To override the port, set the SERVER_PORT environment variable to desired port.

#### Example Configuration Snippet
```yaml
        readinessProbe:
          httpGet:
            port: 8080 # Set to server port
            path: /actuator/health/readiness
        livenessProbe:
          httpGet:
            port: 8080
            path: /actuator/health/liveness
```