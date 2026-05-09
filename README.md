# PLARIZA_CS3C_Distributed-Voting-System
![Alt text](https://raw.githubusercontent.com/joyul123/PLARIZA_CS3C_Distributed-Voting-System/8470c14d097ecf1c9aa8dc835a4308451c8d8257/Diagram.svg)
![Alt text](https://github.com/joyul123/PLARIZA_CS3C_Distributed-Voting-System/blob/main/25%20records.png?raw=true)
![Alt text](https://github.com/joyul123/PLARIZA_CS3C_Distributed-Voting-System/blob/main/160%20records.png?raw=true)

REFLECTION

In this Distributed Voting System laboratory activity, I gained valuable hands-on experience in building a distributed application using Supabase and Google Colab. Since Google Cloud Platform was not free, I used Supabase as the backend platform, and PostgreSQL as an alternative, and it worked very effectively, and performed all the coding and testing using Google Colab.
The most interesting part for me was running multiple edge nodes simultaneously. I executed the edge_node.py script in several terminals (and also ran them in different Colab notebooks), and it was fascinating to observe how each node generated votes independently at varying speeds and intervals. This gave me a clear understanding of the asynchronous and unpredictable behavior of real distributed systems.
At the beginning, I faced some network timeout issues while sending votes from the edge nodes. After implementing retry logic in the Python script, the system became significantly more stable and resilient to temporary connection problems.
I developed a Supabase Edge Function that acted as the main ingestion API. It successfully received votes from all edge nodes and stored them in the database using upsert operations based on user_id and poll_id. This ensured idempotency — even when I intentionally sent duplicate votes during fault injection, no duplicate records were created.
One of the most insightful experiences was simulating system failure by temporarily disabling the Edge Function. During this period, the edge nodes kept retrying to send votes, and once I redeployed the function, all pending votes were processed successfully. This effectively demonstrated the concept of eventual consistency in a distributed environment.
Using Supabase together with Google Colab made the development process much faster and more convenient. While it provided less visibility into message queuing compared to a full Pub/Sub system, Supabase’s real-time capabilities allowed me to instantly see vote results updating in the database, which was very satisfying.
Overall, this laboratory activity greatly enhanced my understanding of key distributed system concepts such as fault tolerance, idempotency, edge-to-cloud communication, and system recovery. Coding everything in Google Colab while integrating with Supabase gave me practical confidence in developing resilient distributed applications.
I believe the skills and knowledge I gained from this project will be highly useful for my future work in real-time systems and distributed architectures.
