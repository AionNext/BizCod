# Distributed Data Types 

Distributed Data Types (DDT) provide convenient way to deal with specific data structures that are available in distributed environments 

* DMap
* DMultimap
* DStack
* DQueue
* DRingbuffer
* DGraph
* DList
* DSet


Topic

* Topic is the distributed mechanism for publishing messages that are delivered to multiple subscribers. It is also known as the publish/subscribe (pub/sub) messaging model.

Concurrency utilities

* FencedLock is the distributed implementation of Lock. When you use lock, the critical section that Lock guards is guaranteed to be executed by only one thread in the entire cluster.

* Semaphore is the distributed implementation of Semaphore. When performing concurrent activities, semaphores offer permits to control the thread counts.

* AtomicReference  When you need to deal with a reference in a distributed environment, you can use  AtomicReference.

* FlakeIdGenerator is used to generate cluster-wide unique identifiers.

