# Agent Index Registry Service

A registration database for tracking agentic AI systems, inspired by (MIT’s Agent Index)[https://aiagentindex.mit.edu/index/].

## Overview

As autonomous and semi-autonomous AI systems proliferate, transparency about their design, intended uses, and safety practices becomes increasingly necessary. MIT’s Agent Index provides an important public resource for documenting deployed agentic AI systems. This project builds on the MIT Agent Index idea by providing:


1. Agent Index Server: 
- **REST API** via [FastAPI](https://fastapi.tiangolo.com/) for CRUD operations over HTTP. 
- **Agent Card Validation** using [Pandera](https://pandera.readthedocs.io/en/stable/), which enables schema validation for incoming requests. 
- **Analyzes** agent card entries using [Daft Dataframes](https://www.getdaft.io/)
- **Stores** validated records in [LanceDB](https://lancedb.com/).
- **Serves** a REST API via [FastAPI](https://fastapi.tiangolo.com/) that is deployed

2. Static Web Page for submitting 

The service is designed to facilitate a transparent portfolio of agentic AI systems and promote accountability in the field.

## Motivation

Transparency is essential when dealing with AI systems that have real-world impacts. In a world where autonomous and semi-autonomous systems are on the rise, knowing the technical components, safety practices, and deployment details is key. This service is intended not only to contribute to that transparency but also to allow others to host their own databases that can feed into broader efforts like MIT’s index.

## Setup

### Prerequisites

- Python 3.8+
- [Ray](https://docs.ray.io/en/latest/serve/index.html)
- [LanceDB](https://lancedb.com/) (this example uses a local directory for storage)

### Installation

1. **Clone the repository:**
```bash
git clone https://github.com/yourusername/agent-index-service.git
cd agent-index-service
```

2. **Create a Virtual Environment:**
```bash
python3.10 -m venv .venv
```

2.	Install dependencies:
```bash
pip install -r requirements.txt
```

3. Running the Application
Start the service with:
```bash
python main.py
```
This will initialize Ray, start Ray Serve, deploy the FastAPI app, and expose the following endpoints:
	•	POST /agent_cards: Submit a new agent card (validated with Pandera).
	•	GET /agent_cards: Retrieve all stored agent cards.

