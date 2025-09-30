# 📖 Chat Resource Documentation

## 🔹 Exports

### Client-side (`cl_chat.lua`)

- **`addMessage(message)`**  
  Adds a message to the chat.  
  - `message: string | table` → Text or object with properties (args, color, templateId, etc).

- **`addSuggestion(name, help, params?)`**  
  Adds a command suggestion to the chat.  
  - `name: string` → Command name (e.g., `/car`)  
  - `help: string` → Help text  
  - `params?: table` → Additional parameters

---

### Server-side (`sv_chat.lua`)

- **`addMessage(target?, message)`**  
  Sends a message to a player’s chat or globally.  
  - `target: number | -1` → Player ID or `-1` for all  
  - `message: table` → Message structure (`args`, `color`, `template`, etc.)

- **`registerMessageHook(hook)`**  
  Registers a hook to intercept chat messages.  
  - `hook: function(source, message, hookRef)`  
    - `hookRef.updateMessage(table)` → Updates message data  
    - `hookRef.cancel()` → Cancels the message  
    - `hookRef.setSeObject(object)` → Sets permission object  
    - `hookRef.setRouting(target)` → Sets message target  

- **`registerMode(modeData)`**  
  Registers a new chat mode (e.g., channels).  
  - `modeData: table`  
    - `name: string` → Unique identifier  
    - `displayName: string` → Display name  
    - `color?: string` → Hex color (`#fff`)  
    - `isChannel?: boolean` → Whether it’s a channel  
    - `isGlobal?: boolean` → Whether it’s global  
    - `seObject?: string` → ACE object for permission  
    - `cb: function(source, message, hookRef)` → Callback on message send  

---

## 🔹 Events

### Client-side

- **`chatMessage(author, color, text)`** *(deprecated, use `chat:addMessage`)*  
- **`chat:addMessage(message)`** → Adds a message  
- **`chat:addSuggestion(name, help, params?)`** → Adds a suggestion  
- **`chat:addSuggestions(suggestions)`** → Adds multiple suggestions  
- **`chat:removeSuggestion(name)`** → Removes a suggestion  
- **`chat:addMode(mode)`** → Adds a chat mode  
- **`chat:removeMode(name)`** → Removes a chat mode  
- **`chat:addTemplate(id, html)`** → Adds a custom template  
- **`chat:clear`** → Clears the chat  
- **`chat:init`** → Chat initialization (triggered on NUI load)  
- **`_chat:messageEntered(author, color, message, mode)`** → Internal for message sending  

---

### Server-side

- **`chat:init` (player join)** → Sends available commands and modes to the player  
- **`chat:addTemplate(id, html)`** → Adds a global template  
- **`chat:addMessage(message)`** → Adds a global message  
- **`chat:addSuggestion(name, help, params?)`** → Adds a global suggestion  
- **`chat:removeSuggestion(name)`** → Removes a global suggestion  
- **`chat:clear`** → Clears chat for everyone  
- **`_chat:messageEntered(author, color, message, mode)`** → Player sent a message   
- **`chatMessage(source, author, text)`** → Message routed by the server  
- **`playerJoining`** → Native event (shows join message)  
- **`playerDropped(reason)`** → Shows player quit message  

---

## 🔹 Usage Examples

### Client-side Example: `addMessage`
```lua
-- Send a simple text message to the chat
exports["chat"]:addMessage("Hello world!")

-- Send a formatted message
exports["chat"]:addMessage({
    color = { 255, 0, 0 },
    args = { "System", "Server restart in 10 minutes!" }
})
```

### Client-side Example: `addSuggestion`
```lua
-- Send a simple text message to the chat
-- Send a formatted message
exports["chat"]:addSuggestion("/car", "Spawn a vehicle", {
    { name = "model", help = "Vehicle model name" }
})
```

⚙️ This documentation covers the **exports** and **events** (both public and internal) provided by the `chat` resource.
