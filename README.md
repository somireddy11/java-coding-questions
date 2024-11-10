# java-coding-questions

Sure! Below is a coding question related to Java collections:

### Problem Statement: **Find the Most Frequent Element in a List**

**Description**: Given a list of integers, find the element that appears the most in the list. If there is a tie (i.e., multiple elements appear the same maximum number of times), return the smallest of these elements.

**For example**:
- Input: `[4, 5, 6, 4, 4, 5, 5, 7]`
- Output: `4`

**Input**:
- A list of integers `nums`.

**Output**:
- The element that occurs the most in the list. If multiple elements have the same frequency, return the smallest one.

### Approach:

1. **Use a HashMap** to store the frequency of each element.
2. **Iterate through the list** and populate the HashMap with the count of each element.
3. **Identify the maximum frequency** and then check for the element(s) with that frequency.
4. If multiple elements have the same frequency, return the smallest one.

---

### Solution:

```java
import java.util.*;

public class MostFrequentElement {
    public static int findMostFrequent(List<Integer> nums) {
        // Step 1: Create a HashMap to store the frequency of each element
        Map<Integer, Integer> frequencyMap = new HashMap<>();
        
        // Step 2: Populate the frequency map
        for (int num : nums) {
            frequencyMap.put(num, frequencyMap.getOrDefault(num, 0) + 1);
        }

        // Step 3: Find the element with the highest frequency and handle ties
        int mostFrequentElement = nums.get(0); // Start with the first element
        int maxFrequency = frequencyMap.get(mostFrequentElement);

        for (Map.Entry<Integer, Integer> entry : frequencyMap.entrySet()) {
            int currentElement = entry.getKey();
            int currentFrequency = entry.getValue();

            if (currentFrequency > maxFrequency || (currentFrequency == maxFrequency && currentElement < mostFrequentElement)) {
                mostFrequentElement = currentElement;
                maxFrequency = currentFrequency;
            }
        }

        return mostFrequentElement;
    }

    public static void main(String[] args) {
        List<Integer> nums = Arrays.asList(4, 5, 6, 4, 4, 5, 5, 7);
        System.out.println("Most frequent element: " + findMostFrequent(nums)); // Output: 4
    }
}
```

---

### Explanation of the Solution:

1. **Frequency Map (HashMap)**: We use a `HashMap<Integer, Integer>` to store each element as the key and its frequency (count) as the value.
   
2. **Populating the Frequency Map**: We loop through each element of the list, and for each element, we update its count in the `frequencyMap`. We use the `getOrDefault` method to return the current count or `0` if the element does not exist in the map yet.

3. **Finding the Most Frequent Element**:
   - We iterate through the entries of the map.
   - For each entry, if the current frequency is higher than the `maxFrequency`, we update the `mostFrequentElement` to this one.
   - If the current frequency is equal to `maxFrequency`, we check if the current element is smaller than the `mostFrequentElement` and update it if needed (to handle ties).

4. **Time Complexity**:
   - **Time complexity**: O(n), where `n` is the size of the input list, because we iterate over the list once to populate the map and once over the map entries to find the result.
   - **Space complexity**: O(n), where `n` is the size of the input list, as we store the frequencies of all elements in the map.

---

### Test Cases:

**Test Case 1**:
```java
List<Integer> nums = Arrays.asList(4, 5, 6, 4, 4, 5, 5, 7);
System.out.println(findMostFrequent(nums)); // Output: 4
```

**Test Case 2**:
```java
List<Integer> nums = Arrays.asList(1, 1, 2, 2, 3, 3);
System.out.println(findMostFrequent(nums)); // Output: 1 (since 1 and 2 have the same frequency, but 1 is smaller)
```

**Test Case 3**:
```java
List<Integer> nums = Arrays.asList(10, 20, 30, 20, 10, 10);
System.out.println(findMostFrequent(nums)); // Output: 10
```

---

Let me know if you would like to explore any variations of this problem or if you have any other questions!


2. Find the Intersection of Two Lists
Problem: Given two lists of integers, find the intersection of both lists. Each element in the intersection should appear only once, and the result should be a list containing all the common elements.

Example:

Input: list1 = [1, 2, 2, 1], list2 = [2, 2]
Output: [2]
Approach:
Use HashSet to remove duplicates and find the common elements between the two

import java.util.*;

public class ListIntersection {
    public static List<Integer> intersection(List<Integer> list1, List<Integer> list2) {
        Set<Integer> set1 = new HashSet<>(list1);
        Set<Integer> result = new HashSet<>();

        for (int num : list2) {
            if (set1.contains(num)) {
                result.add(num);
            }
        }

        return new ArrayList<>(result);
    }

    public static void main(String[] args) {
        List<Integer> list1 = Arrays.asList(1, 2, 2, 1);
        List<Integer> list2 = Arrays.asList(2, 2);
        System.out.println(intersection(list1, list2)); // Output: [2]
    }
}

Certainly! Here are some more Java collections-related coding questions to test your understanding and problem-solving skills.

### 1. **Find the Intersection of Two Lists**
**Problem**: 
Given two lists of integers, find the intersection of both lists. Each element in the intersection should appear only once, and the result should be a list containing all the common elements.

**Example**:
- Input: `list1 = [1, 2, 2, 1]`, `list2 = [2, 2]`
- Output: `[2]`

### Approach:
- Use `HashSet` to remove duplicates and find the common elements between the two sets.
  
**Solution**:
```java
import java.util.*;

public class ListIntersection {
    public static List<Integer> intersection(List<Integer> list1, List<Integer> list2) {
        Set<Integer> set1 = new HashSet<>(list1);
        Set<Integer> result = new HashSet<>();

        for (int num : list2) {
            if (set1.contains(num)) {
                result.add(num);
            }
        }

        return new ArrayList<>(result);
    }

    public static void main(String[] args) {
        List<Integer> list1 = Arrays.asList(1, 2, 2, 1);
        List<Integer> list2 = Arrays.asList(2, 2);
        System.out.println(intersection(list1, list2)); // Output: [2]
    }
}
```

---

### 2. **Merge Two Sorted Lists**
**Problem**:
Given two sorted lists, merge them into one sorted list.

**Example**:
- Input: `list1 = [1, 2, 4]`, `list2 = [1, 3, 4]`
- Output: `[1, 1, 2, 3, 4, 4]`

### Approach:
- Use a two-pointer technique to merge both lists while maintaining the sorted order.

**Solution**:
```java
import java.util.*;

public class MergeSortedLists {
    public static List<Integer> mergeSorted(List<Integer> list1, List<Integer> list2) {
        List<Integer> result = new ArrayList<>();
        int i = 0, j = 0;

        while (i < list1.size() && j < list2.size()) {
            if (list1.get(i) <= list2.get(j)) {
                result.add(list1.get(i));
                i++;
            } else {
                result.add(list2.get(j));
                j++;
            }
        }

        // Add remaining elements
        while (i < list1.size()) {
            result.add(list1.get(i));
            i++;
        }

        while (j < list2.size()) {
            result.add(list2.get(j));
            j++;
        }

        return result;
    }

    public static void main(String[] args) {
        List<Integer> list1 = Arrays.asList(1, 2, 4);
        List<Integer> list2 = Arrays.asList(1, 3, 4);
        System.out.println(mergeSorted(list1, list2)); // Output: [1, 1, 2, 3, 4, 4]
    }
}
```

---

### 3. **Remove Duplicates from a List**
**Problem**:
Given a list of integers, remove all duplicate values from the list.

**Example**:
- Input: `[1, 2, 2, 3, 4, 4]`
- Output: `[1, 2, 3, 4]`

### Approach:
- Use a `HashSet` to remove duplicates because sets do not allow duplicate elements.

**Solution**:
```java
import java.util.*;

public class RemoveDuplicates {
    public static List<Integer> removeDuplicates(List<Integer> list) {
        Set<Integer> set = new HashSet<>(list);
        return new ArrayList<>(set);
    }

    public static void main(String[] args) {
        List<Integer> list = Arrays.asList(1, 2, 2, 3, 4, 4);
        System.out.println(removeDuplicates(list)); // Output: [1, 2, 3, 4]
    }
}
```

---

### 4. **Find the Kth Largest Element in an Array**
**Problem**:
Given an array of integers, find the `K`th largest element in the array.

**Example**:
- Input: `arr = [3, 2, 1, 5, 6, 4]`, `K = 2`
- Output: `5`

### Approach:
- Use a `PriorityQueue` (min-heap) to keep track of the top `K` elements.

**Solution**:
```java
import java.util.*;

public class KthLargestElement {
    public static int findKthLargest(int[] nums, int k) {
        PriorityQueue<Integer> minHeap = new PriorityQueue<>();

        for (int num : nums) {
            minHeap.add(num);
            if (minHeap.size() > k) {
                minHeap.poll();  // Remove the smallest element when size exceeds k
            }
        }

        return minHeap.peek();  // The root of the min-heap is the kth largest element
    }

    public static void main(String[] args) {
        int[] nums = {3, 2, 1, 5, 6, 4};
        int k = 2;
        System.out.println(findKthLargest(nums, k)); // Output: 5
    }
}
```

---

### 5. **Group Anagrams**
**Problem**:
Given a list of strings, group the anagrams together. An anagram is a word formed by rearranging the letters of another word.

**Example**:
- Input: `["eat", "tea", "tan", "ate", "nat", "bat"]`
- Output: `[["eat", "tea", "ate"], ["tan", "nat"], ["bat"]]`

### Approach:
- Use a `Map` to group words by their sorted characters as the key.

**Solution**:
```java
import java.util.*;

public class GroupAnagrams {
    public static List<List<String>> groupAnagrams(List<String> strs) {
        Map<String, List<String>> map = new HashMap<>();

        for (String str : strs) {
            char[] chars = str.toCharArray();
            Arrays.sort(chars);
            String key = new String(chars);

            map.computeIfAbsent(key, k -> new ArrayList<>()).add(str);
        }

        return new ArrayList<>(map.values());
    }

    public static void main(String[] args) {
        List<String> strs = Arrays.asList("eat", "tea", "tan", "ate", "nat", "bat");
        System.out.println(groupAnagrams(strs)); 
        // Output: [["eat", "tea", "ate"], ["tan", "nat"], ["bat"]]
    }
}
```

---

### 6. **First Non-Repeated Character**
**Problem**:
Given a string, find the first non-repeating character. If there is no non-repeating character, return `-1`.

**Example**:
- Input: `"leetcode"`
- Output: `'l'`

### Approach:
- Use a `LinkedHashMap` to preserve the order of characters and count their occurrences.

**Solution**:
```java
import java.util.*;

public class FirstNonRepeatingCharacter {
    public static char firstUniqChar(String s) {
        Map<Character, Integer> map = new LinkedHashMap<>();
        
        // Count occurrences of each character
        for (char c : s.toCharArray()) {
            map.put(c, map.getOrDefault(c, 0) + 1);
        }
        
        // Find the first character with count 1
        for (Map.Entry<Character, Integer> entry : map.entrySet()) {
            if (entry.getValue() == 1) {
                return entry.getKey();
            }
        }
        
        return '-';  // Return '-' if no unique character exists
    }

    public static void main(String[] args) {
        String s = "leetcode";
        System.out.println(firstUniqChar(s)); // Output: 'l'
    }
}
```

---




### Conclusion:

These coding questions cover a variety of problems related to Java collections, including lists, sets, maps, and heaps. They test your ability to manipulate collections efficiently and implement common algorithms using the appropriate data structures.

Feel free to try these questions and let me know if you need help with solutions or further explanations. Happy coding!


###7  How do you find the frequency of each element in an ArrayList?


Here are some commonly asked Java interview questions focusing on the Collections framework. These questions range from basic concepts to more advanced applications and are designed to test your understanding of different collection classes, algorithms, and performance considerations.

---

### 1. **How do you remove duplicates from an ArrayList in Java?**

One way to remove duplicates from an `ArrayList` is to convert it into a `Set` and then back to an `ArrayList`, as `Set` does not allow duplicates.

```java
import java.util.*;

public class RemoveDuplicates {
    public static void main(String[] args) {
        List<Integer> list = new ArrayList<>(Arrays.asList(1, 2, 2, 3, 4, 4, 5));
        
        // Method 1: Using a HashSet
        List<Integer> uniqueList = new ArrayList<>(new HashSet<>(list));
        
        // Method 2: Using LinkedHashSet to maintain insertion order
        List<Integer> uniqueListOrdered = new ArrayList<>(new LinkedHashSet<>(list));
        
        System.out.println("Without duplicates: " + uniqueList);
        System.out.println("Without duplicates (maintained order): " + uniqueListOrdered);
    }
}
```

---

### 2. **How do you find the frequency of each element in an ArrayList?**

Use a `HashMap` to count the occurrences of each element.

```java
import java.util.*;

public class FrequencyCounter {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("apple", "banana", "apple", "orange", "banana", "apple");
        
        Map<String, Integer> frequencyMap = new HashMap<>();
        
        for (String item : list) {
            frequencyMap.put(item, frequencyMap.getOrDefault(item, 0) + 1);
        }
        
        System.out.println("Frequency of elements: " + frequencyMap);
    }
}
```

---

### 3. **How do you find the intersection of two lists in Java?**

You can use `retainAll` to find the intersection between two lists.

```java
import java.util.*;

public class IntersectionOfLists {
    public static void main(String[] args) {
        List<Integer> list1 = new ArrayList<>(Arrays.asList(1, 2, 3, 4, 5));
        List<Integer> list2 = new ArrayList<>(Arrays.asList(3, 4, 5, 6, 7));
        
        list1.retainAll(list2);
        
        System.out.println("Intersection: " + list1); // Output: [3, 4, 5]
    }
}
```

---

### 4. **How do you sort a `Map` by its values?**

You can use a `LinkedHashMap` to maintain insertion order after sorting by values.

```java
import java.util.*;
import java.util.stream.*;

public class SortMapByValue {
    public static void main(String[] args) {
        Map<String, Integer> map = new HashMap<>();
        map.put("apple", 3);
        map.put("banana", 1);
        map.put("orange", 2);
        
        Map<String, Integer> sortedMap = map.entrySet()
            .stream()
            .sorted(Map.Entry.comparingByValue())
            .collect(Collectors.toMap(
                Map.Entry::getKey,
                Map.Entry::getValue,
                (e1, e2) -> e1,
                LinkedHashMap::new
            ));
        
        System.out.println("Map sorted by values: " + sortedMap);
    }
}
```

---

### 5. **How do you find the first non-repeating character in a string using collections?**

Use a `LinkedHashMap` to maintain insertion order and count occurrences.

```java
import java.util.*;

public class FirstNonRepeatingCharacter {
    public static void main(String[] args) {
        String str = "swiss";
        Map<Character, Integer> charCount = new LinkedHashMap<>();
        
        for (char c : str.toCharArray()) {
            charCount.put(c, charCount.getOrDefault(c, 0) + 1);
        }
        
        for (Map.Entry<Character, Integer> entry : charCount.entrySet()) {
            if (entry.getValue() == 1) {
                System.out.println("First non-repeating character: " + entry.getKey());
                break;
            }
        }
    }
}
```

---

### 6. **How do you reverse a `List` in Java?**

You can use `Collections.reverse()` to reverse the elements of a list in place.

```java
import java.util.*;

public class ReverseList {
    public static void main(String[] args) {
        List<Integer> list = new ArrayList<>(Arrays.asList(1, 2, 3, 4, 5));
        
        Collections.reverse(list);
        
        System.out.println("Reversed list: " + list);
    }
}
```

---

### 7. **How do you implement a LRU Cache in Java using Collections?**

Use a `LinkedHashMap` with access order to implement an LRU Cache.

```java
import java.util.*;

class LRUCache<K, V> extends LinkedHashMap<K, V> {
    private final int capacity;

    public LRUCache(int capacity) {
        super(capacity, 0.75f, true);
        this.capacity = capacity;
    }

    @Override
    protected boolean removeEldestEntry(Map.Entry<K, V> eldest) {
        return size() > capacity;
    }

    public static void main(String[] args) {
        LRUCache<Integer, String> cache = new LRUCache<>(3);
        cache.put(1, "one");
        cache.put(2, "two");
        cache.put(3, "three");
        cache.get(1); // Access element to move it to the most recent position
        cache.put(4, "four"); // This will evict key 2

        System.out.println(cache.keySet()); // Output: [3, 1, 4]
    }
}
```

---

### 8. **How do you convert a `List` of strings into a single comma-separated string?**

Use `String.join()` or Java Streams to concatenate list elements.

```java
import java.util.*;

public class ListToString {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("apple", "banana", "orange");
        
        String result = String.join(", ", list);
        System.out.println("Comma-separated string: " + result);
    }
}
```

---

### 9. **How do you find the maximum occurring element in an array using collections?**

Use a `HashMap` to count occurrences and find the maximum.

```java
import java.util.*;

public class MaxOccurringElement {
    public static void main(String[] args) {
        int[] arr = {1, 2, 2, 3, 3, 3, 4, 5};
        
        Map<Integer, Integer> countMap = new HashMap<>();
        
        for (int num : arr) {
            countMap.put(num, countMap.getOrDefault(num, 0) + 1);
        }
        
        int maxCount = 0;
        int maxElement = -1;
        
        for (Map.Entry<Integer, Integer> entry : countMap.entrySet()) {
            if (entry.getValue() > maxCount) {
                maxCount = entry.getValue();
                maxElement = entry.getKey();
            }
        }
        
        System.out.println("Max occurring element: " + maxElement);
    }
}
```

---

### 10. **How do you shuffle elements in a `List` in Java?**

You can use `Collections.shuffle()` to randomly shuffle elements in a list.

```java
import java.util.*;

public class ShuffleList {
    public static void main(String[] args) {
        List<Integer> list = new ArrayList<>(Arrays.asList(1, 2, 3, 4, 5));
        
        Collections.shuffle(list);
        
        System.out.println("Shuffled list: " + list);
    }
}
```

---

These questions cover a variety of Java Collection concepts and methods, from basic operations to more complex data manipulation tasks. Understanding these examples will help you perform well in coding interviews focusing on Java collections.

