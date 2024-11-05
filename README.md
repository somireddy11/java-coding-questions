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
