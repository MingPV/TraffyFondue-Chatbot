<!-- eslint-disable vue/html-self-closing -->
<template>
  <div class="chat-container">
    <div class="chat-header">
      <h1>AI Chatbot Assistant</h1>
      <p>Your virtual assistant for all your needs</p>
    </div>
    <div class="chat-messages">
      <div
        v-for="(message, index) in messages"
        :key="index"
        :class="['message', message.sender]"
      >
        <p>{{ message.text }}</p>
      </div>
    </div>
    <div class="chat-input">
      <input
        v-model="userInput"
        type="text"
        placeholder="Type your message..."
        @keyup.enter="sendMessage"
      />
      <button @click="sendMessage">Send</button>
    </div>
  </div>
</template>

<script setup>
const messages = ref([
  { sender: "bot", text: "Welcome! How can I assist you today?" },
]);

const userInput = ref("");

function sendMessage() {
  if (userInput.value.trim() === "") return;

  messages.value.push({ sender: "user", text: userInput.value });
  userInput.value = "";

  // Simulate bot response
  setTimeout(() => {
    messages.value.push({
      sender: "bot",
      text: "Thank you for your message. I am here to help!",
    });
  }, 1000);
}
</script>

<style scoped>
.chat-container {
  display: flex;
  flex-direction: column;
  height: 90vh;
  max-width: 700px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 5vh;
  border: 1px solid #333;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.5);
  background-color: #1e1e1e;
  color: #f5f5f5;
}

.chat-header {
  background-color: #2a2a2a;
  color: #f5f5f5;
  padding: 20px;
  text-align: center;
  border-bottom: 1px solid #333;
}

.chat-header h1 {
  margin: 0;
  font-size: 24px;
  font-weight: bold;
}

.chat-header p {
  margin: 5px 0 0;
  font-size: 14px;
  opacity: 0.8;
}

.chat-messages {
  flex: 1;
  padding: 20px;
  overflow-y: auto;
  background-color: #1e1e1e;
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.message {
  padding: 12px 16px;
  border-radius: 12px;
  max-width: 75%;
  font-size: 14px;
  line-height: 1.5;
  word-wrap: break-word;
}

.message.bot {
  background-color: #2a2a2a;
  align-self: flex-start;
  color: #f5f5f5;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
}

.message.user {
  background-color: #4a90e2;
  color: white;
  align-self: flex-end;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
}

.chat-input {
  display: flex;
  padding: 16px;
  background-color: #2a2a2a;
  border-top: 1px solid #333;
}

.chat-input input {
  flex: 1;
  padding: 12px;
  border: 1px solid #444;
  border-radius: 8px;
  margin-right: 10px;
  font-size: 14px;
  background-color: #1e1e1e;
  color: #f5f5f5;
}

.chat-input input::placeholder {
  color: #888;
}

.chat-input button {
  padding: 12px 20px;
  background-color: #4a90e2;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.chat-input button:hover {
  background-color: #357ab8;
}
</style>
