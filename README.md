# Towards more reactive microservices

## Main Idea
In order for us to facilitate and secure the loan granting process in the banking system, we agreed on the following use cases to develop:

- A client of the bank prepares his papers, scans them and send them to the bank in a trial to secure a loan.
- The commercial service sees the latter's documents, deducts its own audit and usual procedures to see if the client is eligible for the loan then send it to the risk management service.
- After the risk management receives the decision of commercial service, it has the final say about whether the client is eligible of a loan or not.
- The client recives the final decision from the risk management service in a secure way.

## Technologies
<img align="left" width="200" height="100" src="https://res.cloudinary.com/practicaldev/image/fetch/s--m_Ng9MLF--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/i/fppjegg7q1kb2pdzmlvf.png">

<img align="left" width="100" height="100" src="https://user-images.githubusercontent.com/62222721/171054797-193dd2c8-169c-4f61-87b4-745da8f11e45.png">

<img width="200" height="100" src="https://upload.wikimedia.org/wikipedia/fr/thumb/6/62/MySQL.svg/langfr-1920px-MySQL.svg.png">

## What's Redis?

Redis is an open source, in-memory data structure store used as a database, cache, message broker, and streaming engine. Redis provides data structures such as strings, hashes, lists, sets, sorted sets with range queries, bitmaps, hyperloglogs, geospatial indexes, and streams. Redis has built-in replication, Lua scripting, LRU eviction, transactions, and different levels of on-disk persistence, and provides high availability via Redis Sentinel and automatic partitioning with Redis Cluster.

## Architecture
![Copy of architecture-design for tp banking system(3)](https://www.canva.com/design/DAFCQlmMKKU/WwJ3FXsWMBKspFsQUlNT-g/view?utm_content=DAFCQlmMKKU&utm_campaign=share_your_design&utm_medium=link&utm_source=shareyourdesignpanel)

1) The client scans his documents and sends them through the Broker.
2) The commercial service reads through the documents and decides on the eligibility of the client.
3) The commercial service send its notifications to the risk management.
4) The risk management receives the commercial service inial decision securily.
5) After Deducting to a final decision, the risk management sends to the broker its final decision.
6) The client receives a YES or NO answer to his loan request.


**Client**
- Sends the request about a loan from the bank.
- Receives at the end of the treatment an answer to his request.

**Commercial Service**
- Deducts a final decision after a thourough investigation on the financial state of the client.
- Notifies the risk management.

**Risk Management**
- Receives the commercial service notification.
- Runs its own investigation.
- Deducts to a final decision.
- Notifies the client about that final decision.
