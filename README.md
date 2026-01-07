# IndexedPagedList

**Author:** Andy Pham  
**Course:** CS2280 - Data Structures & Algorithms (Iowa State University, HW3)  

---

## Overview

`IndexedPagedList` is a custom implementation of the Java `List` interface that uses a **doubly-linked list of pages** (nodes), where each page stores multiple elements in an array. This design is optimized for:

- **Fast indexed access:** $O(\log N_\text{pages})$ time using a binary search over a top-level page index.
- **Efficient iteration:** Fail-fast list iterator starting at any position.
- **Dynamic updates:** Handles page splitting, merging, and rebalancing to maintain performance during insertions and deletions.

---

## Key Features

- **Paged structure:** Each page stores multiple items, reducing overhead of traditional linked lists.
- **Binary-search page indexing:** Quickly finds the page for any logical index.
- **Fail-fast iterator:** Detects concurrent modifications for safe iteration.
- **Automatic page management:** Pages are split or merged based on item count to maintain efficiency.
- **Generic:** Can store any type `<E>`.

---

## Example Usage

```java
public class TestIndexedPagedList {
    public static void main(String[] args) {
        IndexedPagedList<Integer> list = new IndexedPagedList<>();
        
        // Add elements
        list.add(10);
        list.add(20);
        list.add(1, 15); // Insert at index 1
        
        // Remove element
        list.remove(0);
        
        // Iterate
        for (Integer i : list) {
            System.out.println(i);
        }

        // Internal view of pages
        System.out.println(list.toStringInternal());
    }
}
