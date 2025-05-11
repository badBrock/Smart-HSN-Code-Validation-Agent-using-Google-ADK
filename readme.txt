+---------------------+
| 1. User Input (JSON) |
|    e.g., {"code": "010188"} |
+---------------------+
          |
          v
+-------------------------------------+
| 2. call_agent_and_print Function   |
|    - Receives user query (query_json) |
|    - Creates user content for agent  |
+-------------------------------------+
          |
          v
+-------------------------------------+
| 3. code_runner.run_async()         |
|    - Sends user content to code_agent |
+-------------------------------------+
          |
          v
+-------------------------------------+
| 4. Agent 'code_agent' Execution    |
|    - Receives user input ("010188")  |
|    - Checks input against input_schema |
|    - Validation (must_be_numeric) passes |
|    - Agent decides to use 'validateCode' tool based on instructions |
+-------------------------------------+
          |
          v
+-------------------------------------+
| 5. validateCode Tool Function       |
|    - Receives code: "010188"         |
|    - Prints "Tool Call" message      |
|    - Tries to convert "010188" to int (int_code = 10188) |
|    - Checks if int_code (10188) is in my_dict |
|    - 10188 is NOT in my_dict        |
|    - Checks for parent codes (prefixes): |
|      - "01" (exists in my_dict)     |
|      - "0101" (exists in my_dict)   |
|    - Creates message about parent codes found |
|    - Prints "Tool Result" message     |
|    - Returns the parent codes message |
+-------------------------------------+
          |
          v
+-------------------------------------+
| 6. Agent 'code_agent' Response    |
|    - Receives the tool's output     |
|    - Formulates final response based on instructions and tool output |
|    - Final Response: "The code '010188' was not found, but its parent codes exist: '01': 'LIVE ANIMALS', '101': 'LIVE HORSES, ASSES, MULES AND HINNIES'." |
+-------------------------------------+
          |
          v
+-------------------------------------+
| 7. call_agent_and_print Function   |
|    - Receives final response from agent |
|    - Prints "<<< Agent 'code_agent' Response: ..." |
|    - Retrieves and prints session state ('code_result') |
+-------------------------------------+

