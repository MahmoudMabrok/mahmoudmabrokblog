- **garbage collection (GC)** is a form of **automatic memory management**.
- The garbage collector, or just collector, attempts to **reclaim garbage**, or memory occupied by objects that are **no longer in use** by the program.
- **GC** is used to **clean up unused objects** and so **reduce** the potential for **memory leaks** and data corruption. 
- **Types of garbage collection**:
  - Tracing
    ` The overall strategy consists of determining which objects should be garbage collected by tracing which objects are reachable by a chain of references from certain root objects, and considering the rest as garbage and collecting them`
  - Reference Counting.

- Resources other than memory, such as **network sockets**, **database handles**, **user interaction windows**, **file** and **device descriptors**, are **not typically handled** by garbage collection. 





