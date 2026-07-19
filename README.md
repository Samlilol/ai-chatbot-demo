# ai-chatbot-demo
Building a simple ai chatbot from scratch using steamlit and langchain stack

## Demo-video
Google Drive Preview: <link>https://drive.google.com/file/d/1TkXa_gCnoWwTW-VPamjwsYO1sTxOzxae/view?usp=share_link</link>


Download: <link>https://github.com/Samlilol/ai-chatbot-demo/blob/main/Analytic-Chatbot-Demo.mp4</link>

## Architecture
```mermaid
flowchart TD
    UI[UI Layer]
    ORCH[Orchestration Layer]
    AGENT[Specialist Agent]
    TOOLS[Tools<br/>Memory · Database · Chart Gen · RAG Search]
    GUARD{Guardrail}
    CLARIFY[Ask Clarification]
    REJECT[Rejection]
    COMPOSER[Composer Agent]
    EVAL{Eval}
    RESPONSE[Response]
    OBS[(Observability Layer<br/>structured logs from all nodes)]

    UI --> ORCH
    ORCH --> AGENT
    AGENT <--> TOOLS
    AGENT --> GUARD
    GUARD -- pass --> COMPOSER
    COMPOSER --> EVAL
    EVAL -- pass --> RESPONSE
    EVAL -- fail --> COMPOSER
    GUARD -- risk / low confidence --> CLARIFY
    GUARD -- risk / low confidence --> REJECT
    CLARIFY --> ORCH

    RESPONSE ~~~ OBS

    classDef main fill:#eef2f7,stroke:#334155,stroke-width:1.5px,color:#0f172a
    classDef warn fill:#fef9ec,stroke:#b45309,stroke-width:1.5px,color:#78350f
    classDef stop fill:#fdf2f2,stroke:#b91c1c,stroke-width:1.5px,color:#7f1d1d
    classDef ok fill:#f0fdf4,stroke:#15803d,stroke-width:1.5px,color:#14532d
    classDef obs fill:#f5f5f5,stroke:#616161,stroke-width:1px,color:#212121,stroke-dasharray: 5 5

    class UI,ORCH,AGENT,TOOLS,GUARD,COMPOSER,EVAL main
    class CLARIFY warn
    class REJECT stop
    class RESPONSE ok
    class OBS obs
```
