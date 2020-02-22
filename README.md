# kth largest element in a stream
## https://leetcode.com/problems/kth-largest-element-in-a-stream

Design a class to find the kth largest element in a stream. Note that it is the kth largest element in the sorted order, not the kth distinct element.

Your KthLargest class will have a constructor which accepts an integer k and an integer array nums, which contains initial elements from the stream. For each call to the method KthLargest.add, return the element representing the kth largest element in the stream.
```
Example:

int k = 3;
int[] arr = [4,5,8,2];
KthLargest kthLargest = new KthLargest(3, arr);
kthLargest.add(3);   // returns 4
kthLargest.add(5);   // returns 5
kthLargest.add(10);  // returns 5
kthLargest.add(9);   // returns 8
kthLargest.add(4);   // returns 8
```

**Note: You may assume that nums' length ≥ k-1 and k ≥ 1.**

## Implementation : Min Heap

```java
class KthLargest {
        private PriorityQueue<Integer> minHeap;
        private int k;

        public KthLargest(int k, int[] nums) {
            this.k = k;
            minHeap = new PriorityQueue<>(k);
            for (int num : nums)
                add(num);
        }

        public int add(int num) {
            if (minHeap.size() < k)
                minHeap.add(num);
            else if (minHeap.peek() < num) {
                minHeap.poll();
                minHeap.add(num);
            }
            return minHeap.peek();
        }
}
```

### Key points :
Note that in the `add(num)` function, if the size of minHeap is less than k, we simply add the num to minHeap, otherwise we check whether new element is greater than the peek element (smallest element) in the minHeap, if thats the case only then we add the new element to minHeap by first removing the smallest element from minHeap of size k.

This is how we maintain the minHeap of size k, so the kth largest element will always be peek of minHeap.

# References :
https://leetcode.com/problems/kth-largest-element-in-a-stream/discuss/149050/Java-Priority-Queue



