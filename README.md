# PLARIZA_CS3C_Distributed-Voting-System
![Alt text](https://raw.githubusercontent.com/joyul123/PLARIZA_CS3C_Distributed-Voting-System/8470c14d097ecf1c9aa8dc835a4308451c8d8257/Diagram.svg)
![Alt text](https://github.com/joyul123/PLARIZA_CS3C_Distributed-Voting-System/blob/main/25%20records.png?raw=true)
![Alt text](https://github.com/joyul123/PLARIZA_CS3C_Distributed-Voting-System/blob/main/160%20records.png?raw=true)

REFLECTION

In this Distributed Voting System laboratory activity, I gained valuable hands-on experience in building a distributed application using Supabase and Google Colab. Since Google Cloud Platform was not free, our group decided to use Supabase as the backend platform. I performed the coding, testing, and experimentation using Google Colab.
The most interesting part for me was running multiple edge nodes simultaneously. I executed the edge_node.py script across several terminals and different Google Colab notebooks. It was fascinating to observe how each node generated votes independently at different speeds and intervals. This experience gave me a real understanding of the asynchronous and unpredictable nature of distributed systems.
At the beginning, I encountered network timeout issues while sending votes from the edge nodes. After implementing retry logic in the Python script, the system became much more stable and resilient to temporary connection failures.
I developed a Supabase Edge Function that served as the ingestion API. It successfully received votes from all edge nodes and stored them in the database using upsert operations based on user_id and poll_id. This ensured idempotency — even when I intentionally sent duplicate votes during fault injection testing, no duplicate records were created.
One of the most insightful moments was when I simulated failure by temporarily disabling the Edge Function. While it was disabled, the edge nodes continued retrying to send votes. Once I redeployed the function, all pending votes were processed successfully. This clearly demonstrated the concept of eventual consistency in practice.
Using Supabase together with Google Colab made the entire development process fast and convenient. Although it offered less visibility into message queuing compared to a full Pub/Sub system, Supabase’s real-time capabilities allowed me to see vote results updating instantly in the database, which was very satisfying.
Overall, this laboratory activity significantly improved my understanding of key distributed system concepts such as fault tolerance, idempotency, edge-to-cloud communication, and system recovery. Coding the full system in Google Colab while integrating it with Supabase gave me strong practical confidence in developing resilient distributed applications.
I believe the skills and insights I gained from this project will be highly useful for my future work in real-time and distributed systems.
