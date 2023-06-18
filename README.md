# Generics-Collections
Generics, Sort &amp; Search in Collections

Key Attributes of Common Collection Classes:

1. ArrayList: Fast Iteration and fast random access.

2. LinkedList: Good for adding elements at the end i.e Stacks and Queues. 

3. HashSet: Fast access, no duplicates, provides no ordering

4. LinkedHashSet: No duplicates, iterates by insertion order.

5. TreeSet: No duplicates, iterates in sorted order.

6. HashMap: Fastest updates(Key/Value) pairs. Allows one null key, and many null values.

7. HashTable: Like a slower HashMap (due to synchronized methods). No null keys or null values allowed.

HashTable - Does not allow null keys
This is because, in put(K key, V value) method, we have key.hashcode() which throws null pointer exception.
HashTable - Does not allow null value
This is because, in put(K key, V value) method we have if(value==null){throw new NullPointerException

HashMap allows null values as it doesn't have any checks like HashTable, while it allows only one null key. This is done with the help of putForNullKey method, which add the value to the 0th index of the internal Array every time the key is provided as null

8. LinkedHashMap: Faster iterations, iterates by insertion order or last accessed. Allows one null key and many null keys.

9. TreeMap: A sorted map.

10. Iterated with the enhanced for loop, or with an iterator via hasNext() and next();

11. hasNext() returns if more elements exist, the Iterator does not move.

12. next() returns the next element and moves the iterator forward.

13. To work correctly, a Map's keys must override equals() and hashcodes();

14. Queues use offer() to add an element, poll() to remove the head of the queue, and peek() to look at the head of the queue.

15. Difference between synchronized and concurrent collections in Java?

    Synchronized collection classes, Hashtable, Vector and the synchronized wrapper classes, Collections.synchronizedMap() and                                          Collections.synchronizedList()provides a basic thread safe implementation of Map and List. However, in a highly concurrent environment, usage of synchronized       collection classes is rarely useful as the entire collection needs to be locked in order to avoid ConcurrentModificationException during iteration.

    In Summary, concurrent collections use advanced techniques to achieve thread-safety without compromising Scalability. For example, ConcurrentHashMap only           locks a certain portion of Map while Hashtable locks a full map while doing iteration or performing any write operation.

5. MetaSpace in Java 8.
 JVM Memory Structure is divided into multiple memory area like heap area, stack area, method area, PC Registers etc. The following image illustrates the different memory areas in Java: 

The heap is created when the JVM starts. The heap is generally divided into two parts. That is: 
1.Young Generation(Nursery): All the new objects are allocated in this memory. Whenever this memory gets filled, the garbage collection is performed. This is called as Minor Garbage Collection.
2.Old Generation: All the long lived objects which have survived many rounds of minor garbage collection is stored in this area. Whenever this memory gets filled, the garbage collection is performed. This is called as Major Garbage Collection.

Apart from the heap memory, JVM also contains another type of memory which is called as Permanent Generation or “PermGen”. 




PermGen Memory: This is a special space in java heap which is separated from the main memory where all the static content is stored in this section. Apart from that, this memory also stores the application metadata required by the JVM. Metadata is a data which is used to describe the data. Here, garbage collection also happens like any other part of the memory. String pool was also part of this memory before Java 7. Method Area is a part of space in the PermGen and it is used to store the class structure and the code for methods and constructors. The biggest disadvantage of PermGen is that it contains a limited size which leads to an OutOfMemoryError. The default size of PermGen memory is 64 MB on 32-bit JVM and 82 MB on the 64-bit version. Due to this, JVM had to change the size of this memory by frequently performing Garbage collection which is a costly operation. Java also allows to manually change the size of the PermGen memory. However, the PermGen space cannot be made to auto increase. So, it is difficult to tune it. And also, the garbage collector is not efficient enough to clean the memory. 
Due to the above problems, PermGen has been completely removed in Java 8. In the place of PermGen, a new feature called Meta Space has been introduced. MetaSpace grows automatically by default. Here, the garbage collection is automatically triggered when the class metadata usage reaches its maximum metaspace size. 




























