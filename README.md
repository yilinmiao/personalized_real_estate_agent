This project implements a personalized real estate agent application called "HomeMatch". It uses a LLM to generate synthetic real estate listings, stores them in a vector database, and then finds and personalizes listings based on buyer preferences.

## Project Structure
- `personalized_real_estate_agent.ipynb`: The app.
- `listings.json`: Stores the synthetically generated real estate listings (created on the first run).
- `chroma_db/`: Directory where the Chroma vector database is persisted (created on the first run).
- `README.md`: This file.

## Features

1.  **Synthetic Listing Generation**: Uses an LLM (OpenAI's GPT-3.5-turbo-instruct) to generate diverse real estate listings.
2.  **Vector Database Storage**: Embeds the generated listings using OpenAI embeddings and stores them in a persistent ChromaDB database.
3.  **Semantic Search**: Performs similarity search on the listings based on a natural language summary of buyer preferences.
4.  **Personalized Descriptions**: Leverages the LLM to rewrite the descriptions of matched listings, tailoring them to the buyer's preferences while maintaining factual accuracy.

**Execution Steps:**

-   The script will first check for your OpenAI API key.
-   It will then attempt to load listings from `listings.json`. If the file doesn't exist or is invalid, it will generate 10 new listings using the LLM and save them.
-   Next, it initializes the Chroma vector database in the `chroma_db/` directory. It loads the listings, creates embeddings, and adds any new listings to the database.
-   Hardcoded buyer preferences are defined and summarized.
-   A semantic search is performed using the buyer preference summary against the vector database, retrieving the top 3 most similar listings.
-   Finally, the descriptions of these top listings are personalized using the LLM, highlighting aspects relevant to the buyer's preferences. Original and personalized descriptions are printed for comparison.

## Example Output

The script prints output for each step, including:
-   Status messages for setup, listing generation, DB population.
-   The defined buyer preferences.
-   The results of the semantic search (top matching listings and scores).
-   The original and personalized descriptions for the matched listings. 
