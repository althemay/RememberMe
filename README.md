# RememberMe - Dementia Assistant

## Summary

**RememberMe** is an innovative solution designed to enhance the quality of life for individuals suffering from dementia. This digital assistant helps users maintain their independence by supporting memory recall, managing daily tasks, and connecting them with their loved ones and familiar environments.

## Description

The application integrates multimedia data, such as video, audio, and personal notes, and uses the Twelve Labs API to convert these into texts. These texts are then organized and stored in a database, which the application's chatbot uses to help users remember important personal information.

## Development Team

- Tatiane Wu Li
- Pedro Goncalves de Paiva
- Aleksei (Alex) Korablev
- Na Le

## Technical Details

The project is built with Python and uses the following technologies:

- **Twelve Labs API:** For processing multimedia content.
- **SQLite:** For database management.
- **Python Libraries:** `os`, `requests`, `time`, `sqlite3`, `pprint`, `glob`.

### Setup Instructions

1. **Environment Setup:**
   Set your Twelve Labs API key and API URL as environment variables.
   ```python
   import os
   os.environ['API_KEY'] = 'your_api_key'
   os.environ['API_URL'] = 'https://api.twelvelabs.io/v1.2'
   ```

2. **Database Initialization:**
   Run the following Python code to set up the SQLite database.
   ```python
   import sqlite3

   def get_db_connection():
       return sqlite3.connect('video_summaries.db')

   def create_summaries_table():
       with get_db_connection() as conn:
           cursor = conn.cursor()
           cursor.execute('''
           CREATE TABLE IF NOT EXISTS summaries (
               video_id TEXT PRIMARY KEY,
               summary TEXT,
               processing_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
           )
           ''')
           conn.commit()

   create_summaries_table()
   ```

3. **API Interaction:**
   Example code to interact with the Twelve Labs API.
   ```python
   import requests

   API_URL = os.getenv("API_URL")
   API_KEY = os.getenv("API_KEY")
   headers = {"x-api-key": API_KEY}
   response = requests.post(f"{API_URL}/indexes", headers=headers, json=data)
   print(response.json())
   ```

4. **Running the Application:**
   Execute the main script to start the application.
   ```python
   if __name__ == "__main__":
       main()
   ```

### How to Use

Once the setup is complete, run the script and follow the on-screen prompts to process videos. The application will provide text summaries stored in the SQLite database, which can be retrieved and displayed to the user.

## Contact

For any questions or concerns, please reach out to aleksei@uni.minerva.edu
