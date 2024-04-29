---
tags:
  - degree/ads/datastructures
---
![[Data Structures MOC 🌍]]

### The Hash Table

Suppose we want to store data consisting of key-value pairs.

|name|student number|
|-|-|
|Smith|123512|
|Jones|174322|
|Jackson|192852|

We want to be able to look up the values using the keys.
- the total amount of data might be very large
- our algorithms might perform many look ups.

A hash table consists of a bucket array and a hash function.

A bucket array for a hash table is an array $A$ of size $N$, where each cell of $A$ is thought as a bucket storing a collection of KVPs.

The size $N$ of the array is called the capacity of the hash table.

---
### Hash Function

A hash function $h$ is a function that maps each key $k$ to an integer in the range $[0,N-1]$, where $N$ is the capacity of the hash table.

The main idea is the use $h(k)$ as an index into the bucket array $A$. That is, we store the KVP $(k,v)$ in the bucket $A[h(k)]$.
So the hash function tells us the index that the data should be stored in.

Ideally, we'd like a hash function to be efficiently computable and each table position is equally likely for each key.

If there are two keys with the same hash value $h(k)$, then two different entries will be mapped to the same bucket in $A$. This is called a collision.

---
### Compression Function
A compression function is also needed to map the integers output by the hash function to the $[0,N-1]$ range.

Some compression functions include:
- division: take integer mod N
- multiply add and divide (MAD): $y$ maps to $ay+b\mod N$ where $a$ and $b$ are non-negative integers.

---
### Collision Handling

There are several ways to deal with collisions.
Whatever method we choose, ideally we want to minimise the number of collisions as this slows performance. This is what separates bad from good hash functions.

Here are 4 ways of handling collisions:
- Separate Chaining
- Linear Probing
- Quadratic Probing
- Double Hashing

Methods 2, 3 and 4 are examples of [[Open Addressing]] policies for collision reduction.

##### Separate Chaining:

Each bucket $A[i]$ stores a [[Linked Lists|Linked List]] holding the entries $(k,v)$ such that $h(k)=i$.

Each list entry holds the input data the gets that bucket. So if 54, 10, 65 and 98 all map to the same index 100, we can store a list that says 54: data, 10: data, 65:data and 98:data at the index 100. 

Then when we look for key 65, we look at the bucket 100 and see there's multiple entries. Then we traverse the list until we get the node 54: data

Costs:
- Cost is proportional to length of list.
- Average length = $N/M$ ($N$ is amount of data, $M$ is size of array).
- Worst case: all keys hash to same list.

##### Linear Probing:

If we try to insert $(k,v)$ into a bucket $A[i]$ that's already occupied, where $i=h(k)$, then we try next at $A[i+1]\mod N$.

If $A\left[i+1\right]\mod{N}$ is also occupied, then we try $A[i+2]\mod N$ and so on.

The name linear probing comes from the fact that accessing a cell of the bucket array can be viewed as a probe.

Costs:
- Insert and search costs depend on length of cluster
- Average length of cluster is $N/M$.
- Worst case: all keys hash to same cluster

##### Quadratic Probing

Quadratic probing iteratively tries the buckets $A[i+f(j)\mod N]$ for $j=0,1,2,...,$ where $f(j)=j^2$ until it finds an empty bucket.

Quadratic probing avoids clustering patterns that occur with linear probing. However, it creates its own kind of clustering, called secondary clustering.

The quadratic probing strategy may not find an empty bucket in $A$ even if one exists.

##### Double Hashing

We have a secondary hash function $h'$ and if $h$ maps some key that's already occupied, we iteratively try the buckets $A[(i+f(j))\mod N]$, for $j=0,1,2,...,$ where $f(j)=j\times h'(k)$.

A common choice for secondary hash functions is $k'(k)=q-(k\mod q)$, for some prime number $q<N$.

The secondary hash function should not evaluate to zero.

---
### Comparisons

The [[Open Addressing]] schemes are more memory efficient compared to separate chaining.

The separate chaining method can be just as fast or faster than other methods

If memory space is not an issue, separate chaining is the method of choice.

---
### Deletions from a Hash Table

Deletions from the hash table must not hinder future searches.
If you just leave a bucket empty this will hinder future probes.

But you also can't just leave the bucket unusable.

To solve this, we use tombstones that are markers of deleted buckets.

If you find a tombstone while searching, you can just ignore it.

If you find a tombstone while inserting, you can put the new record in the bucket with the tombstone.

The use of tombstones lengthens the average probe sequence distance which is an issue.

Two possible remedies are:
- Local Reorganisation
	- After deleting a key, continue to follow the probe sequence of that key and move records into the vacated bucket.
- Periodically rehash the table and reinsert all records into a new hash table.