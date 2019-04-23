# HashTable
The main idea of a hash table is to take a bucket array, A, and a hash function, h, and
use them to implement a map by storing each entry (k,v) in the “bucket” A[h(k)].

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
  
## Compression Functions
Once an integer `hash code` is generated for a key object `k`, there is still the issue of mapping that integer 
into the range `[0,N−1]`. The integer hash code may be `negative` or may `exceed the capacity` of the bucket array.
This computation, known as a `compression function`.

### The MAD (Multiply-Add-and-Divide) Method

`[(ai+b) mod p] mod N`

`N` is the `size` of the bucket array, `p` is a `prime number` larger than `N`, and `a` and `b` are integers chosen at 
random from the interval `[0, p−1]`, with `a > 0`.

This compression function is chosen in order to eliminate `repeated patterns` in the set of
hash codes and get us closer to having a “good” hash function, that is, one such that
the probability any two different keys collide is `1/N`.

## Collision-Handling Schemes
### Separate Chaining
A simple and efficient way for dealing with collisions is to have each bucket A[ j]
store its own secondary container, holding all entries (k,v) such that h(k) = j. A
natural choice for the secondary container is a small map instance implemented
using an unordered list.

