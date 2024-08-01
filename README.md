<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Multi-user chat application">
    <meta name="keywords" content="chat, multi-user chat, online chat">
    <meta name="robots" content="index, follow">
    <title>Multi-User Chat Application</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: #f4f4f4;
        }
        .container {
            display: flex;
            height: 100vh;
        }
        .sidebar {
            width: 250px;
            background: #333;
            color: #fff;
            padding: 10px;
            box-shadow: 2px 0 5px rgba(0,0,0,0.1);
            display: flex;
            flex-direction: column;
        }
        .sidebar h3 {
            margin-top: 0;
        }
        .user-list {
            flex: 1;
            overflow-y: auto;
        }
        .chat-area {
            flex: 1;
            display: flex;
            flex-direction: column;
        }
        .chat-header {
            background: #444;
            color: #fff;
            padding: 10px;
        }
        .chat-messages {
            flex: 1;
            overflow-y: auto;
            padding: 10px;
            background: #fff;
        }
        .chat-footer {
            display: flex;
            padding: 10px;
            background: #eee;
        }
        .chat-footer textarea {
            flex: 1;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            margin-right: 10px;
        }
        .chat-footer button {
            background: #007bff;
            color: #fff;
            border: none;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
        }
        .chat-footer button:hover {
            background: #0056b3;
        }
        .message {
            margin-bottom: 10px;
        }
        .message.user {
            color: #007bff;
        }
        .message.system {
            color: #666;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="sidebar">
            <h3>Users</h3>
            <div class="user-list" id="userList">
                <!-- User list will be dynamically populated here -->
            </div>
        </div>
        <div class="chat-area">
            <div class="chat-header">
                <h2>Chat Room</h2>
            </div>
            <div class="chat-messages" id="chatMessages">
                <!-- Chat messages will be dynamically populated here -->
            </div>
            <div class="chat-footer">
                <textarea id="messageInput" placeholder="Type your message here..."></textarea>
                <button id="sendMessage">Send</button>
            </div>
        </div>
    </div>
    <script>
        const userList = document.getElementById('userList');
        const chatMessages = document.getElementById('chatMessages');
        const messageInput = document.getElementById('messageInput');
        const sendMessageButton = document.getElementById('sendMessage');

        // Simulate user list
        const users = ['User1', 'User2', 'User3'];
        users.forEach(user => {
            const userItem = document.createElement('div');
            userItem.textContent = user;
            userList.appendChild(userItem);
        });

        // Simulate chat messages
        const messages = [
            {user: 'User1', text: 'Hello everyone!', type: 'user'},
            {user: 'User2', text: 'Hi User1!', type: 'user'},
            {user: '', text: 'System: User3 joined the chat', type: 'system'}
        ];
        messages.forEach(message => {
            const messageDiv = document.createElement('div');
            messageDiv.textContent = message.user ? `${message.user}: ${message.text}` : message.text;
            messageDiv.classList.add('message', message.type);
            chatMessages.appendChild(messageDiv);
        });

        // Send message
        sendMessageButton.addEventListener('click', () => {
            const messageText = messageInput.value.trim();
            if (messageText) {
                const newMessage = document.createElement('div');
                newMessage.textContent = `You: ${messageText}`;
                newMessage.classList.add('message', 'user');
                chatMessages.appendChild(newMessage);
                messageInput.value = '';
                chatMessages.scrollTop = chatMessages.scrollHeight;
            }
        });
    </script>
</body>
</html>

      
