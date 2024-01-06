# simple-gpt-api
#### api responsible for very basic integration with open ai and with long term memory tools like regular database
#### without vector databases



test locall endpoint: http://127.0.0.1:8000/aidevs-4.4 with curl with json body {"question": "This is question"} 
curl -X POST "http://localhost:8000//aidevs-4.4/" -H  "accept: application/json" -H  "Content-Type: application/json" -d "{\"question\":\"This is question\"}"
