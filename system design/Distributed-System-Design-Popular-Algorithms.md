[TOC]
# 1\. Consistence Hashing

Consistent hashing is a hashing technique that minimizes the need for remapping when a hash table is resized . In traditional hash tables, a change in the number of array slots causes nearly all keys to be remapped. However, consistent hashing uses a special kind of hashing technique such that only keys need to be remapped on average, where “n” is the number of keys and “m” is the number of slots. This technique is particularly useful in load balancing, where a standard hash function can be used to calculate the hash value for a blob, and then the resultant value of the hash is used with modular operations to determine the specific server where the blob will be placed. This technique is used in various data storage and distribution systems, including OpenStack’s Object Storage Service Swift, Amazon’s storage system Dynamo, and Akamai content delivery network.

Consistent hashing is widely used in distributed system design for several use cases, including but not limited to:

- Load balancing: Consistent hashing allows for easy distribution of load across multiple servers. When a new server is added to the cluster or an existing server is removed, only a small subset of keys need to be remapped to the new or remaining servers, minimizing the impact of the change on the overall system.
    
- Caching: Consistent hashing is used to determine which cache node should store a particular key-value pair. This can help reduce the number of cache misses, improving the overall performance of the system.
    
- Content delivery: Consistent hashing is used to map content to edge servers in a content delivery network (CDN). This helps ensure that content is served from the server closest to the user, reducing latency and improving the user experience.
    
- Database sharding: Consistent hashing is also used to shard data across multiple database servers, allowing for efficient distribution of data and improved performance. In this case, each shard is allocated to a particular server based on its hash value.
    

<img src="../_resources/871bf25972726ca7f33d3f126d902567.png" alt="871bf25972726ca7f33d3f126d902567.png" width="315" height="216" class="jop-noMdConv"><img src="../_resources/e6388343cf1a5b74f0cce23a95458a4a.png" alt="e6388343cf1a5b74f0cce23a95458a4a.png" width="528" height="220" class="jop-noMdConv">

# 2\. Bloom Filters

A Bloom filter is a probabilistic data structure that is used to test whether an element is a member of a set or not 1. It works by hashing elements and setting the corresponding bits in an array of bits. When testing if an element is in the set, the Bloom filter hashes the element and checks if all of the corresponding bits in the array are set. If any of the bits are not set, then the element is not in the set. However, if all of the bits are set, the element may or may not be in the set, as there could have been a collision with another element that set the same bits.

Bloom filters have a high space efficiency as they require relatively small amounts of memory compared to other data structures, such as hash tables or binary search trees. They are also very fast in terms of insertion and search time, with constant time complexity. However, they have a trade-off in terms of the number of false positives, which is the probability that a Bloom filter will incorrectly identify an element as being in the set when it is not. The probability of false positives can be controlled by adjusting the size of the Bloom filter and the number of hash functions used.

Bloom filters are commonly used in various applications, including:

- Spell checkers: Bloom filters can be used to quickly check if a word is in a dictionary, reducing the need to search through the entire dictionary word by word.
    
- Network routers and firewalls: Bloom filters can be used to store information about the network traffic, such as the IP addresses of known malware or spam sources, and quickly identify if incoming traffic is from a known source.
    
- Databases and search engines: Bloom filters can be used to pre-filter candidate records or documents to avoid expensive disk access and CPU processing.
    
- Web browsers: Bloom filters can be used to store information about visited URLs for fast phishing and malware detection.
    

<img src="../_resources/5289cb7f769adc93ad049c446df31ddc.png" alt="5289cb7f769adc93ad049c446df31ddc.png" width="518" height="186" class="jop-noMdConv"><img src="../_resources/af01113a95bbf8b7c39f73735cc082d9.png" alt="af01113a95bbf8b7c39f73735cc082d9.png" width="457" height="257" class="jop-noMdConv">

# 3\. Skip Lists

Skip lists are a type of probabilistic data structure, similar to a multilevel linked list, that can efficiently search, insert, and delete elements in a sorted sequence. They are designed to have an average search, insertion, and deletion time complexity of O(log n), making them a suitable alternative to balanced trees in some cases.

Skip lists allow for efficient searching by adding multiple levels of links between nodes, with the lower levels acting as shortcuts to higher levels. The linking between levels is done randomly, so that each element has a probability of appearing at each level, with higher levels having progressively smaller probabilities. This randomness helps ensure that the skip list stays balanced on average, even as elements are added or removed.

Skip lists are used in a variety of applications, including databases, game programming, and network routing. They are particularly well-suited for applications that require fast search times and frequent insertions, and may be a better choice than balanced trees in situations where the cost of rebalancing becomes prohibitive. However, because they rely on randomness, their performance can be difficult to predict precisely, and they may not be as suitable for applications that require very tight control over performance characteristics.

![dd6f585a307a1d0934c625f2081ba3ee.png](../_resources/dd6f585a307a1d0934c625f2081ba3ee.png)

# 4\. B-Tree

A B-tree is a self-balancing tree data structure that maintains sorted data and allows efficient search, insertion, and deletion operations in logarithmic time. Unlike other self-balancing binary search trees, B-trees have the ability to deal with much larger data sets and are commonly used in storage systems such as databases and file systems. They generalize binary search trees by allowing nodes to have more than two children and have a fixed maximum size, referred to as the order, which determines the number of keys that can be stored in each node.

In a B-tree, internal nodes can have a variable number of child nodes within an ordered range, with each node storing keys and pointers to other nodes. The keys within a node are ordered, and the pointers are used to navigate between nodes during search operations. At the leaf level, actual data is stored in sorted order.

B-trees are designed to maintain balance, which ensures efficient search operations, and they achieve this through a process of node splitting and merging. When a new key is inserted, or a key is removed, the B-tree is rebalanced so that the number of levels in the tree remains relatively constant.

B-trees have logarithmic time complexity for search, insertion, and deletion operations, which makes them a popular choice for applications that require quick access to large data sets. They are also used extensively in modern database systems to provide fast indexing and querying capabilities.

![d82895815b18afbe11ae5a496d2a094c.png](../_resources/d82895815b18afbe11ae5a496d2a094c.png)

A B+ tree is an extended version of a B-tree, where each non-leaf node contains a fixed number(m) of pointers to child nodes(m-ways). The B+ tree has better performance compared to binary search trees and B-trees when searching and inserting data. The B+ tree is often used in databases and file systems where the data is stored in external storage. In a B+ tree, all the data is stored in the leaf node, whereas the internal nodes only store index keys. The leaf nodes are linked, and a sequential access can be made along the leaf nodes. Because of its many pointers, the B+ tree has good space utilization, as well as good performance for range queries. It is also self-balancing to ensure that the time complexity for searching, insertion, and deletion is logarithmic in most cases.

<img src="../_resources/01752144d4c30ba10bb3e873de422b0f.png" alt="01752144d4c30ba10bb3e873de422b0f.png" width="567" height="290" class="jop-noMdConv"> <img src="../_resources/7e2aac86ed81319e50295803b7f50a31.png" alt="7e2aac86ed81319e50295803b7f50a31.png" width="896" height="370" class="jop-noMdConv">

# 5\. LRU and LFU

In a typical LRU implementation, you maintain a map of key-value pairs and a linked list of keys in the order of their access. Whenever an item is accessed, you move its corresponding key to the head of the list. If you need to evict an item due to capacity constraints, you simply remove the least recently accessed item from the tail of the list.

<img src="../_resources/c42b2b468fcae8f96a49564d5b1391e8.png" alt="c42b2b468fcae8f96a49564d5b1391e8.png" width="796" height="323" class="jop-noMdConv">

LFU eviction policy can be implemented using a combination of a hash map and a priority queue. In this implementation, you maintain a hash map of key-value pairs and a priority queue of entries ordered by the least frequency of usage. Whenever an entry is accessed, you increment its usage count and update its position in the priority queue. If you need to evict an item due to capacity constraints, you simply remove the least frequently used item from the head of the priority queue

<img src="../_resources/7b3b0a60534c65d335c403fb3324f145.png" alt="7b3b0a60534c65d335c403fb3324f145.png" width="715" height="460" class="jop-noMdConv">

The choice between LRU and LFU eviction policies depends on the specific use case and access patterns of the cache. LRU is typically a good choice when you have a large cache with high locality of reference, i.e., the most recently accessed items are likely to be accessed again in the near future. LFU is a good choice when you have a small cache with many frequently accessed items that you want to keep in memory at all times. However, there are many variations of both eviction policies, and other policies such as LRU-K and Adaptive Replacement Cache (ARC) that combine the benefits of both LRU and LFU policies.

# 6\. Reverse index

A reverse key index is a type of index found in database management systems where the key value is reversed before entering it into the index. For example, the value 24538 becomes 83542 in the index . This technique is particularly useful when indexing data such as sequence numbers where each new key value is greater than the prior value. Reversing the key value reduces contention for index blocks and has become particularly important in high volume transaction processing systems. While this technique is not applicable to all types of data, it can significantly improve performance for certain use cases.

Reverse indexes can be used in distributed systems to improve performance by minimizing contention for index blocks. In a high-volume transaction processing system, there can be a large number of index blocks being written to or read from simultaneously, leading to contention for these resources. By reversing the key value before entering it into the index, the distribution of index blocks can be more evenly spread out, reducing contention and improving performance. Additionally, reverse indexes can be used for fast lookups in a wide range of data structures, including inverted indexes used for information retrieval systems, document stores, and full-text search engines.

A reverse index simply stores the values for the index in reverse order. A value such as `123` would be stored as `321` in a reverse index. Oracle shifts the order of the value transparently, so that a user in the previous example would input the value `123` and have the same value returned in a query. When a reverse index is used, the natural tendency of the index toward an unbalanced state is prevented, because consecutive values are distributed through the B*-tree index structure. The following SlideShow illustrates the problem and the solution delivered by reverse indexes:

![8ea6256c6e7653201d62c7ff3f77424a.png](../_resources/8ea6256c6e7653201d62c7ff3f77424a.png)

# 7\. Inverted index

An inverted index is a database index that stores a mapping from content, such as words or numbers, to its locations in a table, document, or set of documents. The purpose of an inverted index is to allow for fast full-text searches, but it comes at the cost of increased processing when a document is added to the database. This data structure is a central component of a typical search engine indexing algorithm and is used on a large scale in search engines, document retrieval systems, and full-text search engines. There are two main variants of inverted indexes: record-level and word-level, with the latter offering more functionality such as phrase searches, but requiring more processing power and space to be created. Additionally, compression techniques are often used to reduce the amount of storage required for an inverted index.

![d89922ef37db7dc54b99d65df65ccafc.png](../_resources/d89922ef37db7dc54b99d65df65ccafc.png)

# 8\. Trie algorithm

The trie algorithm, also known as a prefix tree, is a tree-based data structure used for storing and searching associative arrays or sets of strings . Unlike a binary search tree, nodes in a trie do not directly store the values associated with their keys. Rather, each node represents a character in a string key and has links to child nodes representing subsequent characters, with the entire string key being stored at the position in the tree defined by the path taken to reach its final character node. This allows for fast searching and retrieval of values based on their associated keys, as well as a variety of string-related operations such as prefix matching and auto-completion. In distributed systems, tries can be partitioned or replicated across multiple machines to improve performance and fault tolerance, with care taken to maintain data consistency and handle updates. Trie algorithms have numerous practical applications, including in information retrieval, spell checking, and networking protocols.

In distributed systems, tries can be partitioned or replicated across multiple machines to improve performance and fault tolerance. Partitioning involves dividing the trie into smaller sub-tries, with each sub-trie being stored on a separate machine. Queries can then be sent to these machines in parallel, with the results aggregated at the client-side. Replication, on the other hand, involves replicating the trie across multiple machines using distributed hash table (DHT) or peer-to-peer protocols. This ensures that each machine has a consistent copy of the data.

A hybrid approach can also be used where some parts of the trie are partitioned while others are replicated. This can help balance the load across the machines while also ensuring consistency and fault tolerance. However, maintaining data consistency and handling updates can be challenging in a distributed setting. Techniques such as versioning, conflict resolution, and distributed locking can be used to address these issues.

Trie algorithms have numerous practical applications in distributed systems, including in information retrieval, spell checking, and networking protocols. By partitioning or replicating the data structure across multiple machines, performance can be improved while maintaining data consistency and availability.

<img src="../_resources/8b663b6fe170c276907925537d81e710.png" alt="8b663b6fe170c276907925537d81e710.png" width="536" height="509" class="jop-noMdConv">

# 9\. Rsync algorithm

The rsync algorithm is a type of delta encoding used for minimizing network usage when transferring and synchronizing files between computers . It works by comparing the modification times and sizes of files on the source and destination systems, and only transferring the differences (or “deltas”) between them. This reduces the amount of data that needs to be transmitted over the network, making the transfer faster and reducing network congestion. Additionally, zlib may be used to add data compression, and SSH or stunnel can be used for security. Rsync is typically used for synchronizing files and directories between two different systems, and is written in C as a single-threaded application.

<img src="../_resources/db4bbab61f1ed4f40fcf5abe36aa7295.png" alt="db4bbab61f1ed4f40fcf5abe36aa7295.png" width="280" height="283" class="jop-noMdConv">

# 10\. Merkle tree

A Merkle tree is a tree data structure used in cryptography and computer science applications for efficient and secure verification of data integrity. In a Merkle tree, each leaf node is labeled with the cryptographic hash of a data block, and each non-leaf node is labeled with the cryptographic hash of the labels of its child nodes. This allows for verifying the contents of a large data structure using only a small subset of the hash values, making it efficient and highly secure. In distributed systems, Merkle trees are used for efficient and secure data verification across multiple nodes or peers. By creating and distributing Merkle trees among nodes, they can easily verify that the same data is available on all nodes and detect any changes, making it useful for applications such as blockchain, P2P networks, and file sharing. Merkle trees are a type of cryptographic commitment scheme, and the root of the tree serves as the commitment to the entire data structure.

<img src="../_resources/401a91064fe9aed4433a405d3fd02c7a.png" alt="401a91064fe9aed4433a405d3fd02c7a.png" width="500" height="318" class="jop-noMdConv">

# 11\. Leaky bucket / Token bucket

The leaky bucket and token bucket algorithms are two different approaches to traffic shaping and rate limiting in computer networks.

The leaky bucket algorithm enforces a steady output rate by allowing input traffic to enter a bucket at a variable rate , but the bucket has a fixed capacity. When the bucket overflows, excess traffic is discarded. The average output rate is controlled by the rate at which the bucket leaks.

<img src="../_resources/d879f2f13f59810586add51f894640f4.png" alt="d879f2f13f59810586add51f894640f4.png" width="365" height="337" class="jop-noMdConv"> <img src="../_resources/db15c6d233d8bf78ce9849017208c45a.png" alt="db15c6d233d8bf78ce9849017208c45a.png" width="356" height="250" class="jop-noMdConv">

The token bucket algorithm also controls traffic based on a fixed output rate, but instead of using a bucket to control the input, it uses tokens. A token bucket is initially filled with a fixed number of tokens, and when a packet arrives, a token is removed from the bucket to allow it to be transmitted. If there are no tokens in the bucket, packets are queued or discarded.

![e455c2766ccfec540e46e254955f1935.png](../_resources/e455c2766ccfec540e46e254955f1935.png)

Both algorithms can be used to smooth out traffic and prevent network congestion by enforcing a maximum rate of traffic. They are often used in combination with other techniques such as Quality of Service (QoS) and traffic classification to control network traffic and prioritize certain types of traffic over others.

# 12\. Geohash

Geohash is a geocode system invented in 2008 by Gustavo Niemeyer that encodes a geographic location into a short string of letters and digits . The encoding represents a rectangular bounding box that contains the location and is recursively subdivided into smaller and smaller cells, each identified by a unique geohash code. The more characters included in the geohash, the more precisely it defines the location. Geohashes are used in applications that require location-based searches, such as mapping and location-based services. They are also used for indexing and querying geospatial data in databases and search engines.

<img src="../_resources/689850fed73db07eb262e5cca8595d5f.png" alt="689850fed73db07eb262e5cca8595d5f.png" width="564" height="315" class="jop-noMdConv"> <img src="../_resources/1dcd8a0c3205e1b0a35f28d74c1f7ea2.png" alt="1dcd8a0c3205e1b0a35f28d74c1f7ea2.png" width="538" height="355" class="jop-noMdConv">

# 13\. Quadtree

A quadtree is a tree data structure used in computer graphics , geographic information systems (GIS), and other applications that require efficient spatial indexing and querying of 2D or 3D points, rectangles or other geometric primitives. A quadtree recursively subdivides a 2D or 3D space into four equally sized quadrants or regions, each represented by a quadtree node. Each node can be further subdivided until a leaf node is reached. The leaf node contains the actual data or objects that are being indexed and queried. The quadtree provides a fast and efficient way of searching for points or objects within a rectangular area or for nearest neighbors. It is commonly used in GIS for indexing maps, as well as in computer graphics for collision detection, frustum culling, and other spatial operations. The quadtree is a special case of a recursive partitioning tree, where each internal node is divided into a fixed number of subregions or children.

Quadtrees are trees used to efficiently store data of points on a two-dimensional space. In this tree, each node has at most four children. We can construct a quadtree from a two-dimensional area using the following steps:

- Divide the current two dimensional space into four boxes.
- If a box contains one or more points in it, create a child object, storing in it the two dimensional space of the box
- If a box does not contain any points, do not create a child for it
- Recurse for each of the children.

<img src="../_resources/7b94058f7390cbec0921da162010e56c.png" alt="7b94058f7390cbec0921da162010e56c.png" width="813" height="403" class="jop-noMdConv">

There are some differences to consider when choosing between using a geohash or a quadtree for spatial indexing and searching:

1.  Precision: Geohashes provide variable precision by adjusting the length of the hash string, while a quadtree subdivides the space into fixed-sized cells. Thus, geohashes are more flexible in terms of precision but may result in more computational overheads.
    
2.  Indexing Performance: Quadtree is the more efficient structure in terms of indexing performance, as it guarantees that each cell in the space is covered by at most one node. This property directly translates to faster traversal times and lower memory usage, resulting in faster indexing of spatial data.
    
3.  Search Performance: Geohash is faster for point search as each cell is represented by a unique hash value. This means that, in principle, the search query only needs to match against the hash values to identify relevant nodes. On the other hand, quadtree may be more efficient for range search as it allows for direct traversal of relevant cells. Overall, the choice between geohash and quadtree is dependent on the use case and the specific spatial requirements of the application.
    

# 14\. Leader election

In distributed computing, leader election is the process of designating a single process as the coordinator of a task distributed among several computers or nodes . The goal of leader election is to break the symmetry among nodes and select a unique leader node that will organize and coordinate the task. Leader election algorithms are designed to be efficient and economical in terms of message passing and computation. There are several strategies for leader election, including comparisons of unique and comparable identities, randomized leader election, and the use of secret sharing or quorum systems. Leader election is a fundamental problem in distributed computing and has applications in various fields, including cloud computing, blockchain, and distributed databases.

There are several algorithms that can be employed to select a leader in such systems, and I shall mention a few:

- Bully Algorithm: In this algorithm, a process with the highest priority (usually determined by process ID) becomes the leader. When a process detects the absence of a leader, it initiates an election by sending an “Election” message to processes with higher priority. If it receives no response, it declares itself the leader and sends a “Victory” message to all lower-priority processes.
    
- Ring Algorithm: In this approach, processes are arranged in a logical ring. When a process detects the absence of a leader, it initiates an election by sending an “Election” message containing its process ID to its neighbor in the ring. Each process forwards the message, updating the process ID if it encounters a higher one. When the message returns to the initiator, the process with the highest ID is declared the leader.
    
- Paxos Algorithm: This algorithm is based on a consensus protocol that ensures agreement among processes in the presence of failures. It involves three roles: proposers, acceptors, and learners. Proposers suggest new leader values, acceptors vote on these values, and learners learn the chosen value. The algorithm guarantees that only one value is chosen, and that value is the new leader.
    
- Raft Algorithm: Raft is a consensus algorithm designed to be more understandable than Paxos. It divides time into terms, and each term has a leader. The leader is responsible for managing the replicated log and ensuring consistency. If a leader fails, a new election is held, and a new leader is chosen for the next term.
    

![8d00dbf5abf609798e7deb9d2f918e9e.png](../_resources/8d00dbf5abf609798e7deb9d2f918e9e.png)

# 15. Consensus (Raft/Paxos)

Both Raft and Paxos are leader election algorithms used in distributed computing to elect a single process as the leader or coordinator of a task distributed among several nodes. The leader is responsible for the organization and coordination of the task, thus making it a fundamental problem in distributed computing.

Paxos is a family of consensus algorithms that guarantee the consistency of replicated state machines in a distributed system. The algorithm uses a proposal and acceptance mechanism to ensure that only one value or operation can be chosen as the final agreed-upon value. Paxos is designed to tolerate up to a third of the nodes failing or behaving maliciously.

![9f39096913873d9b68060cd7f7438532.png](../_resources/9f39096913873d9b68060cd7f7438532.png)

Raft, on the other hand, is an alternative consensus algorithm to Paxos. It was designed to be simpler and more understandable than Paxos. Raft works by electing a leader among the nodes, which is responsible for managing the replicated state machine. Unlike Paxos, Raft uses a heartbeat mechanism to allow nodes to detect a failed leader and elect a new one.

<img src="../_resources/103e008491a32ad7299483a1278fc817.png" alt="103e008491a32ad7299483a1278fc817.png" width="540" height="284" class="jop-noMdConv">

Overall, both Paxos and Raft provide fault-tolerance and performance guarantees for consensus-based distributed systems, but Raft is considered to be more understandable and easier to implement than Paxos.

<img src="../_resources/7007caf9598bbb0ba69e4feac7729245.png" alt="7007caf9598bbb0ba69e4feac7729245.png" width="849" height="331" class="jop-noMdConv">

# 16\. Time synchronization

Time synchronization is the process of ensuring that the clock on one device is aligned with the clock on another device . This is essential in computing and networking systems where multiple devices may need to coordinate their activities. The clock on each device must be periodically reset with the correct time to ensure that all devices are in sync. Techniques like Network Time Protocol (NTP) are commonly used for this purpose. Time synchronization is also important in other fields, such as financial services and scientific research, where accurate timekeeping is critical for accurate record-keeping and analysis.

There are several algorithms used for time synchronization in distributed systems, including:

- Network Time Protocol (NTP): NTP is a widely used protocol for clock synchronization in computer networks . It is designed to synchronize time across a network of computers by exchanging time-stamped packets between them.
    
- Berkeley Algorithm: The Berkeley Algorithm is a clock synchronization algorithm used in distributed systems. It assumes that each machine node in the network either has a clock of its own or is connected to a clock source . The algorithm synchronizes the clocks in the network by using the average time of all the clocks in the network.
    
- Cristian’s Algorithm: Cristian’s Algorithm is a simple algorithm for clock synchronization in distributed systems. It involves sending time requests from the client to the server and calculating the offset between the server’s time and the client’s time.
    
- Precision Time Protocol (PTP): PTP is a protocol for clock synchronization that is designed to achieve high precision even in large, complex networks. It uses hardware timestamps to achieve high accuracy and precision.
    

<img src="../_resources/89f34d59f4714e26e6182d885d9bdbf6.png" alt="89f34d59f4714e26e6182d885d9bdbf6.png" width="606" height="281" class="jop-noMdConv">

# 17\. Erasure coding

Erasure coding, also known as forward error correction, is a data protection method used in distributed storage systems. In erasure coding, data is broken down into fragments and redundant pieces of data are added to create encoded fragments. By using this method, the original data can be reconstructed from only a subset of the encoded fragments. Erasure coding is different from traditional data protection methods, such as RAID, which require full copies of data to be stored on multiple disks. Erasure coding can provide higher storage efficiency and better fault tolerance in distributed storage systems. There are several erasure coding algorithms, including Reed-Solomon and Cauchy-Reed-Solomon codes, which are commonly used in distributed storage systems like Hadoop and Ceph.

<img src="../_resources/e3b32699b4a078b765b06ae5791eb665.png" alt="e3b32699b4a078b765b06ae5791eb665.png" width="670" height="424" class="jop-noMdConv">

# 18\. Message digest algorithms

A message digest algorithm, also known as a hash function, is a procedure that maps input data of an arbitrary length to an output of fixed length . This output is often referred to as a message digest or cryptographic hash. Message digest algorithms are commonly used in information security to ensure data integrity, provide non-repudiation, and enable secure communication channels.

Some examples of message digest algorithms include the MD5 and SHA-1 algorithms, which were widely used in the past but have been found to have vulnerabilities. More recent hash algorithms, such as the SHA-2 and SHA-3 families, are considered more secure and are recommended for use in new applications.

Overall, message digest algorithms are an important tool for information security and data protection, and it is important to use secure and modern algorithms to ensure the safety and integrity of data.

There are several widely used message digest algorithms, including:

- MD5: MD5 is a 128-bit hash algorithm that was widely used in the past but has been found to have vulnerabilities.
    
- SHA-1: SHA-1 is a 160-bit hash algorithm that was widely used in the past but has also been found to have vulnerabilities.
    
- SHA-2: SHA-2 is a family of hash algorithms that includes SHA-224, SHA-256, SHA-384, and SHA-512. These algorithms are still considered secure and are commonly used today.
    
- SHA-3: SHA-3 is a family of hash algorithms that was selected in a public competition held by the National Institute of Standards and Technology (NIST) in 2012. It is considered to be very secure.
    

# 19\. Atomic commit

In a distributed system, ensuring consistency and durability of transactions across multiple nodes is a critical task. The atomic commit protocol is a technique used in distributed computing to ensure that a transaction is either committed or rolled back in its entirety across all nodes of the distributed system . In other words, atomic commit involves making sure that all participating nodes either fully commit or fully cancel the transaction, leaving the system in a consistent state.

The two-phase commit protocol (2PC) is a commonly used atomic commit protocol. In 2PC, a coordinator node initiates the transaction and communicates with all participating nodes to ensure that they are ready to commit. In the first phase of the protocol, the coordinator sends a prepare request to all participants, asking them to prepare for the transaction by making sure they have all necessary resources. If all participants are ready, they respond with a prepared message. If any participant is not ready, they respond with a fail message. In the second phase, the coordinator sends a commit message to all participants if all prepared. If the coordinator node receives acknowledgements from all nodes, it sends the commit message to complete the transaction. If any of the nodes responds with a fail message, the coordinator sends an abort message to all participants, undoing the transaction.

<img src="../_resources/c5b9eba7201997095270a936885605a8.png" alt="c5b9eba7201997095270a936885605a8.png" width="585" height="438" class="jop-noMdConv">

Other atomic commit protocols include the three-phase commit protocol (3PC) and the Paxos protocol. These protocols have variations of the 2PC approach but with additional steps, in order to improve the availability of the system and minimize transaction blocking time.

# 20\. Mutual exclusion

Mutual exclusion is a property of concurrency control , which aims to prevent race conditions between multiple threads of execution in a computer system. It requires that one thread of execution does not enter a critical section while another thread is already accessing the same critical section, to ensure that the system remains in a consistent state. This is often implemented using locks or other synchronization mechanisms to regulate access to critical sections. Mutual exclusion is an important concept in computer science and plays a vital role in ensuring thread safety and preventing data corruption in concurrent systems.

<img src="../_resources/b3e94c193384c98b7bec7d53b7944343.png" alt="b3e94c193384c98b7bec7d53b7944343.png" width="299" height="354" class="jop-noMdConv">

# 21\. Global state collection

In the realm of distributed systems, global state collection is a technique used to gather information about the overall state of the system at a given point in time.

A distributed system consists of multiple processes or nodes that communicate with each other to perform tasks. Each process maintains its local state, which includes information about its current status, data, and any ongoing computations. The global state of the system is a combination of the local states of all processes, along with the state of communication channels between them.

Collecting the global state can be challenging due to the asynchronous nature of distributed systems, where processes may be executing concurrently and messages may be delayed or lost. One approach to address this issue is the use of snapshot algorithms, such as the Chandy-Lamport algorithm.

The Chandy-Lamport algorithm works as follows:

1.  A designated process initiates the snapshot by recording its local state and marking its incoming channels as empty.
2.  The initiating process sends a “snapshot” message to all its neighboring processes through its outgoing channels.
3.  Upon receiving the “snapshot” message, a process records its local state if it has not done so already. It then marks the incoming channel from which it received the message as empty and forwards the “snapshot” message to its neighbors.
4.  Each process continues to record the state of its incoming channels, capturing any messages received after recording its local state but before receiving the “snapshot” message on that channel.

Once the algorithm is complete, the collected local states and channel states can be combined to form a consistent global state of the distributed system. This global state can be used for various purposes, such as debugging, monitoring, and recovery.

<img src="../_resources/32aa21551b994ba93ad5069dc346fb66.png" alt="32aa21551b994ba93ad5069dc346fb66.png" width="285" height="340" class="jop-noMdConv">

# 22\. Gossip

In distributed computing, a gossip protocol is a type of communication protocol that allows state sharing in a distributed system 1. It is based on the way epidemics spread, where each node in the system randomly selects a few other nodes to share information with, and those nodes in turn share with others, eventually disseminating the information to all nodes in the system. Gossip protocols are often used for tasks such as dissemination of data, failure detection, and state synchronization in large-scale distributed systems. They can help improve system scalability, fault tolerance, and resilience in the face of network failures or other types of disruptions. However, like all distributed systems designs, gossip protocols have trade-offs, such as increased network overhead and potential delays in propagating updates to all nodes.

![8625cd178d9ba98aad1e41dfc3d823c1.png](../_resources/8625cd178d9ba98aad1e41dfc3d823c1.png)

# 23\. Replica management

In distributed systems, replica management refers to the process of maintaining consistency and coordination of multiple copies of data, services or application instances across different nodes or servers in the system.

One replica management strategy is primary-backup replication, where one node (the primary) is designated as the master copy and all updates to the data/service are applied to this primary node, with the changes then propagated to the backup replicas. This approach provides strong consistency guarantees, but has the downside of requiring a failover process if the primary node fails.

Another strategy is active-active replication, where multiple replicas are actively serving traffic and responding to requests simultaneously. This approach can improve system performance, but may lead to data consistency issues if updates on different replicas occur concurrently.

A third strategy is read replica architecture, where multiple replicas in the system can serve only read requests, while a single primary replica serves both read and write requests. This approach can help scale read-heavy workloads and provide better response times, but may lead to data consistency issues if multiple replicas are updated concurrently.

Quorum-based replication is a technique in distributed systems used to ensure consistency and availability of replicated data. It involves creating a quorum of replicas, where a majority of replicas must be in agreement for a write operation to be considered successful. This technique ensures that any updates to shared data are propagated to the majority of replicas, and the changes are not lost during a network partition or a node failure. Quorum-based replication is often used in distributed databases and other distributed systems where consistency is critical for write and read operations. It helps to ensure that data consistency is maintained while also aiming to provide high availability of data. Quorum-based replication is comparatively easy to implement and is a popular technique for achieving strong data consistency in various distributed systems.

![4819bee82c441c39d12f8b53302015f2.png](../_resources/4819bee82c441c39d12f8b53302015f2.png)

# 24. Self-stabilization

Self-stabilization is a concept of fault-tolerance in distributed systems . It refers to a property of a distributed algorithm or system that guarantees that even if it starts from an arbitrary initial state, it will converge to a correct and stable state within a finite time. In other words, a self-stabilizing system can recover from arbitrary faults, errors, or failures that may occur in the system, and still maintain its correctness and stability.

Self-stabilization is particularly useful in distributed systems where failures and faults are common, and where it can be difficult to ensure that all processes are synchronized and consistent with each other. Self-stabilization can provide a robust and fault-tolerant foundation for many distributed system applications, such as routing protocols, consensus algorithms, and fault-tolerant computing.

There are several types of self-stabilizing algorithms, such as leader election, mutual exclusion, and clock synchronization, that provide different kinds of safety and liveness guarantees. The design and analysis of self-stabilizing algorithms can be challenging due to the non-deterministic and asynchronous nature of distributed systems, and requires a deep understanding of distributed computing theory and practice.

# 25\. HyperLoglog

HyperLogLog is a probabilistic algorithm used for estimating the number of distinct elements in a large dataset or multiset, which becomes impractical to keep track of using traditional methods due to the required amount of memory. The algorithm uses significantly less memory compared to exact methods, and is able to estimate cardinalities of more than a billion with a typical accuracy of 2% using about 1.5 kB of memory. HyperLogLog is an extension of the earlier LogLog algorithm, which is based on a probabilistic approach to estimate the unique count of elements in a dataset. HyperLogLog has various applications in big data analytics, machine learning, distributed query engines, and data recommenders, among others.

It is frequently used in Postgres, Redis, and other distributed systems, and can allow for efficient rollup tables with HyperLogLog, which permit storage and access of data structure concurrently.

The HyperLogLog algorithm works by hashing each element in the dataset to a 64-bit value. The algorithm then examines the binary representation of the hash value to determine the position of the first zero bit. This position is used to assign the element to one of several “buckets” or “registers”.

The algorithm maintains a set of counters, with each counter corresponding to a specific range of register values. For example, one counter might count the number of registers that have a value of zero, while another counter might count the number of registers that have a value of one.

The HyperLogLog algorithm uses a “bias correction” step to reduce the estimation error that occurs when the number of registers is small. The bias correction involves adjusting the estimate by a constant value that depends on the number of registers and the distribution of the hashed elements.

<img src="../_resources/10916cfa2cf52f7c60934d9598794f02.png" alt="10916cfa2cf52f7c60934d9598794f02.png" width="837" height="369" class="jop-noMdConv">

# 26\. Count-min Sketch

Count-min Sketch is a probabilistic data structure used for estimating the frequency of events in a stream of data . It is similar to HyperLogLog in that it uses significantly less memory compared to exact methods, and provides estimated counts with high accuracy. Count-min Sketch uses a hash table with multiple hash functions to map events to a set of counters. Each event is hashed multiple times, and the corresponding counters are incremented. To estimate the frequency of an event, the hash functions are used to retrieve the counters associated with the event, and then the minimum value is returned. Count-min Sketch is frequently used in big data and streaming applications due to its high scalability and accuracy, and can be used for applications such as spam filtering, network monitoring, and intrusion detection, etc.

<img src="../_resources/df489ffb4c4fce5651d2616489ac9ff3.png" alt="df489ffb4c4fce5651d2616489ac9ff3.png" width="476" height="399" class="jop-noMdConv">

# 27\. Hierarchical timing wheels

Hierarchical timing wheels is a technique used for implementing timers in software systems. It is based on the idea of using multiple timing wheels with different granularities to handle timer events 12. The timers are organized into multiple wheels, with each wheel handling a range of timer intervals. A higher-level wheel manages a larger range of timer intervals than a lower-level wheel. When a timer fires, the corresponding event is processed by the lowest-level wheel. If the timer interval falls outside the range of the lowest-level wheel, it is automatically promoted to the next higher-level wheel. This process continues until the timer interval is accommodated by one of the wheels in the hierarchy. Hierarchical timing wheels are commonly used in event-driven systems, and have advantages over other timer implementations such as accuracy, scalability, and avoidance of unnecessary overheads.

<img src="../_resources/468bfff34d9678c11542752f1c6e75d9.png" alt="468bfff34d9678c11542752f1c6e75d9.png" width="512" height="399" class="jop-noMdConv">

# 28\. Operational transformation (OT)

Operational transformation (OT) is a technology used to support collaborative functionalities in advanced collaborative software systems . Originally developed for consistency maintenance and concurrency control in collaborative text document editing, OT has since been expanded to include capabilities such as group undo, locking, conflict resolution, operation notification and compression, group-awareness, HTML/XML and tree-structured document editing, among others. OT uses algorithms to ensure that concurrent operations on shared data result in consistent and predictable outcomes. It has numerous applications in real-time collaborative software systems, such as Google Docs and Microsoft Office, and is used for minimizing latency while preserving document consistency.

The basic idea of OT is to transform operations on a shared object so that they can be applied in a consistent and deterministic way, even when they are applied concurrently by multiple users. In other words, OT ensures that every user sees a consistent view of the shared object, even when there are multiple conflicting updates.

The OT algorithm works by transforming each operation based on the previous operations that have been applied to the shared object. When a user makes an update, their operation is transformed based on the previous operations that have been applied to the shared object. This ensures that the update is applied correctly, even if other users have made conflicting updates.

The OT algorithm is typically implemented using a data structure called an operation history, which stores all the operations that have been applied to the shared object. The history is used to transform new operations and to resolve conflicts between concurrent updates.

![1c9253cfd87928f14988e445c3a6dbc4.png](../_resources/1c9253cfd87928f14988e445c3a6dbc4.png)

# 29\. Last Write Wins (LWW)

Last Write Wins (LWW) is a conflict resolution strategy used in distributed systems. When multiple nodes or clients attempt to update the same data at the same time, conflicts can arise. LWW is a simple approach to handling such conflicts, where the system chooses the update with the most recent timestamp or version number as the winner and discards the other updates.

In LWW, each update is timestamped or given a version number, and when a conflict arises, the system compares the timestamps or version numbers of the conflicting updates. The update with the latest timestamp or version number is chosen as the winner, and its value is used to update the data in the system. The other updates are discarded, and their values are lost.

LWW is easy to implement and works well in situations where conflicts are rare or where losing updates is acceptable. However, LWW can lead to data loss and inconsistencies when multiple updates are made to the same data in quick succession or when timestamps or version numbers are not synchronized correctly across the distributed system.

LWW is often used in distributed databases and other systems where data consistency is not critical or where conflicts are infrequent. In more complex scenarios, such as collaborative editing or real-time collaboration, more sophisticated conflict resolution strategies, such as Operational Transformation (OT), may be required to ensure data integrity and consistency.

Operational Transformation (OT) and Last Write Wins (LWW) are two techniques used to handle conflicts in distributed systems, but they have different approaches and trade-offs.

# 30. Vector clocks

Vector clocks are a mechanism used in distributed systems to track causality and ordering of events between different nodes. In a distributed system, events may occur concurrently on different nodes, and it can be challenging to determine the ordering of these events. Vector clocks are a way to track the relative ordering of events and detect causality between them.

In a vector clock, each node maintains a vector of integers that represent the number of events that have occurred on that node. When a node generates an event, it increments its own component in the vector. When a node receives an event from another node, it updates its vector to include the maximum value of each component from both vectors. This way, the vector clock of each node reflects the relative ordering of events between all nodes in the system.

Vector clocks are useful in many applications, including distributed databases, distributed file systems, and distributed consensus algorithms. They are used to determine whether two events are causally related, whether a node has seen all events from another node, and whether a node's state is consistent with the state of other nodes. By maintaining vector clocks and comparing them across nodes, distributed systems can ensure correct ordering of events and maintain consistency across different nodes.

Some specific uses of vector clocks in distributed systems include:

- Conflict detection and resolution: Vector clocks can be used to detect and resolve conflicts when multiple nodes concurrently modify the same data. By comparing the vector clocks associated with the conflicting updates, a system can determine whether the updates are causally related and which update should be applied.
    
- Consistency maintenance: Vector clocks can be used to ensure that all nodes in a distributed system have an up-to-date view of the system state. By comparing the vector clocks associated with different versions of data, a system can determine whether a node has seen all updates to the data and can safely apply those updates.
    
- Distributed consensus: Vector clocks can be used in consensus algorithms, such as Paxos or Raft, to ensure that all nodes agree on the ordering of events and decisions. By exchanging and comparing vector clocks, nodes can ensure that they have seen all relevant events before making a decision.
    

Implementing vector clocks typically involves assigning a vector of integer counters to each node in the distributed system. Whenever a node generates an event, it increments its own counter in the vector, and the updated vector is propagated to other nodes along with the event. When a node receives an event and its associated vector clock, it updates its own vector clock to include the maximum value of each component from both vectors.

<img src="../_resources/20c254d1a340701b03dcd696fb807bfc.png" alt="20c254d1a340701b03dcd696fb807bfc.png" width="797" height="468">