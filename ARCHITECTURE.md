# RAG-based HR Assistant Architecture

## System Overview

This document describes the architecture of the RAG-based AI Powered HR Assistant system.

## Components

### 1. Document Ingestion Layer
- HR policy documents are uploaded and processed
- Documents are chunked into meaningful paragraphs
- Chunks are converted into vector embeddings using Google AI Studio embeddings API

### 2. Vector Database (Supabase + pgvector)
- Stores all policy document chunks and their embeddings
- Enables semantic search capabilities
- Provides fast retrieval of relevant policy sections

### 3. Retrieval Engine
- Accepts user queries
- Converts queries to embeddings
- Performs semantic search to find top-k relevant policy chunks
- Returns context for the generation layer

### 4. Generation Layer
- Receives user query and retrieved context
- Uses Groq LLM (llama-3.3-70b-versatile) to generate responses
- Ensures answers are grounded in actual policy documents
- Provides confidence scores and source citations

### 5. API Layer
- Supabase Edge Functions for serverless execution
- REST endpoints for query submission
- Response formatting and delivery

## Data Flow

```
User Query
    ↓
Query Embedding (Google AI Studio)
    ↓
Semantic Search (Supabase pgvector)
    ↓
Retrieve Top-K Policy Chunks
    ↓
Groq LLM Generation (with context)
    ↓
Formatted Response with Citations
    ↓
User Response
```

## Database Schema

### policies table
```sql
CREATE TABLE policies (
  id BIGSERIAL PRIMARY KEY,
  title TEXT NOT NULL,
  content TEXT NOT NULL,
  embedding vector(384),
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX ON policies USING ivfflat (embedding vector_cosine_ops);
```

## Deployment

The system is deployed on:
- **Frontend**: Vercel/Netlify for React UI
- **Backend**: Supabase Edge Functions
- **Database**: Supabase PostgreSQL with pgvector
- **LLM**: Groq Cloud API

## Security Considerations

- API keys stored in environment variables
- Supabase Row Level Security (RLS) for access control
- Rate limiting on API endpoints
- Audit logging for all queries
- Data encryption in transit and at rest

## Scalability

- Serverless architecture auto-scales with demand
- Vector database optimized for semantic search
- Caching layer for frequently asked questions
- Load balancing for multiple concurrent users
