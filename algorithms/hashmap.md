# HashMap

## How HashMap works internally in Java
- Hashing: a way to assigning a unique code for any variable/object after applying any formula/algorithm on its properties.
  - Hash function should return the same hash code each and every time when the function is applied on same or equal objects.
  - All objects in Java inherit a default implementation of `hashCode()` function defined in `Object` class. This function produces hash code by typically converting the internal address of the object into an integer, thus producing different hash codes for all different objects.
  - HashMap has an inner class Entry:
  ```java
  static class Entry<K ,V> implements Map.Entry<K, V> {
      final K key;
      V value;
      Entry<K ,V> next;
      final int hash;
      ...//More code goes here
  }
  ```
* More Details: https://howtodoinjava.com/java/collections/hashmap/how-hashmap-works-in-java/#short_answer
