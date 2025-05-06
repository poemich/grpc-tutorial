# an Advanced Programming Class Repository

by Muhammad Fadhlan Karimuddin (2306245011)

## Reflection

1. What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable?
   
   - **Unary RPC:** 
     The client sends one request and gets one response. Ideal for simple operations like those in our Payment Service (e.g., fetching user details or saving data).
   - **Server Streaming RPC:** 
     The client sends one request and then receives a series of responses. Best used for scenarios like live updates or sending large lists.
   - **Bi-Directional Streaming RPC:** 
     Both client and server send multiple messages independently and at the same time. Perfect for real-time features like chat, system monitoring, or collaboration.

2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?
   
   Validate each data fragment for authentication and authorization. Encrypt every piece of data exchanged between the client and server to ensure privacy. Unlike REST, where validation is per request, gRPC may need repeated checks for a single call.

3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications?
   
   Managing bidirectional streaming in Rust involves:
   - Coordinating the read/write cycle between client and server to avoid blocking or race conditions.
   - Efficiently handling asynchronous tasks for many connections.
   - Robust error handling on both sides without disrupting the entire stream.

4. What are the advantages and disadvantages of using the tokio_stream::wrappers::ReceiverStream for streaming responses in Rust gRPC services?
   
   **Advantages:**
   - Easy integration with gRPC using tonic.
   - Asynchronous synchronization.
   - Flexible and modular.
   - Concurrency-friendly.
   
   **Disadvantages:**
   - Risk of data loss if the channel is full and sending fails.
   - Additional overhead.
   - Authentication and authorization required for each data fragment.
   - More complex error handling.

5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time?
   
   To promote maintainability and extensibility:
   - Separate business logic for easier development and maintenance.
   - Create shared modules or libraries for common code.
   - Use generics for flexible handling of various data types.
   - Apply design patterns like the Builder pattern for constructing complex objects.

6. In the MyPaymentService implementation, what additional steps might be necessary to handle more complex payment processing logic?
   
   Steps to handle more complex payment logic:
   - Add input validation before processing payments.
   - Simulate or connect to external payment services.
   - Implement authentication and authorization.
   - Use a database to store payment history.

7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms?
   
   gRPC improves efficiency and structure in inter-service communication. Using Protocol Buffers (protobuf) makes it faster and lighter than JSON. However, interoperability can be challenging in ecosystems that don't natively support gRPC, requiring proxies or REST conversion.

8. What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs?
   
   **Advantages of HTTP/2:**
   - Multiplexing (multiple requests over one connection).
   - Header compression.
   - Efficient bandwidth usage.
   
   **Disadvantages:**
   - Less widespread support compared to HTTP/1.1.
   - More complex initial setup.
   
   HTTP/2 is faster and safer for structured services, while WebSocket is better for unstructured real-time communication.

9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness?
   
   REST uses a one-way request-response model, suitable for standard operations but less ideal for real-time needs. gRPC supports two-way streaming, enabling continuous data exchange for applications like chat, live notifications, or sensor data.

10. What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads?
    
    gRPC uses a fixed schema with Protocol Buffers, ensuring faster communication and easier validation. However, changes require regenerating code. REST with JSON is more flexible but can lead to errors if the format is inconsistent or poorly documented.