### Microservice Patterns:
1. Saga Pattern
   - Choreography (using EventSource like Apache Kafka)
   - Orchestration
2. CQRS Pattern ( Command And Query Responsibility Segregation )
   - Segregate Read and Write Operations into different services.
   - Handle High Load
   - Write Complex Queries
   - Add Additional Security
   - Query Micro service ( GET )
   - Command Micro service ( PUT, POST, DELETE )
3. Transactional Outbox Pattern
   - Dual Write Problem
   - Writing data into more than one services using the same transaction causing Data Inconsistency.
   - This pattern ensures reliable message delivery in distributed systems.
   - Create an outbox so that the message can be accessed from that.
   - Create a Local Transaction (write to a new table) rather than a distributed transaction.
   - Use Message Relay Service ( MRS ) as a Poller to relay ( publish ) this message to another micro service.
4. Microservice Sidecar Pattern
   - Separating the primary tasks from the secondary tasks.
   - Examples include Logging Service, Monitoring Service, Configuration Service and Authentication Service.
5. Microservice Event Sourcing Pattern
   - It is a pattern where state changes are logged or stored as a sequence of immutable events instead of being stored directly in the database.
6. Microservice Aggregator Pattern
   - Solves problems of
      - Network Load
      - High Latency
      - Data Enrichment Overload
      - Error Handling Complexity
      - Not Resilient systems
      - Security and Exposure Risk
   - Create an Aggregator service that handles all the above problems and perform the actions instead of calling all micro services from a single point.
7. Microservice Hexagonal Architecture
   - Also known as Ports and Adapter Design Pattern
   - It's all about structuring the application
   - Separate the core logic from the external sources and plugin the ports and adapters of different sources interacting with the system.
   - adapter IN -> Port In -> Core Logic -> Port OUT -> Adapter OUT
   - Rest or Kafka -> Place Order Use case -> order-service -> Repository Port -> Database, File System, Cloud