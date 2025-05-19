# spring-boot-ai-mcp-client
This is MCP Client using springboot 

Overview

The application facilitates communication with an MCP server, likely to leverage AI model capabilities. It uses Spring AI's ChatClient to send prompts and receive responses. The ChatController exposes an API endpoint to handle user input and interact with the ChatClient. 


Key Components

pom.xml: This file defines the project's dependencies and build configuration.
It uses the Spring Boot Starter Parent (spring-boot-starter-parent) to inherit common dependencies and configurations.
It includes dependencies for:
spring-boot-starter-web: For building web applications with Spring MVC.
spring-ai-openai-spring-boot-starter: To integrate with OpenAI.
spring-ai-mcp-client-spring-boot-starter: To use the Spring AI MCP client.
spring-ai-bom: Spring AI Bill of Materials to manage versions of Spring AI dependencies. 
src/main/java/com/siddhu/SpringBootAiMcpClientApplication.java: This is the main entry point of the Spring Boot application.
The @SpringBootApplication annotation enables Spring Boot's autoconfiguration and component scanning.
The SpringApplication.run() method starts the application. 
src/main/java/com/siddhu/config/MCPClientChatClientConfig.java: This configuration class sets up the ChatClient.
The @Configuration annotation indicates that this class provides Spring beans.
The @Bean annotation defines a ChatClient bean.
It uses a ChatClient.Builder and ToolCallbackProvider to configure the ChatClient, potentially integrating tools for more complex interactions. 
src/main/java/com/siddhu/controller/ChatController.java: This controller handles incoming chat requests.
The @RestController annotation indicates that this class is a controller and that its methods return data directly (rather than views).
The @RequestMapping("/chat") annotation maps requests to the /chat path to this controller.
It uses @Autowired to inject the ChatClient.
The @PostMapping("/ask") annotation maps HTTP POST requests to the /chat/ask endpoint.
The chat() method receives user input (userInput) as a request body, sends it to the ChatClient using chatClient.prompt(userInput), and returns the response content. 
src/main/resources/application.yml: This file contains the application's configuration.
It sets logging levels for MCP client communication.
It configures Spring AI to use OpenAI, including API key and base URL. Critically it also configures the specific model to use (google/gemini-2.0-flash-exp:free).
It provides configuration for the MCP client, specifying how to connect to the MCP server.
In this case, it's configured to start the MCP server using stdio (standard input/output).
It defines connection details for a server named "mongo-mcp-server," including the command to execute (java), arguments to pass to the command (to run the server's JAR file), and environment variables (MONGO_HOST, MONGO_PORT) to configure the server. 
In Summary

This Spring Boot application acts as a client that can send text prompts to an MCP server and receive responses. It's configured to use Spring AI for handling the communication and sets up an API endpoint (/chat/ask) for external interaction. The configuration in application.yml is crucial for specifying how to connect to and run the MCP server.
