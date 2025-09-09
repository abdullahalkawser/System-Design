# System-Design
            System Design Notes
1️⃣ HLD (High-Level Design) vs LLD (Low-Level Design)
🔹 HLD (High-Level Design)
Definition (English): It shows the overall system architecture, main components, and how they interact.


বাংলায়: পুরো সিস্টেমের বড় ছবি/architecture বোঝায়। কোন কোন মডিউল থাকবে, তারা কিভাবে connect হবে তা define করে।


👉 Features:
Big picture view of system


Technology stack, architecture (Monolithic / Microservices)


Modules and their relationships


Focus: What system will do


👉 Example:
 Banking system → Modules: Login, Accounts, Transactions, Reports.

🔹 LLD (Low-Level Design)
Definition (English): It gives detailed logic of each component/module.


বাংলায়: প্রতিটি মডিউলের ভেতরে কীভাবে কাজ হবে তা detail level এ বোঝায়।


👉 Features:
Class diagrams, database schema


API design, function-level details


Algorithms and pseudo code


Focus: How system will work


👉 Example:
 Transaction Module → Functions: debitAccount(), creditAccount(), validation rules, DB tables.

2️⃣ Functional vs Non-Functional Requirements
🔹 Functional Requirements
Definition (English): Features and functions the system must perform.


বাংলায়: সিস্টেম কী কী কাজ করতে পারবে, সেই ফাংশন/ফিচারগুলো।


👉 Examples:
User login & signup


Payment processing


Search option


Upload documents



🔹 Non-Functional Requirements (NFR)
Definition (English): Quality attributes and constraints of the system.


বাংলায়: সিস্টেম কতটা দ্রুত, সুরক্ষিত, reliable ইত্যাদি। কাজের বাইরে quality measure।


👉 Examples:
Performance → System must handle 10k users at once


Security → Data encryption, authentication


Scalability → Horizontal scaling support


Reliability → 99.9% uptime guarantee



📝 Quick Revision Table
Topic
Focus
Example
HLD
What system will do (Big picture)
Banking System Modules
LLD
How system will work (Details)
Functions, DB schema
Functional Req.
System features (Do’s)
Login, Payment, Search
Non-Functional Req.
Quality attributes
Speed, Security, Uptime



📌 Monolithic Architecture
🔹 Definition
English: Monolithic architecture is a single unified software system where all the components (UI, business logic, database, etc.) are tightly coupled and run as one unit.


বাংলায়: Monolithic architecture হলো এমন একটি সফটওয়্যার ডিজাইন যেখানে সবকিছু একসাথে (একটা ব্লকের মতো) তৈরি হয় — যেমন UI, business logic, database সব এক জায়গায় থাকে।



🔹 Characteristics (বৈশিষ্ট্য)
Single codebase → পুরো অ্যাপ্লিকেশন একটাই কোডবেসে থাকে।


Tightly coupled → সব মডিউল একে অপরের সাথে strongly connected।


Single deployable unit → অ্যাপ্লিকেশনকে আলাদা আলাদা করে নয়, বরং পুরোটা একসাথে deploy করতে হয়।


Simple to develop initially → ছোট প্রজেক্টে সহজে তৈরি করা যায়।



🔹 Advantages (সুবিধা)
✅ Easy to develop for small apps
 ✅ Easy to test (unit test simple)
 ✅ Single deployment process
 ✅ Performance better (no network latency between services)

🔹 Disadvantages (অসুবিধা)
❌ Large codebase → Hard to maintain
 ❌ Scalability problem → পুরো অ্যাপ scale করতে হয়, আলাদা module নয়
 ❌ Deployment risk → ছোট change করলেও পুরো system redeploy করতে হয়
 ❌ Technology lock-in → সব মডিউল same tech stack এ থাকতে হয়

🔹 Example
E-commerce Monolith App → Product management, user authentication, payment system সব এক প্রজেক্টে build করা।


যদি payment system-এ bug হয় → পুরো app আবার deploy করতে হবে।








Difference Between Monolithic and Microservices Architecture



🔹 Monolithic Architecture
Definition (English): Single unified application where all components (UI, business logic, DB) are tightly coupled.


বাংলায়: সব মডিউল/ফিচার এক কোডবেসে থাকে, সবকিছু একসাথে deploy হয়।


👉 Example: একটি e-commerce app যেখানে product, payment, user সবকিছু এক project-এর মধ্যে।
 Monolithic Architecture-এ Latency
Monolithic-এ:
সব modules একই process / server-এ থাকে।


Internal calls function calls এর মাধ্যমে হয়।


তাই communication অনেক দ্রুত হয়।


উদাহরণ:
 User requests “Place Order” → Server internally function call দিয়ে Payment + Inventory + Notification process করে → Response খুব দ্রুত আসে।
Latency Factor:
সাধারণত low latency কারণ internal calls network এর মধ্য দিয়ে যায় না।


Bottleneck শুধু server CPU/memory।


✅ ফায়দা: Internal communication অনেক দ্রুত।
 ❌ অসুবিধা: অ্যাপ বড় হলে এবং load বেশি হলে single server-এ congestion হতে পারে → latency বাড়ে।


🔹 Microservices Architecture
Definition (English): Application is broken into small independent services, each running on its own and communicating via APIs.


বাংলায়: বড় অ্যাপকে ছোট ছোট সার্ভিসে ভাগ করা হয়, প্রতিটি আলাদা ভাবে deploy ও scale করা যায়।
Microservices Architecture
✅ Advantages
Scalability → Scale only the required service (e.g., Payment service)।


Independent Deployment → একেকটা service আলাদা deploy করা যায়, কম risk।


Flexibility → প্রতিটি সার্ভিসে আলাদা tech stack ব্যবহার করা যায়।


Fault Isolation → এক সার্ভিস down হলেও পুরো system down হয় না।


Faster Development (Large Teams) → Multiple teams একসাথে different services নিয়ে কাজ করতে পারে।


Better Maintainability → ছোট codebase হওয়ায় সহজে modify করা যায়।


Cloud Friendly → Containerization (Docker, Kubernetes) এর সাথে ভালোভাবে fit করে।


❌ Disadvantages
Complexity in Management → অনেক সার্ভিস deploy, monitor, manage করা কঠিন।


Performance Overhead → API call/network latency বেশি।


Testing Difficulty → Integration testing harder due to many services।


DevOps Dependency → Automation, CI/CD pipeline, orchestration tools প্রয়োজন।


Data Management Issue → প্রতিটি সার্ভিস আলাদা database ব্যবহার করলে consistency maintain করা কঠিন।


Skill Requirement → Developers & Ops team এর বেশি জ্ঞান দরকার (cloud, containers, orchestration)।




👉 Example: E-commerce app → Payment service আলাদা, Product service আলাদা, User 
service আলাদা।
Microservices-এ Latency
Microservices-এ:
প্রতিটি module আলাদা service হিসেবে থাকে।


Services একে অপরের সাথে network calls (HTTP/REST, gRPC, message queue) এর মাধ্যমে communicate করে।


তাই communication slow হয়।


উদাহরণ:
 User requests “Place Order” → Order Service → Payment Service → Inventory Service → Notification Service → Response
Latency Factor:
Network latency + serialization/deserialization + multiple service hops → মোট latency Monolithic-এর চেয়ে বেশি।


প্রতিটি service independent, তাই এক service crash করলে সব system hang হয় না।


✅ ফায়দা: Fault isolation, independent scaling।
 ❌ অসুবিধা: Network latency বেশি → response time ধীর।

⚡ তুলনামূলক (Latency)
Feature
Monolithic
Microservices
Internal Communication
Function call → very fast
Network call → slower
Average Latency
Low
Higher (depends on network & hops)
Scalability
Difficult
Easy (scale only needed services)
Fault Tolerance
Low
High


💡 সারাংশ:
Monolithic → low latency, কিন্তু scale/maintenance কঠিন।


Microservices → higher latency (network calls), কিন্তু scale, maintain ও fault tolerance অনেক ভালো।


📝 Comparison Table
Feature
Monolithic
Microservices
Structure
Single codebase, tightly coupled
Multiple small services, loosely coupled
Deployment
Whole app deployed together
Each service deployed independently
Scalability
Hard (must scale entire app)
Easy (scale specific service only)
Technology Stack
Same tech for all modules
Different services can use different tech
Performance
Faster (no network calls between modules)
Slightly slower (services communicate via APIs)
Maintenance
Difficult when codebase grows
Easier, as services are smaller
Failure impact
One bug may crash whole system
Failure limited to single service
Best for
Small/medium apps
Large, complex, scalable apps






1️⃣ What is Latency? (Latency কী?)

Latency মানে হলো network delay – কোনো data একটি point থেকে অন্য point এ পৌঁছাতে কত সময় লাগে।
Bangla-English:
 “Latency হলো network-এ data পাঠানোর সময়। যদি latency বেশি হয়, তাহলে network slow অনুভূত হয়।”


Example:
ধরো তুমি বাংলাদেশ থেকে USA-এর server-এ request পাঠালে, সেই request-এর উত্তর আসতে যা সময় লাগে— সেটাই latency।


Measurement:
মাপা হয় milliseconds (ms) এ।



2️⃣ Types of Latency (Latency-এর ধরন)
Propagation latency:


Data signal কতো দ্রুত network medium (cable, fiber, wireless) দিয়ে travel করছে।


Transmission latency:


Data send করতে কত সময় লাগে (data size এবং bandwidth এর উপর নির্ভর করে)


Processing latency:


Router, switch বা server data process করতে কত সময় নিচ্ছে


Queuing latency:


Network এ traffic congestion হলে waiting time বৃদ্ধি পায়





3️⃣ How to Reduce Latency (Latency কমানোর উপায়)
Bangla-English tips:


Use a CDN (Content Delivery Network)


Data user-এর কাছাকাছি server থেকে provide করা হয় → distance কমে latency কমে


Caching


Frequently accessed data local server বা browser-এ রাখলে server request কম হয় → latency কমে


Optimize network path


Direct routes use করা, unnecessary hops কমানো


Upgrade bandwidth


Bigger bandwidth → transmission latency কম হয়


Use faster servers / edge servers


Processing latency কমানো যায়



4️⃣ CDN vs Caching (Bangla-English)
Feature
CDN (Content Delivery Network)
Caching
Purpose
User-এর কাছে content provide করা
Frequently used data store করা
Location
Multiple global edge servers
Local server/browser
Example
Akamai, Cloudflare, AWS CloudFront
Browser cache, Redis, Memcached
Latency Impact
Reduce distance-based latency
Reduce server processing latency
Use Case
Static content like images, videos
Dynamic/static data for fast access

Bangla-English summary:
CDN = global scale latency reduce



Caching = server load কমিয়ে latency reduce







Throughput in System Design

Definition:
 Throughput হলো একটি system কত efficiently কাজ করছে বা কত request/process/unit time এ complete করতে পারছে।
সহজভাবে বললে: “একটা system কত request/transaction/operation per second handle করতে পারে।”


Unit: requests/sec, transactions/sec, operations/sec



Example (Bangla + English)
Scenario:
 ধরা যাক, তুমি একটা online shopping website বানাচ্ছ।
System Input: Users sending requests to view products, place orders, etc.


Throughput: যদি system এক second-এ 1000 requests successfully process করতে পারে, তাহলে system-এর throughput = 1000 requests/sec।


Latency vs Throughput:


Latency = কত time লাগে এক individual request complete করতে।


Throughput = কত request system এক unit time-এ handle করতে পারে।


Bangla Example:
ধরো, Amazon website-এ 1 মিনিটে 60,000 order request আসে।


যদি system 1 মিনিটে সব 60,000 request successfully process করে → throughput = 1,000 requests/sec।



Key Points for System Design
High throughput → System can handle more requests per second.


Throughput can be increased by:


Horizontal scaling (more servers)


Load balancing


Caching frequent data


Database optimization


Trade-off: High throughput system may have higher latency per request if resources are stretched.
How to Improve Throughput
1. Horizontal Scaling (Scale Out)
Explanation: একের বেশি server/instance ব্যবহার করা।


Bangla Example: যদি তোমার website এক server-এ 1000 request/sec handle করে, দুই server এ handle হবে ~2000 request/sec।


Method: Use load balancers to distribute traffic.



2. Vertical Scaling (Scale Up)
Explanation: Existing server-এর resource (CPU, RAM, Network) বাড়ানো।


Example: একটি powerful CPU + বেশি RAM → বেশি requests একই server-এ handle করা সম্ভব।



3. Caching
Explanation: Frequently used data memory বা cache-এ রাখা যাতে database access কম লাগে।


Bangla Example: Product info cache-এ রাখলে, user request handle করার জন্য database query করার প্রয়োজন পড়ে না → faster processing → higher throughput.


Tools: Redis, Memcached



4. Database Optimization
Explanation: Efficient queries, indexing, read replicas.


Bangla Example: Large table scan করে data fetch করলে slow হবে → indexing করলে request fast হবে → throughput বাড়বে।


Tips: Use sharding, partitioning, or read replicas for high read load.



5. Asynchronous Processing
Explanation: কিছু task background-এ করা, main request fast handle করা।


Example:


User places order → enqueue task for email notification → user doesn’t wait → throughput increases.


Tools: RabbitMQ, Kafka, Celery



6. Reduce Bottlenecks
Identify slow components (CPU, DB, network) and optimize.


Example: If payment processing is slow → use payment gateways asynchronously or batch processing.



7. Optimize Network / API Calls
Minimize data transfer and API latency.


Example: Compress responses, batch multiple requests → faster handling → higher throughput.



💡 Quick Tip:
Latency and throughput are related but different. Sometimes reducing latency improves throughput, but sometimes increasing parallelism improves throughput without affecting latency too much.
Advantages of High Throughput in System Design
1. Better User Experience (বেশি Smooth & Fast)
High throughput means system can handle more requests quickly → users don’t face delays or timeouts.


Example: Online shopping website can handle thousands of users at the same time without slowing down.



2. Scalability (Scale করতে সহজ)
Throughput optimization techniques (horizontal scaling, caching, async processing) help system scale easily for more users.


Example: During festive sales, system can handle spike in traffic without crashing.



3. Cost Efficiency (কম খরচে বেশি কাজ)
Optimized throughput reduces resource wastage.


Example: Efficient DB queries & caching → fewer servers needed → cost saves money.



4. Reliability (More Reliable System)
System with high throughput can handle heavy loads without failing.


Example: Even if 10,000 requests come simultaneously, system processes all without downtime.



5. Competitive Advantage
A fast, high-throughput system retains more users and customers.


Example: Fast-loading app → users stay → business grows.



6. Better Resource Utilization
System processes more tasks per second → CPU, memory, network used efficiently.



💡 Summary:
 High throughput = fast, reliable, scalable, cost-efficient system. It’s critical for websites, APIs, databases, microservices and almost all modern systems.

Availability (Bangla + English Notes)
🔹 What is Availability?


English:
 Availability refers to how much a system is operational and accessible when needed. It is usually measured as a percentage of uptime (e.g., 99.9% availability).
Bangla:
 Availability মানে হলো, একটা সিস্টেম কতক্ষণ সচল ও ব্যবহারযোগ্য থাকে। সাধারণত এটি uptime শতাংশ দিয়ে প্রকাশ করা হয় (যেমন: 99.9% availability)।
Formula (Approx):
Availability=UptimeUptime+DowntimeAvailability = \frac{Uptime}{Uptime + Downtime}Availability=Uptime+DowntimeUptime​
🔹 Replication
English:
 Replication means copying data or services across multiple servers or locations. If one server fails, another copy can serve the request.
Example: Database replication (Master → Slave).


Goal: Improve read performance & availability.


Problem: Data consistency issues (may lag).


Bangla:
 Replication মানে হলো একই ডেটা বা সার্ভিস একাধিক সার্ভারে কপি করে রাখা। যদি একটি সার্ভার নষ্ট হয়, অন্য সার্ভার থেকে সার্ভিস চালু থাকে।
উদাহরণ: Database replication (Master → Slave)।


মূল উদ্দেশ্য: read performance ও availability বাড়ানো।


সমস্যা: ডেটা consistent না থাকার ঝুঁকি থাকে (delay হতে পারে)।



🔹 Redundancy
English:
 Redundancy means having extra hardware, software, or systems as backup to ensure no single point of failure.
Example: Two power supplies in a server, RAID disks.


Goal: Improve fault tolerance & high availability.


Problem: Expensive, needs proper failover mechanism.


Bangla:
 Redundancy মানে হলো অতিরিক্ত রিসোর্স রাখা (হার্ডওয়্যার, সফটওয়্যার, নেটওয়ার্ক) যাতে কোনো একটিতে সমস্যা হলে পুরো সিস্টেম বন্ধ না হয়ে যায়।
উদাহরণ: Server এ ২টা পাওয়ার সাপ্লাই, RAID ডিস্ক।


মূল উদ্দেশ্য: fault tolerance ও high availability নিশ্চিত করা।


সমস্যা: খরচ বেশি এবং সঠিক failover মেকানিজম লাগবে।



🔹 Replication vs Redundancy (Comparison Table)
Feature
Replication
Redundancy
Definition
Copy of data/services across servers
Extra backup hardware/system
Focus
Data & performance
Fault tolerance & reliability
Example
Database replication, CDN
RAID, multiple servers, backup power
Problem
Data inconsistency
Costly implementation
Availability Impact
Improves read availability & scalability
Ensures system continues even if part fails


🔹 Summary (Bangla + English Mix)
👉 Availability = System কতক্ষণ সচল থাকে।
 👉 Replication = Data/Service multiple copies → বেশি availability & read performance, but consistency problem।
 👉 Redundancy = Backup system/hardware → বেশি fault tolerance & high availability, but expensive।

Availability in Monolithic vs Microservices (Replication vs Redundancy)
🔹 Monolithic System
English:
A monolithic system is one large codebase and tightly coupled.


Replication here usually means replicating the whole application in multiple servers.


Redundancy means having backup servers, load balancers, database failover.


Availability Impact:
Replication: Improves performance but scaling is limited (you have to replicate the entire app).


Redundancy: If one server crashes, backup can take over, but single point of failure (database, shared state) still exists.


Bangla:
Monolithic system হলো একটা বড় কোডবেস যেখানে সব মডিউল একসাথে থাকে।


Replication মানে পুরো application এর কপি করে একাধিক সার্ভারে চালানো।


Redundancy মানে backup server, load balancer, database failover ব্যবহার করা।


➡️ Availability:
Replication এ performance কিছুটা বাড়ে কিন্তু পুরো app replicate করতে হয়, flexible নয়।


Redundancy থাকলেও database বা অন্য dependency fail হলে সিস্টেম পুরোপুরি down হয়ে যেতে পারে।



🔹 Microservices System
English:
A microservices system splits the app into independent services (Auth, Payment, Orders, etc.).


Replication happens per service (e.g., 3 replicas of Payment service only).


Redundancy ensures each service has multiple instances, databases are sharded/replicated.


Availability Impact:
Replication: Much more efficient, only critical services are replicated.


Redundancy: No single point of failure, because even if one service instance dies, others keep running.


Bangla:
Microservices system এ application কে ছোট ছোট স্বাধীন সার্ভিসে ভাগ করা হয় (যেমন: Auth, Payment, Orders)।


Replication মানে প্রয়োজনীয় সার্ভিসগুলো আলাদা করে replicate করা যায় (যেমন শুধু Payment service এর ৩টা কপি রাখা)।


Redundancy মানে প্রতিটি সার্ভিসের backup instance থাকে, database আলাদা shard/replica আকারে রাখা হয়।


➡️ Availability:
Replication এ targeted scalability পাওয়া যায় (critical service বেশি replicate করা যায়)।


Redundancy এ কোনো single point of failure থাকে না। এক সার্ভিস down হলেও বাকি system চলতে পারে।



🔹 Comparison Table
Aspect
Monolithic
Microservices
Replication
Whole app replicated → heavy
Per-service replication → efficient
Redundancy
Backup servers, but still single DB failure risk
Each service + DB has redundancy → no single point of failure
Availability
Limited, database often bottleneck
Higher, resilient & fault tolerant
Scalability
Scale entire app only
Scale specific services independently


✅ Summary:
Monolithic + Replication/Redundancy = availability improves a bit, but bottlenecks remain (DB, app size).


Microservices + Replication/Redundancy = high availability, because system is distributed, fault-tolerant, and scalable.


🔹 What is CAP Theorem?
CAP theorem (by Eric Brewer) says:
 In a Distributed System, you can only guarantee two out of the three properties:
C = Consistency


Every node sees the same data at the same time.


Example: যদি তুমি একটা ডেটাবেসে update করো, সব server/user সেই updated data একই সময়ে পাবে।


A = Availability


The system always responds (even if some part fails).


Example: Server down হলেও অন্য server থেকে তোমার query-এর উত্তর পাবে।


P = Partition Tolerance


System continues working even if communication between nodes breaks (network failure)।


👉 CAP theorem: In distributed systems, you can only pick 2 (CA, CP, AP) but not all 3 fully.

🔹 Examples in Bangla-English
1. CA System (Consistency + Availability, no Partition Tolerance)
Works fine when no network partition.


Example: Traditional SQL database on a single server.


Consistency আছে (data সবসময় correct),


Availability আছে (server up থাকলে সবসময় response দিবে),


But যদি server fail করে বা network partition হয় → পুরো সিস্টেম down.



2. CP System (Consistency + Partition Tolerance, no Availability)
System prefers correctness over availability.


Example: MongoDB, HBase (in strict consistency mode)


যদি network issue হয়, system data consistent রাখে, কিন্তু কিছু সময়ের জন্য unavailable হতে পারে।


যেমন ব্যাংকের transaction system — better to block request than give wrong balance।



3. AP System (Availability + Partition Tolerance, no Consistency)
System always responds, even if not fully consistent.


Example: Cassandra, DynamoDB


Network problem হলেও response দিবে, কিন্তু কিছু data eventually consistent হবে।


যেমন: Facebook post like count – একসাথে সব user এর কাছে এক timing এ update নাও হতে পারে, কিন্তু later ঠিক হয়ে যাবে।



🔹 বাংলা Example (Daily Life)
ধরা যাক তুমি আর তোমার friend একই Google Doc edit করছো:
যদি সবসময় same content দেখাও (Consistency) + server সবসময় online থাকে (Availability), তখন network problem হলে (Partition) কাজ করবে না → CA.


যদি তোমার net problem হয়, system হয়তো তোমার access block করবে data loss এড়াতে → CP.


যদি তোমার net problem হয়, তাও তুমি edit করতে পারবে কিন্তু পরে sync হবে (eventual consistency) → AP.



👉 In System Design Interviews, তুমি বলতে পারো:
Banking system prefers CP (Consistency over Availability).


Social media (Facebook, Twitter) prefers AP (Availability over strict Consistency).


Small single-server apps are CA.





📌 Lamport Logical Clock (Simple Notes)

Distributed system-এ একটাই global ঘড়ি (clock) নেই।


তাই event কোনটা আগে/পরে ঘটলো তা বুঝতে Lamport Clock ব্যবহার হয়।


প্রতিটি process (P1, P2, …) নিজের একটা counter (LC) রাখে।



🔹 Rules (Bangla-English mix)
Internal Event → LC = LC + 1


Send Message → LC = LC + 1, message এর সাথে LC attach করে পাঠাবে


Receive Message → LC = max(own LC, received LC) + 1



📖 সুন্দর Example
ধরা যাক দুইটা process আছে: P1 আর P2
👉 শুরুতে:
LC1 = 0


LC2 = 0



✅ Step 1 – Internal Event (P1)
P1 কিছু কাজ করলো (যেমন calculation করলো)


Rule: LC = LC + 1


LC1 = 1



✅ Step 2 – P1 sends message to P2
Message এ attach করা হলো timestamp = 1


এখন message যাচ্ছে P2 এর কাছে



✅ Step 3 – P2 receives message
Current LC2 = 0


Rule: LC2 = max(LC2, received TS) + 1


LC2 = max(0, 1) + 1 = 2


So, P2 জানলো → P1 এর event আগে হয়েছে



✅ Step 4 – Internal Event (P2)
P2 নিজে কিছু event করলো


LC2 = 2 + 1 = 3



👉 Final Timestamps:
P1 event: LC1 = 1


Message send: LC1 = 1


P2 received: LC2 = 2


P2 internal event: LC2 = 3


এখন clear বোঝা যাচ্ছে কে আগে হয়েছে আর কে পরে।

🎯 Key Idea
If LC(a) < LC(b) → a happened before b


If LC(a) = LC(b) → a and b are concurrent (simultaneous but independent)



🔹 Real-Life Analogy (Bangla Example)
ভাবো দুইজন student আছে – তুমি আর তোমার friend।
যখন তুমি notebook এ লিখো, page number ১ বাড়াও।


যখন তুমি message পাঠাও, page number লিখে পাঠাও।


Friend message পেলে দেখে:

 new page = max(own page, received page) + 1


👉 এভাবে দুইজনের লেখা আলাদা notebook এ হলেও event এর order maintain হয়।

📌 তাই Lamport Clock সবসময় বলে দেয় – কে আগে ঘটলো, কে পরে ঘটলো (causal order)।


📌 Scaling in System Design
Scaling মানে হলো – system-কে বেশি load handle করার মতো capable করা।
 এই কাজটা করার দুইটা পদ্ধতি আছে:
Vertical Scaling (Scale Up)


Horizontal Scaling (Scale Out)


🔹 Vertical Scaling (Scale Up)
একটাই server (বা machine)-এ বেশি power যোগ করা।


যেমন: RAM বাড়ানো, faster CPU দেয়া, bigger SSD ব্যবহার করা।


Concept: “Make one machine stronger”


✅ Advantages:
Simple to implement


No code change needed


Consistency easy (single machine)


❌ Disadvantages:
Limited by hardware capacity (একটা server কত RAM/CPU পর্যন্ত নিতে পারবে তার limit আছে)


Expensive hardware লাগে


Single point of failure (যদি এক server down হয় → পুরো system down)


👉 Example:
Small website MySQL database → একটাকে powerful machine-এ চালানো।



🔹 Horizontal Scaling (Scale Out)
একাধিক server যোগ করা এবং load distribute করা।


Concept: “Add more machines instead of making one stronger”


✅ Advantages:
Scalability খুব বেশি (new machine add করলে capacity বাড়বে)


Fault tolerance ভালো (এক server down হলেও অন্য server কাজ চালাতে পারবে)


Cheaper hardware ব্যবহার করা যায়


❌ Disadvantages:
System design complex হয়ে যায় (Load balancer, data replication, consistency manage করতে হয়)


Application কে distributed architecture অনুযায়ী design করতে হয়


👉 Example:
Google, Facebook → millions of servers handle করে horizontally


Cassandra / DynamoDB → horizontally scalable database



📖 Bangla-English Daily Life Analogy
👉 Vertical Scaling (Scale Up)
 একটা rickshaw-তে ৪ জন বসতে পারে। তুমি চাইলে এটাকে truck বানিয়ে ২০ জন বসাতে পারবে। কিন্তু truck-এরও একটা limit আছে (একসময় আর upgrade করা যাবে না)।
👉 Horizontal Scaling (Scale Out)
 একটা truck-এর capacity বাড়ানোর বদলে তুমি আরও truck কিনে ফেলো। তখন যত দরকার তত truck যোগ করা যাবে।

🎯 Quick Comparison Table
Feature
Vertical Scaling (Up)
Horizontal Scaling (Out)
Method
Stronger machine
More machines
Cost
Expensive hardware
Commodity servers
Limit
Hardware সীমিত
Practically unlimited
Complexity
Simple
Complex (distributed)
Failure impact
Single point of failure
More fault tolerant
Example
Add more RAM/CPU
Add more servers (cluster)


👉 Interview-এ answer দিতে পারো এভাবে:
Vertical Scaling = একটাকে powerful করা (limited, simple)


Horizontal Scaling = অনেকগুলো server add করা (scalable, complex)





Redundancy আর Replication এর মধ্যে পার্থক্য


 Redundancy (রিডান্ডেন্সি)
English:
 Redundancy means having extra (backup) components in a system so that if one fails, another can take over. It is about fault tolerance and ensuring system availability.
Bangla:
 Redundancy মানে হলো সিস্টেমে অতিরিক্ত (backup) জিনিস রাখা, যাতে একটি নষ্ট হলেও অন্যটি কাজ চালিয়ে নিতে পারে। এর মূল উদ্দেশ্য হলো system downtime কমানো।
✅ Example (Redundancy):
একটি সার্ভারে দুইটা পাওয়ার সাপ্লাই দেওয়া আছে। যদি একটি নষ্ট হয়, অন্যটি সাথে সাথে কাজ শুরু করবে।


Airline এ multiple engines থাকে। যদি একটা engine fail করে, plane অন্যটা দিয়ে উড়তে পারে।



🔹 Replication (রেপ্লিকেশন)
English:
 Replication means copying the same data/system to multiple locations so that it is available in more than one place. It is mainly for data availability, performance, and reliability.
Bangla:
 Replication মানে হলো একই ডেটা বা সিস্টেমকে একাধিক জায়গায় কপি করে রাখা, যাতে ডেটা সবসময় পাওয়া যায় এবং দ্রুত access করা যায়। এর উদ্দেশ্য হলো data reliability + performance improvement।
✅ Example (Replication):
Facebook এর data অনেক data center-এ copy করা থাকে। Dhaka server down হলেও Singapore server থেকে data পাওয়া যাবে।


A database uses master-slave replication: master database write কাজ করে, আর slave database read কাজ করে।



🔹 Key Differences (মূল পার্থক্য)
Aspect
Redundancy
Replication
Definition
Extra (backup) components to prevent system failure
Copying the same data/system to multiple locations
Purpose
Fault tolerance, high availability
Data reliability, load balancing, performance
Focus
Hardware/Infrastructure backup
Data/Information duplication
Example
Dual power supply in servers
Same database available in multiple servers
Failure Handling
Prevents total system crash
Ensures data is not lost and available everywhere


🔹 Notes (মনে রাখার মতো পয়েন্ট)
Redundancy = Backup Hardware/Component


Replication = Copy of Data/System


Redundancy focuses more on system availability,


Replication focuses more on data availability & performance.


অনেক সময় system-এ দুটো একসাথে ব্যবহার হয় (e.g., Cloud services → both redundancy + replication)।

👉 সহজ করে বললে:
Redundancy = একটা fail করলে backup আছে


Replication = একই data/system অনেক জায়গায় copy আছে
        Load Balancer, এর কাজ, আর Load Balancing Algorithms

 What is Load Balancer?
English:
 A Load Balancer is a device or software that distributes incoming network traffic across multiple servers. Its goal is to ensure no single server gets overloaded, so the system stays fast, reliable, and available.
Bangla:
 Load Balancer হলো এমন একটি সিস্টেম (hardware বা software), যেটা incoming traffic (অনুরোধ) গুলোকে একাধিক server-এর মধ্যে ভাগ করে দেয়। এর ফলে কোনো এক সার্ভার বেশি চাপ (load) পায় না, আর পুরো সিস্টেম smooth ভাবে চলে।

🔹 How Load Balancer Works
English:
A user makes a request (e.g., visiting a website).


The request first goes to the Load Balancer.


The Load Balancer decides which server should handle the request using a specific algorithm.


The server processes the request and sends the response back through the Load Balancer.


Bangla:
User কোনো request করলে (যেমন: ওয়েবসাইটে ঢুকলো)।


Request প্রথমে Load Balancer-এর কাছে যায়।


Load Balancer নির্দিষ্ট algorithm দিয়ে ঠিক করে কোন server এই কাজ করবে।


Server কাজ শেষ করে আবার Load Balancer এর মাধ্যমে response পাঠায়।


✅ Example:
 ধরা যাক তোমার একটা e-commerce সাইট আছে যেখানে ৪টা server আছে। একসাথে ১০,০০০ জন ঢুকলো। Load Balancer সেই traffic কে ৪টা server-এ ভাগ করে দিবে, যাতে কোনো server বেশি চাপ না পায়।

Load Balancer = Server traffic police


Algorithms = Rule কিভাবে request ভাগ হবে।





                             Load Balancing Algorithms

1️⃣ Round Robin
English:
 Distributes requests one by one in order across all servers. After the last server, it starts again from the first.
 Bangla:
 Round Robin হলো সার্ভারের মধ্যে request একের পর এক ভাগ করা। শেষ সার্ভারে গেলে আবার প্রথম সার্ভার থেকে শুরু হয়।
Example:
3টি server: S1, S2, S3


Requests: R1, R2, R3, R4, R5


Distribution:


R1 → S1


R2 → S2


R3 → S3


R4 → S1


R5 → S2


Use Case:
Servers একই ধরনের এবং capacity প্রায় সমান।



2️⃣ Least Connections
English:
 Sends request to the server with the fewest active connections. Useful for servers with different response times.
 Bangla:
 যে সার্ভারে সবচেয়ে কম active connection আছে, নতুন request সেখানে যায়।
Example:
2টি server: S1 (5 active), S2 (2 active)


New request → S2


Next request → whichever has fewer active connections


Use Case:
Servers capacity বা load ভিন্ন হলে।



3️⃣ Weighted Round Robin
English:
 Each server is assigned a weight based on its capacity. Servers with higher weight get more requests.
 Bangla:
 প্রতিটি সার্ভারের একটি weight থাকে। capacity বেশি হলে বেশি request পাবে।
Example:
S1 weight = 3, S2 weight = 1


Requests: 4 requests


Distribution: S1, S1, S1, S2


Use Case:
Servers heterogeneous (ভিন্ন ক্ষমতার) হলে।



4️⃣ IP Hash
English:
 Assigns requests based on client IP address. The same client always goes to the same server.
 Bangla:
 Client এর IP অনুযায়ী request সার্ভারে যায়। একই client সবসময় একই সার্ভারে যাবে।
Example:
Client IP: 192.168.1.10 → Hash → S2


Client IP: 192.168.1.20 → Hash → S1


Use Case:
Session persistence প্রয়োজন হলে (যেমন online shopping)।



5️⃣ Least Response Time
English:
 Sends request to the server with fastest response time and lowest active connections.
 Bangla:
 যে সার্ভারের response time দ্রুত এবং active connections কম, সেখানে request পাঠানো হয়।
Example:
S1 response time = 50ms, 5 active


S2 response time = 30ms, 10 active


New request → S1 (even though S2 has faster CPU, active connections বেশি)


Use Case:
Real-time applications, like video streaming or live games।



6️⃣ Random
English:
 Sends requests to servers randomly, without following any rule.
 Bangla:
 Random ভাবে সার্ভারের মধ্যে request পাঠানো হয়।
Example:
Servers: S1, S2, S3


Requests: R1 → S2, R2 → S1, R3 → S3 (randomly)


Use Case:
Simple, small-scale systems।



🔹 Key Notes
Round Robin → simple, same capacity servers।


Least Connections → dynamic load, servers may have different speed।


Weighted RR → heterogeneous servers।


IP Hash → session persistence।


Least Response Time → performance-critical applications।


Random → simple, no state tracking।



💡 সহজে মনে রাখার ট্রিক:
Round Robin = orderly distribution


Least Connections = lightest server first


Weighted RR = strong server gets more


IP Hash = same client same server


Least Response Time = fastest available server


Random = luck based 😊


Caching:

English:
 Caching is the process of storing frequently accessed data temporarily so that future requests can be served faster.
The cache can be in memory, disk, or browser.


Main goal: Improve performance and reduce latency.


Bangla:
 Caching হলো এমন একটি পদ্ধতি যেখানে প্রায়ই ব্যবহৃত তথ্য সাময়িকভাবে সংরক্ষণ করা হয়, যাতে পরবর্তীতে সেই তথ্য দ্রুত পাওয়া যায়।
Cache হতে পারে RAM, Disk বা Browser।


মূল উদ্দেশ্য: Speed বাড়ানো এবং delay কমানো।



🔹 How Caching Works
User requests data.


System checks if data is in cache.


If yes → fetch from cache (fast)


If no → fetch from main source, then store in cache for next time


Bangla:
User কোনো data চাইলো।


System দেখে data cache-এ আছে কিনা


আছে → cache থেকে পাঠানো (দ্রুত)


নেই → main source থেকে নিয়ে আসে, পরের বার cache-এ রাখা হয়



🔹 Types of Cache
Type
English Explanation
Bangla Explanation
Example
Browser Cache
Stores web page data locally in browser
ব্রাউজারে ওয়েব পেজ সংরক্ষণ
You visit YouTube → next time faster load
Memory Cache (RAM)
Stores data in server memory for quick access
সার্ভারের RAM-এ data রাখা
Redis, Memcached
Disk Cache
Stores data on hard disk
হার্ড ডিস্কে সংরক্ষণ
Browser cache images, OS page cache
Database Cache
Frequently accessed DB queries are cached
DB query ফলাফল cache করা
SELECT query result cached in Redis


🔹🔹 Cache Eviction Techniques
English:
 Cache eviction is the process of removing old or unnecessary data from the cache when it is full so that new data can be stored.
Bangla:
 Cache eviction মানে হলো cache পূর্ণ হলে পুরনো বা অপ্রয়োজনীয় data সরানো, যাতে নতুন data cache-এ রাখা যায়।

1️⃣ LRU (Least Recently Used)
English:
 Removes the data that has not been used for the longest time.
Bangla:
 যে data সবচেয়ে দীর্ঘ সময় ব্যবহার হয়নি, সেটিকে cache থেকে সরানো হয়।
Example:
Cache size = 3, current cache = [A, B, C]


Access order: A → B → C → A → D


Evict → B (least recently used), cache becomes [C, A, D]


Use Case:
Web browser cache, CPU cache



2️⃣ FIFO (First In First Out)
English:
 Removes the oldest data in the cache, i.e., the one that came first.
Bangla:
 যে data cache-এ প্রথমে এসেছে, সেটি প্রথম সরানো হয়।
Example:
Cache size = 3, current cache = [A, B, C]


New data D → Evict A (first in), cache becomes [B, C, D]


Use Case:
Simple caching scenarios, queue-based systems



3️⃣ LFU (Least Frequently Used)
English:
 Removes the data that has been used least frequently.
Bangla:
 যে data কমবার ব্যবহৃত হয়েছে, সেটি cache থেকে সরানো হয়।
Example:
Cache = [A(5), B(2), C(3)] → numbers = usage frequency


New data D → Evict B (least frequency 2), cache = [A, C, D]


Use Case:
Applications where frequency matters, e.g., recommendation systems



4️⃣ Random Replacement
English:
 Removes a randomly chosen data item from the cache.
Bangla:
 Cache থেকে যেকোনো random data সরানো হয়।
Example:
Cache = [A, B, C] → New data D


Evict B randomly → cache = [A, C, D]


Use Case:
Simple or memory-constrained systems



5️⃣ Time-based Eviction (TTL – Time To Live)
English:
 Data is removed from cache after a fixed time period.
Bangla:
 Cache-এ থাকা data নির্দিষ্ট সময় পরে সরানো হয়।
Example:
Cache TTL = 5 mins


Data X added at 10:00 → automatically evicted at 10:05


Use Case:
Session caches, web content caching



🔹 Notes
Eviction needed because cache size is limited


Choice of technique depends on:


Access patterns (recent vs frequent)


Performance requirements


Memory constraints


Often LRU + TTL combination is used in real-world systems



💡 সহজে মনে রাখার উপায়:
LRU = Oldest unused


FIFO = First come, first out


LFU = Rarely used removed


Random = Lucky evict


TTL = Expire after time


🔹 Example
You visit a website → website images, HTML, JS files load → stored in browser cache


Next time you visit → page loads much faster because it fetches from cache, not server


Database example:


Query: SELECT * FROM users WHERE id=1
- First time → fetch from DB (slow)
- Next time → fetch from Redis cache (fast)


🔹 Notes
Cache = Speed Booster


Trade-off: Stale Data Risk → sometimes cached data is outdated


Often used in: Web apps, API calls, databases, OS, CPU



💡 সহজে মনে রাখার উপায়:
 Cache = Short-term storage for faster access













