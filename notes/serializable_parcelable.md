# serializable  
-  is a **standard Java interface** not part of Android SDK.
- The problem with this approach is that reflection is used and it is a **slow** process(if not properly used). 
- **Reflection** is the term for inspecting objects, fields and methods at run-time via Object.getClass()
- Serializables are **better** for **persisting data**.
- **easy to implemet**(just implement the Serializable interface and Java will simply do its best effort to serialize it efficiently).
- Serializable **tends** to create a lot of **temporary objects** and cause quite a bit of garbage collection.


# Parcelable 
- is an **interface** and part of Android SDK.
- Parcelable was specifically designed in such a way that there is **no reflection** when using it.
- we are actually **writing custom code**.
- is **faster** than Serializable in case of default implementation.
- Parcelable interface **takes more time** to implement compared to Serializable interface
- Parcelable array can be passed via Intent in android.
- There are plugins that help creating Parcelable.