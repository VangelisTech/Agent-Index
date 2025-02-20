## Agent Index 

The point of this project is to show people how to set this kind of index up on their own, and to extend its purpose to act as a registration service for Agent Service providers (ASP). 


## Pre-filtering entries according to MITs criteria
```mermaid
flowchart LR
    A([Named "agentic" AI system]) --> B{Can the system accomplish a diverse range<br/> of tasks or have a meaningfully higher<br/> degree of agency than ChatGPT-4.0?}
    B -- No --> X[Exclude]
    B -- Yes --> C{Is the system a product deployed<br/> for commercial or other<br/> consequential applications?}
    C -- Yes --> Y[Include]
    C -- No --> D{Is the system open source?}
    D -- Yes --> Y2[Include]
    D -- No --> E{Could the system be used off the shelf<br/> or with very minor modifications<br/> to accomplish economically valuable tasks<br/> competitively with other solutions?}
    E -- Yes --> Y3[Include]
    E -- No --> F{Is there another compelling reason<br/> to track this system?<br/> E.g., a particularly informative case study<br/> or exceptionally relevant in shaping the state of the art?}
    F -- Yes --> Y4[Include]
    F -- No --> X2[Exclude]
```

### In code: 

Given an agent card model of: 
```python
from pydantic import BaseModel

class AgentCard(BaseModel):
    website: str
    short_description: str
    intended_uses: str
    dates_deployed: str = None
    developer_website: str
    developer_legal_name: str
    developer_entity_type: str
    developer_country: str
    safety_policies: str = None
    backend_model: str
    public_model_specification: bool
    reasoning_planning_memory: str = None
    observation_space: str = None
    action_space_tools: str = None
    user_interface: str
    development_cost_compute: str = None
    access_weights: bool = None
    access_data: bool = None
    access_code: bool = None
    access_scaffolding: bool = None
    access_documentation: bool = None
    controls_guardrails: str = None
    customer_usage_restrictions: str = None
    monitoring_shutdown: str = None
    benchmark_evaluations: str = None
    bespoke_testing: str = None
    safety_evaluations: str = None
    red_team_personnel: str = None
    red_team_scope: str = None
    red_team_findings: str = None
    interoperability: str = None
    usage_statistics: str = None
```

We can store multiple card entries as rown in an equivalent Agent Card DataFrame Model using Pandera:

```python
