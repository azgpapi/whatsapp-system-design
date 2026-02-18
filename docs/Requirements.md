😎 Whatsapp App Requirements: 

Requirements: What are we building 🥱? 

Core Functional Requirements: 💪 
1. Users can send and receive text messages in 1:1 chats 
2. Group chats with up to 100 participants
3. Messages delivered while users are offline get queued up for 30 days 
4. Media attachments; images, videos, audio clips  
5. Message status tracking; sent, delivered, read 
6. Online/Offline status with "last seen"

Non-Functional Requirements: 🟥
1. Low-latency delivery (under 500ms when users are online)
2. Guaranteed message delivery (message can't jsut disappear)
3. Handle billions of users with high throughput 
4. Don't store messages on servers longer than necessary 
5. Stay resilient when individual components fail 


Back-of-the-Envelope to Understand the Scale: ⭐
User Metrics: 
- 1 billion registered users 
- 500 million daily active users 
- 50 million concurrent connections during peak hours 
- Average 10-20 messages per user daily 

Message Estimations: ✉️
- Daily messages: 500M users * 20 messages = 10 billion messages/day 
- That's roughly 115,000 messages per second on average 
- Peak hours: 3-5x = 350,000-500,000 

Storage Calculation: 💼
- Each message with metadata averages about 1KB 
- Daily storage: 1KB * 10B messages = 10 TB/day
- Annual storage: 3.6 PB/year 

Bandwidth: 🎲
- 50M concurrent connections at peak
- Each connection averages 10KB/s for active messaging, that's 500 GB/s of bandwidth  



Requirements Engineering Thinking Process Finished 🤖

