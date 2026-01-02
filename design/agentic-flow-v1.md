# Agentic Flow v1

*High-level overview of the agent-assisted CS resolution system flow*

---

## System Flow Overview

This diagram shows the end-to-end flow of how cases are processed, from initial trigger through to customer resolution.

```mermaid
flowchart TD
    Start([Case Trigger]) --> Input{Input Source}
    Input -->|Customer| CustomerMsg[Customer Message<br/>Chat/Email]
    Input -->|System| FlightAPI[3rd Party API<br/>Flight Status]
    
    CustomerMsg --> Categorize
    FlightAPI --> Categorize
    
    Categorize[2. Categorize & Prioritize<br/>LLM Classifier<br/>GPT-4o mini<br/>Urgency + Type]
    
    Categorize --> Context[3. Context Assembly<br/>RAG Pipeline]
    
    Context --> VectorDB[(Vector Database<br/>KB + Laws + Rules<br/>Historical Cases)]
    VectorDB --> Context
    
    Context --> Reasoning[4. LLM Reasoning<br/>Claude Sonnet<br/>Synthesizes context<br/>Generates options<br/>Explains decisions]
    
    Reasoning --> Human[5. Human Decision<br/>Agent Dashboard<br/>Review options<br/>Approve/Modify/Reject]
    
    Human --> Execute[6. Execute Resolution<br/>Rebook/Refund/Compensate]
    Execute --> Customer([Customer<br/>Resolution Delivered])
    
    Human --> Learning[(Learning Loop<br/>Log decisions<br/>Improve model)]
    Learning -.feedback.-> Reasoning
    
    style Start fill:#e1f5ff
    style Categorize fill:#fff4e1
    style Context fill:#e8f5e9
    style VectorDB fill:#c8e6c9
    style Reasoning fill:#f3e5f5
    style Human fill:#fff9c4
    style Execute fill:#e8f5e9
    style Customer fill:#4caf50,color:#fff
```

---

## Flow Steps

1. **Case Trigger**: Event originates from either customer contact (chat/email) or proactive detection via 3rd party flight status APIs

2. **Categorize & Prioritize**: Fast LLM (GPT-4o mini) classifies the issue type and calculates urgency based on time-to-departure and customer location

3. **Context Assembly**: RAG pipeline retrieves relevant information:
   - Booking details
   - Flight status
   - Policies from knowledge base
   - Laws and regulations
   - Similar historical cases

4. **LLM Reasoning**: Claude Sonnet synthesizes all context to:
   - Understand the full situation
   - Generate 2-4 valid resolution options
   - Explain reasoning and policy justifications
   - Assign confidence scores

5. **Human Decision**: Agent reviews options in dashboard:
   - Sees all context and LLM reasoning
   - Can approve, modify, or reject options
   - Makes final decision (human-in-the-loop for MVP)

6. **Execute Resolution**: Approved option is executed:
   - Rebooking via airline APIs
   - Refund processing
   - Compensation/vouchers
   - Customer notification

**Learning Loop**: All decisions are logged and outcomes tracked to continuously improve the model.

---

*Version 1.0 - January 2026*

