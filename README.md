# kth largest element in a stream
## https://leetcode.com/problems/kth-largest-element-in-a-stream


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
Note that in the `add(num)` if the size of minHeap is less than k, we simply add the num to minHeap, otherwise we check whether new element is greater than the peek element (smallest element) in the minHeap, if thats the case only then we add the new element to minHeap.

# References :
https://leetcode.com/problems/kth-largest-element-in-a-stream/discuss/149050/Java-Priority-Queue



