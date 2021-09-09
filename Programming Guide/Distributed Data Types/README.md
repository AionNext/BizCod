# Distributed Data Types 

Abstract data Types (DDT) prvides convenient way to deal with specific data structures that 

* Map
* Multimap
* Stack
* Queue
* Rinbuffer
* Graph
* List
* Set


Topic

* Topic is the distributed mechanism for publishing messages that are delivered to multiple subscribers. It is also known as the publish/subscribe (pub/sub) messaging model.

Concurrency utilities

* FencedLock is the distributed implementation of java.util.concurrent.locks.Lock. When you use lock, the critical section that Hazelcast Lock guards is guaranteed to be executed by only one thread in the entire cluster.

ISemaphore is the distributed implementation of java.util.concurrent.Semaphore. When performing concurrent activities, semaphores offer permits to control the thread counts.

IAtomicLong is the distributed implementation of java.util.concurrent.atomic.AtomicLong. Most of AtomicLong’s operations are available. However, these operations involve remote calls and hence their performances differ from AtomicLong, due to being distributed.

IAtomicReference is the distributed implementation of java.util.concurrent.atomic.AtomicReference. When you need to deal with a reference in a distributed environment, you can use Hazelcast IAtomicReference.

FlakeIdGenerator is used to generate cluster-wide unique identifiers.

ICountdownLatch is the distributed implementation of java.util.concurrent.CountDownLatch. Hazelcast CountDownLatch is a gate keeper for concurrent activities. It enables the threads to wait for other threads to complete their operations.

PN counter is a distributed data structure where each Hazelcast instance can increment and decrement the counter value and these updates are propagated to all replicas.
