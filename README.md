# Assignment: Understanding and using OPENAI Chat-Completion-API-Parameters

Large language models (LLMs) like OPENAI's GPT use configurable **parameters** to control their behavior and customize responses. 
**#How many OPENAI parameters are there?**
The OPENAI CHAT COMPLETION API includes 8 parameters
**#OPENAI Parameter**:
1. `model`
   * **Requirement: Required**
   * **Purpose:** Specifies the LLm to be used (```e.g., gpt-4, gpt-3.5turbo).
   * **Type:** `str`
   * **Default value:** `None`
   *  **Example:** `''model'': ''gpt-4''`
  
2. `messages`
   * **Requirement: Required**
   * **Purpose:** A list containing the conversation's context (roles and content).
   * **Type:** List of dictionaries
   * **Default value:** No Default; you must provide messages
   *  **Example:** `[
  {"role": "system", "content": "You are a helpful assistant."},
  {"role": "user", "content": "What is AI?"}
]`
3. `max_tokens`
   * **Requirement: Optional**
   * **Purpose:** Set the maximum number of tokens (words/characters) the response can have.
   * * **Type:** ```int
   * **Default value:** **inf**
   *  **Valid Range:** 1 to the model's limit (e.g., 4096 for GPT-3.5-turbo)
   *  **Example:** `''max_tokens'': 100`

4. `temperature`
   * **Requirement: Optional**
   * **Purpose:** Controls how randomness/creativity of the AI's responses are.
   * Lower values = Deterministic and focused answers
   * Higher values = Creative and varied responses
   * * **Type:** ```float
   * **Default value:** 1.0
   *  **Valid Range:** [0,2]
   * **Example:** `''temperature'': 0.2`

5. `top_p`
   * **Requirement: Optional**
   * **Purpose:** Restricts the randomness by focusing on most probable tokens. Works as an alternative of temperature
      * `top_p = 1.0`: No restriction; full creativity
      * `top_p = 0.5`: Restricts to top 50% of likely options
   * * **Type:** `float`
   * **Default value:** 1.0
   * **Valid Range:** [0,1]
   * **Example:** `''top_p'': 0.7`

6. `n`
   * **Requirement: Optional**
   * **Purpose:** Specifies the number of responses to generate.
   * * * **Type:** `int`
   * **Default value:** 1
   * **Valid Range:** [1,inf]
   * **Example:** `''n'': 3`

7. `stream
   * **Requirement: Optional**
   * **Purpose:** Send the response incremently in real time.
   * * **Type:** `Bool`
   * **Default value:** False
   * **Valid Range:** True/False
   * **Example:** `''stream'': True`

8. `tools`
   * **Requirement: Optional**
   * **Purpose:** Enables external capabilities (e.g., code interpreter, browsing, etc.).
   * * **Type:** List of Tools
   * **Default value:** `None`
   * **Example:** `''tools'': [''code-interpreter'']`
---
**Practical Useage Example**

```{
  "model": "gpt-3.5-turbo",
  
  "messages": [
  
    {"role": "system", "content": "You are a math tutor."},
    
    {"role": "user", "content": "What is the square root of 144?"}
  ],
  
  "max_tokens": 50,
  
  "n": 2,
  
  "temperature": 0.3,
  
  "top_p": 1.0,
  
  "stream": false
  
}```

---
**Response**
* The model will use the "gpt-3.5-turbo" engine.
* It considers the context ("You are a math tutor").
* It generates 2 deterministic responses (low temperature) within 50 tokens.
* The response is not streamed but sent as a complete answer.

### **Mnemonic to Memorize Them**  
To remember these parameters easily, use the following mnemonic:  
**"My Magnificent Model Makes The Top-notch Streams True."**

Here’s how it maps to the parameters:  

- **M**: `model`  
- **M**: `messages`  
- **M**: `max_tokens`  
- **T**: `temperature`  
- **T**: `top_p`  
- **N**: `n`  
- **S**: `stream`  
- **T**: `tools`  
