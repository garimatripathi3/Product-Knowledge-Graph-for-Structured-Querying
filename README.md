# Knowledge Graph from Unstructured Product Catalogue

A system that converts unstructured product descriptions into a queryable knowledge graph, enabling structured information extraction and semantic querying of product data.

![Knowledge Graph Visualization](https://github.com/user-attachments/assets/19d32793-fce6-41c9-a57a-84fd1dac9f90)

## Project Overview

This project converts unstructured product text into a structured knowledge graph that:
- Transforms free-text product descriptions into schema-compliant JSON objects
- Builds queryable knowledge representations of product characteristics
- Enables semantic search and inference across the product catalogue
- Prevents hallucination through schema-based constraints

## Implementation Pipeline

1. **Data Preparation**: Generate synthetic training data from the provided JSON dataset
2. **Schema Definition**: Utilize TTL schema to define product attribute relationships
3. **Format Conversion**: Transform structured data to JSONL format for fine-tuning
4. **Model Fine-tuning**: Train the model with schema awareness
5. **Inference**: Query the model for product information and process new product descriptions

## Quick Start Guide

```bash
# Step 0: Generate synthetic training data
python generate_synthetic_data.py --input becn_data.json --output synthetic_data.json

# Step 1: Convert to JSONL format (already completed)
# The formatted data is available at: training_data_jsonl_format.jsonl

# Step 2: Fine-tune the model with schema constraints
python fine_tune.py --schema product_schema.ttl --data training_data_jsonl_format.jsonl

# Step 3: Query the model and process new product descriptions
python query_after_training.py
```

## Hyperparameter Configuration

| Parameter | Description | Default | Range |
|-----------|-------------|---------|-------|
| `learning_rate` | Learning rate for fine-tuning | 5e-5 | 1e-6 - 1e-4 |
| `batch_size` | Batch size for training | 4 | 1 - 16 |
| `epochs` | Number of training epochs | 3 | 1 - 10 |
| `max_length` | Maximum sequence length | 512 | 128 - 1024 |
| `schema_integration` | Schema integration level | "full" | ["none", "partial", "full"] |

