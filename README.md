# 🍔 Burger App: Graph API & Recommendation Engine (Phase 4)

## 📌 Project Overview
This repository contains the final phase of the **Polyglot Data Ecosystem**. It implements a Full CRUD **GraphQL API** integrated with a **Neo4j Graph Database**. 

Instead of relying on paid Managed Cloud APIs, this project features a custom-built backend using **FastAPI** and **Strawberry GraphQL**. This architecture saves cloud infrastructure costs while delivering high-performance relationship traversal.

## 🎯 Key Features
*   **Recommendation Engine:** Leverages Cypher queries to traverse nodes and find complex purchasing patterns instantly (e.g., "Users who bought X also bought Y").
*   **Full CRUD API:** Comprehensive GraphQL queries and mutations to create user purchases, update product prices, and delete nodes along with their relationships safely.
*   **Cost Optimization:** Replaces the Neo4j Aura native GraphQL service ($16/month) with a fully custom, lightweight Python backend ready for free-tier deployment.

## 🏗️ Tech Stack
*   **Database:** Neo4j (Aura Cloud)
*   **Query Language:** Cypher
*   **Backend Framework:** FastAPI (Python)
*   **GraphQL Library:** Strawberry

## 📂 Project Structure
*   `database.py`: Manages the Neo4j Python driver connection and Cypher query execution.
*   `seed.py`: A one-time setup script containing Cypher queries to initialize the database with mock nodes (Users, Burgers, Sides) and relationships (`[:BOUGHT]`).
*   `main.py`: The FastAPI application exposing the GraphQL endpoint (`/graphql`) with full Query and Mutation capabilities.
*   `.env`: Environment variables configuration (ignored in version control).

## ⚙️ Setup & Installation

1. **Install Dependencies:**
   ```bash
   pip install neo4j python-dotenv fastapi uvicorn strawberry-graphql

NEO4J_URI=neo4j+s://<your-instance-id>.databases.neo4j.io
NEO4J_USERNAME=neo4j
NEO4J_PASSWORD=your_secure_password

python seed.py

python main.py

Example GraphQL Operations
Query: Get Recommendations

GraphQL
query {
  getRecommendations(burgerId: "b1") {
    itemName
  }
}
Mutation: Add a New Purchase

GraphQL
mutation {
  addPurchase(userName: "Hazem", burgerId: "b2")
}
Mutation: Update Item Price

GraphQL
mutation {
  updateBurgerPrice(burgerId: "b1", newPrice: 8.99)
}
   د
