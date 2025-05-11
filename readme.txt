The code here is in the folder project by the name of improvement.ipynb , these rest of the files are just me practicing from the documentation and also please use a api key here , i will remove it from here cause the repo is public.

Here in this part of the code at the end of the file improvement.ipynb is where we validate the codes
await call_agent_and_print(code_runner, code_agent, SESSION_ID_TOOL_AGENT, "{ \"code\": \"010188\" }")

010188 , inplace of this code you have to write any code to check
# HSN Code Validation Agent

This project implements an HSN (Harmonized System of Nomenclature) code validation agent using [Google's Agent Development Kit (ADK)](https://github.com/google-deepmind/adk). The agent can determine whether an input HSN code exists, and if not, it will recursively check for its valid parent codes.

## 📁 Project Structure

```
project/
├── improvement.ipynb       # Main implementation notebook
├── (other ADK practice notebooks)
```

> ⚠️ Note: Only `improvement.ipynb` contains the main agent logic. The rest are for practice.

## 🔍 What It Does

The notebook defines a multi-step agent toolchain for checking HSN code validity. When a code is provided, it will:

1. Check if the code exists in the dictionary.
2. If not found, check for parent codes (by reducing the length in steps).
3. Return appropriate messages accordingly.

## ✅ Requirements

Make sure to install the dependencies before running:

```bash
pip install google-generativeai
pip install google-adk  # If not already included with the above
pydantic>=2.0
```

You can also use a `requirements.txt`:

```txt
google-generativeai
pydantic>=2.0
```

## 🔐 API Key

To run this code, you **must provide your Google API key**:

```python
os.environ["GOOGLE_API_KEY"] = "<your-api-key-here>"
```

> **Important**: The API key in the source will be removed before making the repository public.

## 🚀 How to Use

In the last cell of `improvement.ipynb`, you’ll see:

```python
await call_agent_and_print(code_runner, code_agent, SESSION_ID_TOOL_AGENT, "{ \"code\": \"010188\" }")
```

To test with any code, just change `010188` to the desired input (as a string).

## 🔄 Workflow Summary

```
+---------------------+
| 1. User Input (JSON) |
|  e.g., {"code": "010188"} |
+---------------------+
          |
          v
+-------------------------------------+
| 2. call_agent_and_print Function   |
|  - Formats user query              |
+-------------------------------------+
          |
          v
+-------------------------------------+
| 3. code_runner.run_async()         |
|  - Sends query to code_agent       |
+-------------------------------------+
          |
          v
+-------------------------------------+
| 4. Agent 'code_agent' Execution    |
|  - Validates input schema          |
|  - Decides whether to call tool    |
+-------------------------------------+
          |
          v
+-------------------------------------+
| 5. validateCode Tool               |
|  - Checks code and parents         |
|  - Returns relevant result         |
+-------------------------------------+
          |
          v
+-------------------------------------+
| 6. Agent Formats Final Response    |
+-------------------------------------+
          |
          v
+-------------------------------------+
| 7. call_agent_and_print Displays   |
+-------------------------------------+
```

## 📌 Example Response

```text
The code '010188' was not found, but its parent codes exist: '01': 'LIVE ANIMALS', '101': 'LIVE HORSES, ASSES, MULES AND HINNIES'.
```

## 📬 License & Contribution

* This is a student/internship project.
* Contributions or suggestions are welcome via pull requests or issues!

---

Feel free to fork and adapt this for validating other code structures or classifications.

---
