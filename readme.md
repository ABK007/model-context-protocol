# Model Context Protocol (MCP) Documentation

## Overview

**Model Context Protocol (MCP)** is an open protocol designed to standardize and simplify how AI applications interact with external systems, data sources, and tools. The primary goal of MCP is to enhance the performance and personalization of AI models by providing them with richer and more dynamic context. In traditional setups, context was often added manually—via copy-pasting or custom integration logic—which led to a fragmented ecosystem. MCP solves this by introducing standardized interfaces that allow both AI apps (clients) and external systems (servers) to communicate seamlessly.

---

## Motivation Behind MCP

The core idea driving MCP is that **"models are only as good as the context we provide to them."** Historically, context was added through ad hoc methods that varied significantly across applications. Recognizing the need for consistency, MCP was developed with inspiration from two main precedents:

- **APIs (Application Programming Interfaces):**  
  APIs revolutionized how web applications interact by standardizing communication between the front end and the back end. They created a uniform way to translate and handle requests, thereby reducing complexity.

- **Language Server Protocol (LSP):**  
  LSP provided a standard way for Integrated Development Environments (IDEs) to interact with language-specific tools. It enabled any LSP-compatible IDE to leverage a single language server for coding assistance, debugging, and more.

MCP builds on these principles to create a uniform layer between AI applications and external systems—ensuring that once an AI client is MCP-compatible, it can interface with any MCP server with minimal additional work.

---

## Architecture and Key Components

MCP standardizes the interaction between AI applications and external systems through three primary interfaces:

1. **Prompts:**  
   These are the instructions or queries sent to the AI models. In the context of MCP, prompts act as the initial layer of communication that sets the context for the AI to process tasks or requests.

2. **Tools:**  
   Tools refer to the external systems or APIs that provide functionalities. These might include services such as version control systems (e.g., Git), CRMs (e.g., Salesforce), or any application that exposes an API for data access and operations.

3. **Resources:**  
   Resources are data sources that provide the contextual information needed by AI models. This can include databases, documentation repositories, or any system that houses records and other valuable data.

### Client-Server Paradigm

- **MCP Client:**  
  These are the AI applications or agents (such as first-party apps like Perser or Windsurf, or agent systems like Goose) that implement the MCP interface. Once MCP-compatible, these clients can connect to any MCP server seamlessly.

- **MCP Server:**  
  The server acts as a wrapper or mediator that federates access to various external systems (tools and data sources). It aggregates functionalities—be it querying a database, interfacing with a CRM, or connecting to local systems—into a standardized API that AI applications can utilize.

By decoupling the client (AI app) from the specifics of the external systems, MCP enables faster and more centralized development, reducing the overhead for teams that would otherwise have to develop custom integrations for every new data source or tool.

---

## Key Terminologies

- **Model Context Protocol (MCP):**  
  An open protocol aimed at standardizing how AI applications receive context from various external data sources and tools. Its primary role is to ensure that AI models have access to rich, up-to-date context, which in turn improves their performance and personalization.

- **AI Applications/Agents:**  
  These are software systems powered by artificial intelligence that utilize large language models (LMs) to perform tasks. In an MCP ecosystem, these applications can dynamically integrate with external systems to access necessary data and functionalities.

- **API (Application Programming Interface):**  
  A set of rules and protocols for building and interacting with software applications. APIs allow different software systems to communicate with each other in a standardized way.

- **LSP (Language Server Protocol):**  
  A protocol that standardizes communication between IDEs and language-specific servers. It inspired MCP in its approach to reducing fragmentation and creating a uniform integration standard.

- **Prompts:**  
  The text or commands provided to an AI model to guide its behavior. In MCP, prompts are one of the core interfaces, helping the model understand the context and the specific actions to be taken.

- **Tools:**  
  External systems or services that provide functionalities such as version control, CRM access, or data processing. MCP standardizes how these tools are integrated so that AI applications can interact with them without custom coding for each service.

- **Resources:**  
  Data sources that contain the context needed by AI models. These may include databases, documentation sites, or even locally stored files, which are federated through MCP to be accessible in a uniform manner.

- **Federation:**  
  The process of integrating various tools, data sources, and systems into one standardized protocol. Through federation, MCP allows multiple teams or external providers to offer their services via a common interface, thus reducing redundancy and promoting interoperability.

---

## Adoption and Benefits

- **Standardization:**  
  With MCP, developers can build AI applications that interface with any external system using a unified approach. This reduces the need for multiple, custom integrations and accelerates the development cycle.

- **Seamless Integration:**  
  Once an application is MCP-compatible, it can connect to any MCP server with zero additional integration work, making it easier for both internal teams and external partners to adopt and deploy advanced AI features.

- **Enhanced Personalization and Context-Rich Interactions:**  
  By enabling AI models to have direct access to real-time data sources and tools, MCP allows for more personalized and context-aware applications. This leads to improved accuracy and relevance in AI-driven tasks.

- **Enterprise Scalability:**  
  MCP provides a clear separation of concerns, allowing enterprises to centralize critical services (like vector databases or CRM systems) while enabling different teams to build on top of them in a modular fashion. This leads to a faster and more efficient development roadmap.

---

## Future Directions

As the ecosystem around AI applications continues to grow, MCP is expected to evolve further. Key areas for future development include:

- **Broader Adoption:**  
  More AI applications and tools will become MCP-compatible, further unifying the industry.
- **Enhanced Protocol Features:**  
  Continued refinement of the core interfaces (prompts, tools, resources) to support even richer interactions and data exchanges.
- **Community and Enterprise Contributions:**  
  An increasing number of community-built MCP servers and enterprise integrations will enrich the ecosystem, driving innovation and further standardization.

---

# Building with the Model Context Protocol (MCP)

## MCP Architecture

MCP is designed around a client–server model with a clear separation between what is controlled by the model and what is controlled by the application. This separation enables developers to build richer and more responsive AI-powered experiences without reinventing integration logic for every data source or tool.

### Key Components

1. **MCP Client**  
   The client is the front-end AI application (for example, “Cloud for Desktop”) that invokes various MCP components. It is responsible for:
   - **Invoking Tools:** Sending requests to external systems.
   - **Querying for Resources:** Fetching data that provides additional context.
   - **Interpolating Prompts:** Inserting dynamic context into pre-defined prompt templates before passing them to the language model.  
   *(citeturn1file0)*

2. **MCP Server**  
   The server side (or “server builder”) exposes the standardized interfaces that MCP clients consume. It aggregates and makes available:
   - **Tools:** Actions that the model can trigger (e.g., reading data, writing data, updating files).
   - **Resources:** Data outputs that provide contextual or state information, which can be static or dynamically interpolated.
   - **Prompts:** Predefined templates that guide common interactions. These are user-controlled and can be adapted based on the application’s needs.  
   *(citeturn1file0)*

---

## Core Components in Detail

### Tools

- **Definition:**  
  Tools are model-controlled actions that the MCP server makes available to the client application. They serve as the primary means through which the AI model can interact with external systems.
  
- **Usage:**  
  Tools can be designed to retrieve (read) or send (write) data. They may include functionalities such as accessing a vector database, updating files, or interacting with third-party APIs.
  
- **Key Aspect:**  
  The model within the client chooses the best time to invoke a tool based on context. This design makes the integration dynamic and responsive to the task at hand.  
  *(citeturn1file0)*

### Resources

- **Definition:**  
  Resources are pieces of data or external artifacts that are exposed to the application. They provide additional context that goes beyond simple text responses.
  
- **Usage:**  
  A resource might be a static file (such as JSON data or an image) or a dynamic dataset that gets interpolated with user information. They can also include resource notifications where the client subscribes to updates.
  
- **Key Aspect:**  
  Resources enable a richer interface for the application by allowing the server to deliver customized data structures in response to changes in context.  
  *(citeturn1file0)*

### Prompts

- **Definition:**  
  Prompts are user-controlled templates that standardize common interactions. They act as predefined instructions that guide the language model on how to use the context provided.
  
- **Usage:**  
  Unlike tools (which are model-controlled), prompts are initiated by the user. For example, in an Integrated Development Environment (IDE) like Zed, slash commands (e.g., typing “/GPR” to summarize pull requests) are implemented as prompt templates.
  
- **Key Aspect:**  
  Prompts help bridge the gap between static instruction and dynamic interaction, ensuring that the language model receives context in a form it can process efficiently.  
  *(citeturn1file0)*

---

## Building an MCP-Enabled Application

### Step 1: Designing the MCP Client

- **User Interface:**  
  Develop a client interface (for instance, a desktop or web application) that can:
  - Accept user input (commands, URLs, queries).
  - Display contextual outputs (such as summaries or triaged issues).
  
- **Tool Invocation:**  
  Integrate a mechanism where the client can insert and invoke tools. For example, when a user inputs a GitHub repository URL, the client should:
  - Trigger a tool that lists repository issues.
  - Automatically interpolate this data into the prompt for the language model.
  
- **Dynamic Prompts and Resources:**  
  Allow users to trigger pre-defined prompts that can be enriched dynamically with data from the server. The client should also subscribe to resource notifications to update its UI when the server sends new context.

### Step 2: Building the MCP Server

- **Expose Tools:**  
  Develop lightweight, modular endpoints that:
  - Serve as the tools for actions such as “list issues” or “triage tasks.”
  - Are simple enough to be built quickly (often in a matter of hours) yet powerful enough to integrate with various external systems.
  
- **Manage Resources:**  
  Set up endpoints that:
  - Provide resources (static or dynamic) based on the current context or user input.
  - Support resource notifications so that clients can remain synchronized with changes.
  
- **Define Prompts:**  
  Create a library of prompt templates that guide common tasks. Ensure that these templates can be dynamically filled with data from tools and resources to provide the necessary context before being sent to the language model.

### Step 3: Integrating Client and Server

- **Standardized Communication:**  
  Use MCP’s standard interfaces to allow any MCP-compatible client to connect to any MCP server. This means that once the server’s endpoints for tools, resources, and prompts are defined, the client can consume them without extra integration logic.
  
- **Interplay Between Model and Application:**  
  Design your system such that the model decides when to invoke tools (model-controlled) while the application retains control over when resources and prompts are brought into context (application controlled). This separation allows for greater flexibility and richer interactions.

### Example Use Case

Imagine you’re building an application for managing GitHub repositories:

1. **Repository Management:**  
   - **Input:** The user provides a repository URL in the client application.
   - **Tool Invocation:** The model (using an MCP tool) automatically fetches issues from the repository.
   - **Dynamic Prompting:** A predefined prompt template (such as “triage issues”) is interpolated with the list of issues.
   - **Resource Updates:** If new issues appear, the server sends a resource notification to update the client’s view.
   - **Outcome:** The user sees a prioritized list of issues and can act upon them directly from the central dashboard.
  
   *(citeturn1file0)*

---

## Integration with Existing Agent Frameworks

MCP is designed to complement (rather than replace) existing agent frameworks. While agent frameworks focus on the overall loop—such as how a language model processes data and iterates through interactions—MCP provides a standardized layer that simplifies how context is brought in. For example:

- **Agent Framework Integration:**  
  Tools built using MCP can be exposed to agents like those in LangGraph through connectors or adapters. This means that if your system is already built on an agent framework, you can still use MCP to standardize how external context (like GitHub data or file system changes) is integrated without changing your core architecture.
  
- **Complementary Roles:**  
  MCP focuses on how context, tools, and prompts interact with the language model, whereas the agent framework manages the control loop and knowledge management. Both work together to offer a robust, context-rich application experience.

---

## Key Terminologies – A Brief Glossary

- **MCP Client:**  
  The front-end application that consumes MCP services by invoking tools, fetching resources, and interpolating prompts.

- **MCP Server:**  
  The back-end component that exposes standardized endpoints for tools, resources, and prompts, enabling seamless integration with any MCP-compatible client.

- **Tools:**  
  Model-controlled endpoints that perform actions (e.g., reading from or writing to external systems) based on model decisions.

- **Resources:**  
  Data artifacts or dynamic content provided by the server that enrich the application's context, supporting static files, dynamic data, or notifications.

- **Prompts:**  
  Predefined, user-controlled templates for interacting with the server. They guide the language model by embedding contextual information into standard commands.

- **Model-Controlled vs. Application-Controlled:**  
  A design principle where tools are typically invoked by the model (model-controlled), while resources and prompts are often determined or triggered by the application (application-controlled). This separation ensures clarity in how context is managed and utilized.

- **Resource Notifications:**  
  Mechanisms by which the server can inform the client of changes or updates in resources, prompting the client to refresh or update its state accordingly.

---

