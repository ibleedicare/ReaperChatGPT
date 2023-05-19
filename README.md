# Reaper OpenAI

Use openai api inside of Reaper

to use this lua script load it in your own reascript after the install 

```lua
local path = ({reaper.get_action_context()})[2]:match('^.+[\\//]')
package.path = path .. "?.lua"

-- User OpenAI 
local OpenAI = require("openai")
-- On Windows 10 curl is available under System32
local openai = OpenAI:new({key = "YOUR_API_KEY", curl_path=[[C:\Windows\System32\curl.exe]]})

-- Chat with ChatGPT

message = {
  {role = "system", content = "You are an AI Assistant"}, -- Here is your system prompt
  {role = "user", content = "How do I create track in REAPER ?"} -- Here is what the user will send to OpenAI 
}

-- use the chat function 

local response = openai:chat("gpt-3.5-turbo", message)

-- Get the content of the response like in the Python openai package

response = response.choices[1].message.content
```
