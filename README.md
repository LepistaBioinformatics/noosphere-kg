# Stellar Knowledge Graph

A powerful tool for building knowledge graphs from unstructured text using Large
Language Models (LLMs) and the LangChain LLM Graph Transformer.

## What is a Knowledge Graph?

A knowledge graph is a structured representation of information that connects
entities (nodes) through relationships (edges). Unlike traditional databases
that store data in tables, knowledge graphs represent information as a network
of interconnected concepts, making it easier to understand complex relationships
and answer multi-hop questions.

### Why Knowledge Graphs Matter

Knowledge graphs are particularly valuable for:

- **Retrieval-Augmented Generation (RAG)**: While text embeddings work well for
  simple queries, knowledge graphs excel at answering complex, multi-hop
  questions that require understanding connections across multiple entities
- **Structured Operations**: Enable filtering, sorting, and aggregation
  operations that are challenging with unstructured text
- **Relationship Discovery**: Reveal hidden connections and patterns in data
  that might not be apparent from raw text
- **Semantic Search**: Provide more accurate and contextually relevant search
  results

## How It Works

The Stellar Knowledge Graph project leverages LangChain's LLM Graph Transformer
to automatically extract structured information from unstructured text
documents. Here's how the process works:

### 1. Document Processing

The system can process various document formats:

- PDF manuscripts (using docling for conversion)
- Plain text documents
- Any document that can be converted to text format

### 2. LLM-Powered Extraction

The LLM Graph Transformer operates in two modes:

#### Tool-Based Mode (Default)

- Uses LLMs with structured output capabilities (like GPT-4)
- Leverages function calling to extract entities and relationships
- Provides more accurate and consistent results
- Supports property extraction for both nodes and relationships

#### Prompt-Based Mode (Fallback)

- Uses few-shot prompting for LLMs without tool support
- Parses LLM output through custom functions
- Converts results to structured format

### 3. Graph Construction

The extracted information is structured into:

- **Nodes**: Entities like people, organizations, locations, compounds,
  microorganisms
- **Relationships**: Connections between entities (e.g., "WORKS_AT", "PRODUCES",
  "CONTAINED_IN")
- **Properties**: Additional attributes for nodes and relationships (e.g.,
  dates, names, descriptions)

### 4. Database Storage

The constructed knowledge graph is stored in Neo4j, a powerful graph database
that provides:

- Native graph operations
- Built-in visualization capabilities
- Efficient querying and traversal
- Scalability for large knowledge graphs

## Getting Started

### Prerequisites

- Python 3.12+
- Neo4j database (local or cloud instance)
- OpenAI API key (or other compatible LLM provider)

### Installation

1. Clone the repository:

    ```bash
    git clone <repository-url>
    cd stellar-kg
    ```

2. Create a virtual environment:

    ```bash
    python3 -m venv .venv
    source .venv/bin/activate  # On Windows: .venv\Scripts\activate
    ```

3. Install project using poetry:

    ```bash
    poetry install
    ```

### Configuration

1. Set up your Neo4j database connection in the `docker-compose.dev.yml` file
2. Configure your OpenAI API key (or other LLM provider) in the `.env` file

### Basic Usage

TODO: Add usage instructions

### Import Options

TODO: Add import options

## Use Cases

- **Scientific Literature**: Extract research findings, chemical compounds, and
  biological relationships
- **Business Intelligence**: Map organizational structures and business
  relationships
- **Legal Documents**: Identify entities, relationships, and key information
- **Medical Research**: Connect symptoms, treatments, and patient outcomes
- **Academic Research**: Build comprehensive knowledge bases from research
  papers

## Architecture

```mermaid
Documents → LLM Graph Transformer → Structured Graph → Neo4j Database
    ↓              ↓                    ↓              ↓
PDF/Text    Entity Extraction    Nodes & Edges    Graph Storage
```

## Contributing

We welcome contributions! Please feel free to submit issues, feature requests,
or pull requests.

## License

[Apache-2.0](LICENSE)

## Acknowledgments

This project builds upon the excellent work of the LangChain community and the
LLM Graph Transformer implementation. Special thanks to Tomaz Bratanic and the
contributors who made this technology accessible to the broader community.

## Resources

- [LangChain Documentation](https://python.langchain.com/)
- [Neo4j Documentation](https://neo4j.com/docs/)
- [LLM Graph Transformer
  Guide](https://medium.com/data-science/building-knowledge-graphs-with-llm-graph-transformer-a91045c49b59)
- [Neo4j LLM Graph Builder](https://llm-graph-builder.neo4jlabs.com/) (No-code
  alternative)
