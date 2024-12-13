# Chat Application with AI-Powered Summarization

![Node.js](https://img.shields.io/badge/node.js-v14.0.0-brightgreen.svg)
![Express](https://img.shields.io/badge/express-v4.17.1-lightgrey.svg)
![MongoDB](https://img.shields.io/badge/mongodb-v6.3.0-green.svg)
![WebSockets](https://img.shields.io/badge/WebSockets-Enabled-yellow.svg)
![Ollama](https://img.shields.io/badge/ollama-brightgreen.svg)

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [User Manual](#user-manual)
- [Design and Implementation](#design-and-implementation)
- [Setup and Installation](#setup-and-installation)

---

## Project Overview

A real-time chat application enabling users to communicate within multiple chatrooms. The newly integrated **Chat Summary** feature leverages AI to provide concise summaries of conversations and messages, enhancing usability and productivity. Technologies used include **Node.js**, **Express**, **MongoDB**, **WebSockets**, and **Ollama**.

---

## Features

- **Real-Time Chat:** Engage in conversations within various chatrooms.
- **AI-Powered Chat Room Summarization:** Generate concise summaries of chatroom discussions.
- **AI-Powered Message Summarization:** Generate concise summaries of single messages.
- **User Profiles:** Manage and view user profiles.
- **Room Management:** Create and join chatrooms with custom names.
- **Secure Authentication:** User login and session management.
- **WebSocket Integration:** Real-time message broadcasting and updates.

---

## User Manual

### Chat Summary Feature

**Purpose:** Quickly grasp lengthy unread conversations without reading all the messages.

#### Accessing Summaries

1. **Enter a Chatroom:**
   - From the **Lobby**, click on the desired chatroom.

2. **Generate Summary:**
   - Click the **"Summary"** button within the chatroom interface.

3. **View Summary:**
   - A modal will display the summarized content.

4. **Close Summary:**
   - Click the **"×"** button on the modal to close it.

#### Example Workflow

1. **Entering a Chatroom:**
   - Open the chat application and log in with your credentials.

2. **Generating a Summary:**
   - Inside the chatroom lobby, click the **"Summary"** button on the right.
   - A modal window appears with the following summary:
     ```
     Here's a summary of the conversation in concise sentences: ...
     ```

3. **Utilizing the Summary:**
   - Use the summary to quickly recall the main topics without scrolling through the entire message history.

#### Benefits

- **Efficiency:** Understand main points swiftly.
- **Organization:** Keep track of multiple discussions.
- **Accessibility:** Enhance information retention and review.

---

## Design and Implementation

### Overview

The **Chat Summary** feature integrates the OLLAMA 3.2 AI model to generate concise summaries of chatroom conversations, enhancing user experience.

### AI Model Selection

#### Chosen Model: **OLLaMA 3.2**

- **Reason for Adoption:**
  - **Performance:** Effective text generation suitable for summarization.
  - **Cost-Effective:** Hosted locally, eliminating recurring API costs.
  - **Latency:** Reduced response times compared to external APIs.

#### Alternatives Considered

1. **GPT-4 by OpenAI:**
   - **Pros:** Highly capable in understanding and generating human-like text.
   - **Cons:** Requires API access with associated costs and potential latency issues.

2. **BERT (Bidirectional Encoder Representations from Transformers):**
   - **Pros:** Strong performance in understanding context within text.
   - **Cons:** Primarily designed for understanding rather than generating text; requires additional layers for summarization.

3. **T5 (Text-To-Text Transfer Transformer):**
   - **Pros:** Flexible for various NLP tasks, including summarization.
   - **Cons:** Computationally intensive for real-time applications; may require fine-tuning for optimal performance.

### Integration

1. **Client-Side (`app.js`):**
   - Initiates summary requests.
   - Displays summaries in the UI.

2. **Server-Side (`server.js`):**
   - Handles summary requests.
   - Interfaces with the AI model via a local API (`http://localhost:11434/api/generate`).

3. **AI Model Server:**
   - Hosts **OLLaMA 3.2**.
   - Processes summarization prompts and returns summaries.

**Workflow:**

1. User clicks **"Summary"** in a chatroom.
2. Client sends a GET request to `/chat/:room_id/summary`.
3. Server fetches messages, sends them to the AI model.
4. AI model returns a summary.
5. Server sends the summary back to the client.
6. Client displays the summary in a modal.

---

## Setup and Installation

### Prerequisites

- **Operating System:** Windows, macOS, or Linux.
- **Node.js:** v14.x or higher.
- **npm:** Comes with Node.js.
- **MongoDB:** v6.0 or higher.
- **AI Model Server:** Hosting **OLLaMA 3.2** accessible at `http://localhost:11434/api/generate`.

### Installation

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/yourusername/chat-application.git
   cd chat-application

2. **Install Ollama**

   ```bash
   go to https://ollama.com/download
   download and run the ollama.setup file
   go to terminal
   in the terminal of where the setup file is located type: ollama pull llama3.2
   try typing in the terminal of your cloned project folder: ollama run llama3.2:latest
   if it runs, you have succeeded in installing Ollama

2. **Load the Database:**
   
   ```bash
   type in the terminal: mongosh mongo
   then type: load('initdb.mongo')
   then type: load('initUsers.mongo')
   
3. **Run the server

   ```bash
   type in the terminal: nodemon server.js
   then navigate to your browser and open localhost:3000 
