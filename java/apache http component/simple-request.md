<h1> How to do a simple request using HttpComponent </h1>

```java

public String request(String url){

    // Create the client
    CloseableHttpClient httpClient = HttpClients.createDefault();
    // Create a the request
    HttpGet request = new HttpGet(url);
    // Receive the response
    HttpReponse response = httpClient.execute(request);
    // Create a string that could be parsed into a Map.
    String responseBody = EntityUtiles.toString(response.getEntity(), StandardCharsets.UTF_8);

    return responseBody;
}

```