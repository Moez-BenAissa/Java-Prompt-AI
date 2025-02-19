# 📝 Exercise3 - Chain of Thought ~ 10 minutes

The "chain of thought" technique involves guiding the model through a reasoning process to explain each step of the thought process. Here, we use this method to generate TypeScript documentation.

## 1️⃣ Use Case 1: Create a Prompt for the Model to Write Documentation for Java Code

Possible example:

```java
Here is my code:
import javax.ws.rs.GET;
import javax.ws.rs.POST;
import javax.ws.rs.Path;
import javax.ws.rs.PathParam;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.Application;
import java.util.HashSet;
import java.util.Set;

@ApplicationPath("/api")
public class ClientApplication extends Application {
    @Override
    public Set<Class<?>> getClasses() {
        Set<Class<?>> resources = new HashSet<>();
        resources.add(ClientResource.class);
        return resources;
    }
}

@Path("/clients")
class ClientResource {

    @GET
    @Path("/{clientId}")
    public Response getClient(@PathParam("clientId") String clientId) {
        return Response.ok("John Doe").build();
    }

    @POST
    public Response updateClient() {
        return Response.ok("Client updated!").build();
    }
}

Write documentation for this API service.
```

Now it's your turn to integrate your prompt below: 👀
```java
Create a prompt for the model to write documentation for Java code.
[cpied code here]
```

What was the response?
```java
swagger format : 
openapi: 3.0.1
info:
  title: Client API
  description: API for managing client information.
  version: 1.0.0
servers:
  - url: http://localhost:8080/api
    description: Local development server

paths:
  /clients/{clientId}:
    get:
      summary: Get client information
      description: Retrieves client details based on the provided client ID.
      parameters:
        - name: clientId
          in: path
          required: true
          description: Unique identifier of the client
          schema:
            type: string
      responses:
        "200":
          description: Successfully retrieved client information
          content:
            text/plain:
              schema:
                type: string
                example: "


And for makwon format : 

---

## 📌 Endpoints  

### 1️⃣ **Get Client Information**  
- **Endpoint:** `GET /clients/{clientId}`  
- **Description:** Retrieves client details based on the provided client ID.  
- **Request Parameters:**
  - `clientId` (**path parameter**) – Unique identifier of the client *(required)*  
- **Responses:**
  - ✅ `200 OK` – Successfully retrieved client  
    ```json
    "John Doe"
    ```
  - ❌ `400 Bad Request` – Invalid client ID format  
  - ❌ `404 Not Found` – Client not found  

#### 📌 **Example Request (cURL)**  
```sh
curl -X GET "http://localhost:8080/api/clients/123" -H "Accept: text/plain"

```

## 2️⃣ Use Case 2: Create a Prompt for the Model to Document the Same API Using a Specific Methodology

Possible example:

```java
Write documentation for this API service using the OpenAPI methodology.
```

Now it's your turn to integrate your prompt below: 👀
```java
Write documentation for this API service using the OpenAPI methodology.
```

What was the response?
```java
openapi: 3.0.1
info:
  title: Client API
  description: RESTful API for retrieving and updating client information.
  version: 1.0.0
  contact:
    name: API Support
    email: support@example.com

servers:
  - url: http://localhost:8080/api
    description: Local development server

paths:
  /clients/{clientId}:
    get:
      summary: Retrieve client information
      description: Fetches client details based on the provided client ID.
      operationId: getClientById
      parameters:
        - name: clientId
          in: path
          required: true
          description: Unique identifier of the client
          schema:
            type: string
      responses:
        "200":
          description: Successfully retrieved client information
          content:
            text/plain:
              schema:
                type: string
                example: "John Doe"
        "400":
          description: Invalid client ID format
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
        "404":
          description: Client not found
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'

  /clients:
    post:
      summary: Update client information
      description: Updates client details in the system.
      operationId: updateClient
      responses:
        "200":
          description: Client updated successfully
          content:
            text/plain:
              schema:
                type: string
                example: "Client updated!"
        "400":
          description: Invalid request data
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'

components:
  schemas:
    ErrorResponse:
      type: object
      properties:
        error:
          type: string
          example: "Invalid client ID format"

```

## 3️⃣ Use Case 3: Compare Your Two Responses and Test Other Methodologies or Custom Plans

Feel free to explore other documentation methodologies or customize plans to test how the model adapts to different structures and requirements.
