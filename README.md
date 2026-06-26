Borderless Interview Template

This is an empty repository.

---
### Specification

The application should be able to receive API calls for a new or existing conversation with an LLM, and should include support for:

- Starting a new conversation
- Continuing an existing conversation
- two seperate endpoints

- Routing interactions to a specified LLM/model 
    - for now, using API call below to choose a single model
    - could be user specified (in future, adding other options for models)
- Recording the conversation (both input and output)
    - Storing conversation:
        - parent_conversation
            - ID
            - conversation_id
            - model_id
        - conversation
            - ID
            - time started
            - time ended: nullable
            - model_id
        - message
            - ID
            - message_type
            - content
            - timestamp
        - llm_model
            - ...
        - conversation_cost
            - conversation_id
            - tokens_used
            - total_cost

- Storing a quality metric for the final outcome of the interaction (manually supplied through an API call) 

(stretch)
- Allow conversations to be replayed to different LLMs/models to record the difference in result
- Allow system prompts to be stored and called before conversations are started

```
curl "https://generativelanguage.googleapis.com/v1beta/models/gemini-flash-latest:generateContent" \
  -H 'Content-Type: application/json' \
  -H 'X-goog-api-key: AIzaSyDfVUrRVM0ne-JBYcy9Rg0OjWO9SzFV6Is' \
  -X POST \
  -d '{
    "contents": [
      {
        "parts": [
          {
            "text": "Explain how AI works in a few words"
          }
        ]
      }
    ]
  }'
```

### Tech Stack

##### Frontend
- Typescript
- React
- Vite
    - fast compilation with HMR, on-demand module builds, good for small/single page apps
- Tailwind 
    - Straight forward style changes, quick to implement

##### API
- Python
- FastAPI
    - auto generates OpenAPI docs, making it easier to develop
    - quick to set up endpoints
    - can use pydantic validation out of box
- uv
    - Fast package manager, can handle virtual envs out of box, quick set up
- uvicorn
    - quick to set up and lightweight webserver
- SQLite
    - lightweight SQL DB
    - low infrastructure cost
    - suitable for small low-complexity apps
- alembic
    - db migrations# leftover-lunch-recommender
