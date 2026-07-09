# DataQuery

DataQuery is a Natural Language to SQL application that allows users to query CSV datasets using plain English. The application converts natural language questions into SQL queries, executes them on uploaded datasets, and displays the results through an interactive Streamlit interface.

---

## Features

* Natural Language → SQL conversion
* Upload and query multiple CSV files
* Automatic CSV parsing
* Table and column descriptions for improved query generation
* Preview generated SQL before execution
* Execute custom SQL queries manually
* Interactive Streamlit interface
* Download query results as CSV

---

## Tech Stack

* Python
* Streamlit
* DuckDB
* Pandas
* Python Dotenv
* Chardet

---

## Architecture

```text
                  User
                    │
                    ▼
            Streamlit Interface
                    │
                    ▼
              Upload CSV Files
                    │
                    ▼
          Load into Pandas DataFrames
                    │
                    ▼
          Metadata Construction
                    │
                    ▼
            Prompt Generation
                    │
                    ▼
       Natural Language → SQL
                    │
                    ▼
          Register Tables in DuckDB
                    │
                    ▼
           Execute Generated SQL
                    │
                    ▼
            Display Query Results
```

---

## How It Works

### 1. Upload CSV Files

Upload one or more CSV files through the application. Each file is loaded into a Pandas DataFrame for processing.

### 2. Add Dataset Metadata (Optional)

Optionally provide descriptions for tables and columns. This additional context helps improve SQL generation.

### 3. Generate the Prompt

The application constructs a prompt using:

* Table names
* Column names
* Sample records
* User-provided metadata
* Natural language query

### 4. Generate SQL

The prompt is sent to a language model, which converts the user's question into a SQL query. The generated SQL is displayed before execution.

### 5. Execute the Query

Uploaded DataFrames are registered as tables in DuckDB. The generated SQL is executed, and the results are displayed within the application. Users can also write and execute custom SQL queries directly.

---

## Project Structure

```text
.
├── app.py                 # Main Streamlit application
├── csv_utils.py           # CSV parsing utilities
├── prompt_builder.py      # Prompt construction
├── llm_to_sql.py          # Natural language to SQL conversion
├── requirements.txt
└── README.md
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/your-username/dataquery.git
cd dataquery
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate the environment:

**Windows**

```bash
venv\Scripts\activate
```

**Linux / macOS**

```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Run the Application

```bash
streamlit run app.py
```

Open the local Streamlit URL in your browser and upload one or more CSV files to begin querying your data.

---

## Future Improvements

* SQL validation before execution
* Automatic SQL error correction
* Query history
* Query caching
* Data visualization
* Support for Excel and Parquet files

---

## License

This project is licensed under the MIT License.
