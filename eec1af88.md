---
date: 2021-02-10T20:38
tags: 
  - research-paper
  - database
---

# Dynamo: Amazon's highly available key value store

[paper](file:///Users/sudeepkumar/Downloads/dynamo-amazons-highly-available-key-value-store.pdf)

## intro
amazon.com runs on top of thousands of servers and other network components. Some inevitably fail. A highly-available persistence store is needed to give an "always on" experience. This is done by sacrificing consistency on some occasions [what was that theorem again?]


Q: what are the things needed to be highly available? - replication, versioning, query latency

simple scheme: key-value store: what role does this play in how they construct entire solution. For example, how does this help them solve the versioning problem. Would it have effected them if they opted for a more general schema solution?
    
## internal design

![dynamo db techniques](static/dynamodb_techniques.png)

### data partition: consistent hashing
### consistency: object versioning
### consistency among replicas: quorum-like technique and a decentralized replica synchronization protocol.
### gossip based failure detection and membership protoc


## conclusion
highly scalable; can scale up and down as required; can tweak consistency, performance and durability (??) by tweaking some parameters.
claim: It's success (in the demanding env of amazon.com) shows that an eventual consistent storage system can be a building block for highly-available applications.

---
