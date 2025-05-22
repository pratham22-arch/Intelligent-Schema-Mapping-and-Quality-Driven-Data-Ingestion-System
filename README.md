
# Intelligent Schema Mapping and Quality-Driven Data Ingestion System

This project implements a modular data ingestion pipeline capable of:

- Ingesting structured data from CSV, SQL, and API sources.
- Automatically mapping heterogeneous schemas using sentence-transformers and Groq LLM fallback.
- Validating, imputing, and detecting anomalies in the data.
- Classifying records into Gold, Silver, and Manual Review layers based on quality.


```

## Output

- `validated_data.csv`: Full cleaned dataset with quality tags
- `gold_layer.csv`, `silver_layer.csv`, `manual_review.csv`: Stratified output layers

## Technologies Used

- Python, Pandas, Scikit-learn
- Sentence-Transformers (MiniLM)
- Groq LLM for fallback schema mapping
- KNN Imputer, Isolation Forest
