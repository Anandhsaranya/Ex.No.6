# Ex.No.6 Development of Python Code Compatible with Multiple AI Tools
# Date: 03-11-2025
# Register no.: 212223060250
# Aim: 
Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights with Multiple AI Tools
# Experiment:
Development of Python Code Compatible with Multiple AI Tools – The Persona Pattern
# Aim
To develop a single Python function that can automatically read both .csv and .json files into a list of dictionaries, ensuring compatibility with multiple AI tools following the Persona Pattern approach.

# Apparatus Required
Python 3.x
Built-in libraries: csv, json, os
Sample dataset files:
data.csv
data.json
Text editor or IDE (VS Code / PyCharm / Jupyter Notebook)
Explanation
In AI and data-driven applications, different tools often require a uniform input format. The Persona Pattern emphasizes creating adaptable, reusable functions that act as a "persona" for different AI tools.

Here, we create a single function load_data() that:

Accepts a file path.
Automatically detects the file type (.csv or .json).
Converts the contents into a list of dictionaries format.
For .csv, each row becomes a dictionary using headers as keys.
For .json, the file is loaded directly into a list of dictionaries.
Returns the processed data for further use in AI models, pipelines, or analytics.
This ensures that AI tools get standardized input data, regardless of the original file format.

# Python Code
```
import csv
import json
import os

def load_data(file_path):
    """
    Loads data from either a CSV or JSON file into a list of dictionaries.
    
    Args:
        file_path (str): Path to the file (.csv or .json)
    
    Returns:
        list[dict]: Data as list of dictionaries
    """
    if not os.path.exists(file_path):
        raise FileNotFoundError(f"{file_path} does not exist")

    extension = os.path.splitext(file_path)[1].lower()  # get file extension

    data = []
    if extension == ".csv":
        with open(file_path, mode="r", encoding="utf-8") as f:
            reader = csv.DictReader(f)
            data = [row for row in reader]

    elif extension == ".json":
        with open(file_path, mode="r", encoding="utf-8") as f:
            data = json.load(f)
            # Ensure it's a list of dicts
            if isinstance(data, dict):
                data = [data]

    else:
        raise ValueError("Unsupported file format. Please use .csv or .json")

    return data
```

# Example Usage
if __name__ == "__main__":
    csv_data = load_data("data.csv")
    print("CSV Data:", csv_data)

    json_data = load_data("data.json")
    print("JSON Data:", json_data)
Result: The corresponding Prompt is executed successfully.
