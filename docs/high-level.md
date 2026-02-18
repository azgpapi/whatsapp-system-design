High-Level Design of Our Big Project Whatsapp! 

😎 Introduction & Goals 

- This architecture tries to achieve Horizontal scalability to suppport users  concurrent WebSocket connection. It starts simple, and scales to a magnificent number of users as complexity grows.  
- For simplicity purpose, this is the initial high level setup. 

📳 It all starts from mobile app, responsible to make consistent connection with Chat Server and handle UI. Manage local storage and retries when failed operation happen. 

🔃 We have load balancer that is responsible for handling and routing incoming traffic between UI and Chat Servers. We design for not only efficiency but for maintaining failure gracefully, so to remove SPOF(Single Point of Failure), we set 3 load balancers. 

=> We will use the dedicated and more persistent and efficient algorithms for load balancers.  

🗣️ Chat servers will maintain websocket connection with CLIENT, persistence two way communication. Intentionally 3 servers keeping failure will occur in mind to remove SPOF(Single Point of Failure)

* Message Queue Topic: 
📔 We introduce Message Queue, used for Decoupling message writing from delivery this is also a feature that allows us to handle failures gracefully. When one of chat servers receives message, it will acknowledge CLIENT message was sent and asynchronously pushes message to Message Queue for storage and delivery. 
Example: Kafka Message Queue or Rabbit MQ

🫙 Message Database, is responsible for database. We use NoSQL, it is better here like Cassandra or Dynamo DB because we need high write throughput for estimations. Since there will be billions of messages, we need massive write volume without slowing down. 

* Cache Topic: 
©️ Redis, which will be tracking which users are online, which chat server they are connected to and their last activity time stamp. Redis will help chat servers to make routing decisions faster because checking Redis storage will be faster with measure time milliseconds vs. querying directly from origin/database. This at scale will show huge difference

* Media Files (Photos, Videos, Voice Notes)
🗑️ We use Blob storage. AWS S3 or Google Cloud Storage. And we will distribute to CDN Network for fast retrieval of static files; cache popular files at edge locations worldwide. Useful first for static files + fast download for users and allocated geographically. One user will download from nearest server geographically. 

* Notification Service 
🔔 This is used for offline users either through Apple push notification service or Firebase Cloud Messaging for Android. When someone messages one while offline, A -> B, with push notification everything will happen. 

* Presence Service 
👥 Used for managing online and offline users. Recieves updates from Redis and publish presence changes. 