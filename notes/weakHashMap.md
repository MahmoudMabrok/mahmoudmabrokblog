Let’s say that we want to build a cache that keeps big image objects as values, and image names as keys. We want to pick a proper map implementation for solving that problem.

Using a simple HashMap will not be a good choice because the value objects may occupy a lot of memory. What’s more, they’ll never be reclaimed from the cache by a GC process, even when they are not in use in our application anymore.

Ideally, we want a Map implementation that allows GC to automatically delete unused objects. When a key of a big image object is not in use in our application in any place, that entry will be deleted from memory.

Fortunately, the WeakHashMap has exactly these characteristics. Let’s test our WeakHashMap and see how it behaves:


``` java
WeakHashMap<UniqueImageName, BigImage> map = new WeakHashMap<>();
BigImage bigImage = new BigImage("image_id");
UniqueImageName imageName = new UniqueImageName("name_of_big_image");
 
map.put(imageName, bigImage);
assertTrue(map.containsKey(imageName));
 
imageName = null;
System.gc();
 
await().atMost(10, TimeUnit.SECONDS).until(map::isEmpty);
```