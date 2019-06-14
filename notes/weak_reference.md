## Definition
In computer programming, a **weak reference** is a reference that **does not protect** the **referenced object** from **collection** by a **garbage collector**, unlike a strong reference.


## Uses
- in the **observer pattern** (particularly in event handling), if a strong reference is kept, objects **must be explicitly unregistered,** otherwise a memory leak occurs (the lapsed listener problem), while a **weak reference** **removes the need to unregister**.

- the most known use of these references is the **WeakHashMap** class. It’s the implementation of the Map interface where every **key** is stored as **a weak reference** to the given key. When the Garbage Collector **removes a key**, the entity associated with this key is **deleted as well**.


## Examples
since Java 1.2 there are two types:-
  - soft rerefernce 
  - weak reference

for example 
``` java 
import java.lang.ref.WeakReference;

public class ReferenceTest {
	public static void main(String[] args) throws InterruptedException {

            WeakReference wr = new WeakReference("I'm here");
            StrongReference sr = new StrongReference("I'm here");
            System.out.println("before gc: r=" + wr.get() + ", static=" + sr.get());
            System.gc();
            Thread.sleep(100);

            // only r.get() becomes null
            System.out.println("after gc: r=" + wr.get() + ", static=" + sr.get());

	}
}
```  


## eXTRA 

- These special behaviour of SoftReference and WeakReference makes them useful in certain cases e.g. SoftReference looks perfect for implementing caches, so when JVM needs memory it removes object which have only SoftReference pointing towards them.

- On the other hand WeakReference is great for storing meta data e.g. storing ClassLoader reference. If no class is loaded then no point in keeping reference of ClassLoader, a WeakReference makes ClassLoader eligible for Garbage collection as soon as last strong reference removed.

- Some cases
  - **Strong** referece prevent object from GC.
  - **Weak** referece does not prevent object from GC.
  - **Soft** referece does not prevent object from GC but delay it until need a memory.
  - **Phantom** referece does not prevent object from GC (GC collects it whenever it like).





