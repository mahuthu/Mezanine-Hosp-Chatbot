

"# Mezanine-Hosp-Chatbot" 
# Build an LLM RAG Chatbot With LangChain

Our stakeholders would like more visibility into the ever-changing data they collect. They want answers to ad-hoc questions about patients, visits, physicians, hospitals, and insurance payers without having to understand a query language like SQL, request a report from an analyst, or wait for someone to build a dashboard.

To accomplish this, our stakeholders want an internal chatbot tool, similar to ChatGPT, that can answer questions about your company’s data. After meeting to gather requirements, you’re provided with a list of the kinds of questions your chatbot should answer:

- What is the current wait time at XYZ hospital?
- Which hospital currently has the shortest wait time?
- At which hospitals are patients complaining about billing and insurance issues?
- Have any patients complained about the hospital being unclean?
- What have patients said about how doctors and nurses communicate with them?
- What are patients saying about the nursing staff at XYZ hospital?
- What was the total billing amount charged to Cigna payers in 2023?
- How many patients has Dr. John Doe treated?
- How many visits are open and what is their average duration in days?
- Which physician has the lowest average visit duration in days?
- How much was billed for patient 789’s stay?
- Which hospital worked with the most Cigna patients in 2023?
- What’s the average billing amount for emergency visits by hospital?
- Which state had the largest percent increase in Medicaid visits from 2022 to 2023?



## Setup

Create a `.env` file in the root directory and add the following environment variables:

```.env
OPENAI_API_KEY=<YOUR_OPENAI_API_KEY>

NEO4J_URI=<YOUR_NEO4J_URI>
NEO4J_USERNAME=<YOUR_NEO4J_USERNAME>
NEO4J_PASSWORD=<YOUR_NEO4J_PASSWORD>

HOSPITALS_CSV_PATH=https://raw.githubusercontent.com/hfhoffman1144/langchain_neo4j_rag_app/main/data/hospitals.csv
PAYERS_CSV_PATH=https://raw.githubusercontent.com/hfhoffman1144/langchain_neo4j_rag_app/main/data/payers.csv
PHYSICIANS_CSV_PATH=https://raw.githubusercontent.com/hfhoffman1144/langchain_neo4j_rag_app/main/data/physicians.csv
PATIENTS_CSV_PATH=https://raw.githubusercontent.com/hfhoffman1144/langchain_neo4j_rag_app/main/data/patients.csv
VISITS_CSV_PATH=https://raw.githubusercontent.com/hfhoffman1144/langchain_neo4j_rag_app/main/data/visits.csv
REVIEWS_CSV_PATH=https://raw.githubusercontent.com/hfhoffman1144/langchain_neo4j_rag_app/main/data/reviews.csv

HOSPITAL_AGENT_MODEL=gpt-3.5-turbo-1106
HOSPITAL_CYPHER_MODEL=gpt-3.5-turbo-1106
HOSPITAL_QA_MODEL=gpt-3.5-turbo-0125


```

The chatbot uses OpenAI LLMs, so you'll need to create an [OpenAI API key]
The three `NEO4J_` graph database variables are used to connect to your Neo4j AuraDB instance. Follow the directions [here](https://neo4j.com/cloud/platform/aura-graph-database/?ref=docs-nav-get-started) to create a free instance.

Once you have a running Neo4j instance, and have filled out all the environment variables in `.env`, you can run the entire project with [Docker Compose](https://docs.docker.com/compose/). You can install Docker Compose by following [these directions](https://docs.docker.com/compose/install/).

Once you've filled in all of the environment variables, set up a Neo4j AuraDB instance, and installed Docker Compose, open a terminal and run:

```console
$ docker-compose up --build
```

After each container finishes building, you'll be able to access the chatbot API at `http://localhost:8000/docs` and the Streamlit app at `http://localhost:8501/`.


This repo contains the source code for [Build an LLM RAG Chatbot With LangChain]

