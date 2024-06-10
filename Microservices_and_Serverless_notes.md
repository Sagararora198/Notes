
# Microservices and Serverless

## Cloud Computing Solutions

### Monolithic
- **Definition**: One big application with all functions.
- **Drawback**: Difficult to maintain.

### Microservices
- **Definition**: Small, independent applications that communicate through APIs.

### Serverless
- **Definition**: Ability to run applications without managing the underlying infrastructure.

## 12-Factor App Methodology
- **Purpose**: Suited for web apps, frequently used with microservices.
- **Phases**: Can be grouped according to phases of the software delivery lifecycle:
  1. **Code**: Codebase, build, release, run, dev/prod parity, dependencies.
  2. **Deploy**: Config, backend services, processes, port binding.
  3. **Operate**: Concurrency, disposability, logs, admin processes.

## Microservices
- **Definition**: Makes each application component its own service, and each service communicates through APIs.
- **Comparison**:
  - **Monolith**: Single, large application.
  - **SOA (Service-Oriented Architecture)**: Services communicate over a network.
  - **Microservices**: Smaller, more granular services compared to SOA.

## API Gateway
- **Definition**: An API management tool that sits between the client and a collection of backend services.
- **Uses**:
  - Protect API
  - Analyze API
  - Monetize API
  - Present a single point of contact to microservices
  - Add/remove APIs seamlessly
- **Drawbacks**:
  - Complexity
  - Single point of failure
  - Extra step in the process

## Swagger
- **Definition**: API documentation tool.

## GraphQL
- **Definition**: A query language for your API.
- **Advantages**:
  - Allows clients to fetch only what's needed.
  - Language agnostic (can be built in any language).
  - Does not require API versioning.
- **Terms**:
  - Query
  - Fields
  - Mutation (to modify the data)

## Serverless
- **Definition**: Concept of building and running applications that do not require server management.
- **Components**:
  - **FaaS (Function as a Service)**: Used to run functions.
  - **BaaS (Backend as a Service)**: Cloud services such as databases, object storage, and message queues.
- **Characteristics**:
  - Hostless
  - Elastic
  - Load balancer
  - Stateless
  - Event-driven
  - Highly available
  - Usage-based
- **Disadvantages**:
  - Vendor lock-in
  - Cold start
  - Latency (unsuitable for time-critical apps like banking)
  - Security
  - No state persistence (use external caches like Redis)

## FaaS (Function as a Service)
- **Definition**: Subset of serverless computing.
- **Characteristics**:
  - Divide server into functions.
  - Create applications as functions.
  - Deploy on hybrid and on-premise.
  - Stateless.
  - Functions execute in milliseconds.
- **Providers**:
  - **Managed FaaS**: AWS Lambda, Google Cloud Functions, etc.
  - **Self-Managed FaaS**: Fission, Fn Project, Knative, OpenFaaS.

## Serverless Stack
- **Components**:
  - **API Gateway**
  - **FaaS**
  - **BaaS**
- **Framework**: Written in Node.js.
- **Function Trigger**: By events.

## AWS Services

### AWS CodeCommit
- **Definition**: A secure, highly scalable, and fully managed service that hosts private Git repositories.

### AWS Amplify
- **Definition**: A complete solution that lets front-end web and mobile developers easily build, ship, and host full-stack applications in AWS.

### AWS Step Functions
- **Definition**: A visual workflow service that helps developers use AWS services to build distributed applications, automate processes, orchestrate microservices, and create data and machine learning pipelines.

## Example Workflow
1. **Frontend**: Code your frontend in CodeCommit.
2. **Hosting**: Use Amplify to host from CodeCommit.
3. **Backend**: Use Lambda to add functions.
4. **Data**: Store data in DynamoDB.

