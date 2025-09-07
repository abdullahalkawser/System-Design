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










