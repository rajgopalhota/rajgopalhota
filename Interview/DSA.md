### **DSA Questions and Answers in Java (Basic to Medium)**

#### **Arrays**

1. **Find the maximum element in an array.**
   ```java
   public static int findMax(int[] arr) {
       int max = arr[0];
       for (int num : arr) {
           if (num > max) max = num;
       }
       return max;
   }
   ```

2. **Reverse an array.**
   ```java
   public static void reverseArray(int[] arr) {
       int start = 0, end = arr.length - 1;
       while (start < end) {
           int temp = arr[start];
           arr[start] = arr[end];
           arr[end] = temp;
           start++;
           end--;
       }
   }
   ```

3. **Find the second largest element in an array.**
   ```java
   public static int findSecondLargest(int[] arr) {
       int largest = Integer.MIN_VALUE, secondLargest = Integer.MIN_VALUE;
       for (int num : arr) {
           if (num > largest) {
               secondLargest = largest;
               largest = num;
           } else if (num > secondLargest && num != largest) {
               secondLargest = num;
           }
       }
       return secondLargest;
   }
   ```

4. **Check if an array is sorted.**
   ```java
   public static boolean isSorted(int[] arr) {
       for (int i = 1; i < arr.length; i++) {
           if (arr[i] < arr[i - 1]) return false;
       }
       return true;
   }
   ```

5. **Move all zeros to the end of an array.**
   ```java
   public static void moveZerosToEnd(int[] arr) {
       int index = 0;
       for (int num : arr) {
           if (num != 0) arr[index++] = num;
       }
       while (index < arr.length) arr[index++] = 0;
   }
   ```

---

#### **Strings**

6. **Reverse a string.**
   ```java
   public static String reverseString(String str) {
       return new StringBuilder(str).reverse().toString();
   }
   ```

7. **Check if a string is a palindrome.**
   ```java
   public static boolean isPalindrome(String str) {
       int start = 0, end = str.length() - 1;
       while (start < end) {
           if (str.charAt(start) != str.charAt(end)) return false;
           start++;
           end--;
       }
       return true;
   }
   ```

8. **Find the first non-repeating character in a string.**
   ```java
   public static char firstNonRepeatingChar(String str) {
       int[] freq = new int[256];
       for (char c : str.toCharArray()) freq[c]++;
       for (char c : str.toCharArray()) {
           if (freq[c] == 1) return c;
       }
       return '\0';
   }
   ```

9. **Check if two strings are anagrams.**
   ```java
   public static boolean areAnagrams(String s1, String s2) {
       char[] arr1 = s1.toCharArray();
       char[] arr2 = s2.toCharArray();
       Arrays.sort(arr1);
       Arrays.sort(arr2);
       return Arrays.equals(arr1, arr2);
   }
   ```

10. **Count vowels and consonants in a string.**
    ```java
    public static int[] countVowelsAndConsonants(String str) {
        int vowels = 0, consonants = 0;
        str = str.toLowerCase();
        for (char c : str.toCharArray()) {
            if ("aeiou".indexOf(c) != -1) vowels++;
            else if (Character.isLetter(c)) consonants++;
        }
        return new int[]{vowels, consonants};
    }
    ```

---

#### **Linked Lists**

11. **Reverse a linked list.**
    ```java
    class Node {
        int data;
        Node next;
        Node(int data) { this.data = data; }
    }
    public static Node reverseLinkedList(Node head) {
        Node prev = null, curr = head, next = null;
        while (curr != null) {
            next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }
        return prev;
    }
    ```

12. **Detect a loop in a linked list.**
    ```java
    public static boolean detectLoop(Node head) {
        Node slow = head, fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) return true;
        }
        return false;
    }
    ```

13. **Merge two sorted linked lists.**
    ```java
    public static Node mergeTwoLists(Node l1, Node l2) {
        Node dummy = new Node(0), curr = dummy;
        while (l1 != null && l2 != null) {
            if (l1.data <= l2.data) {
                curr.next = l1;
                l1 = l1.next;
            } else {
                curr.next = l2;
                l2 = l2.next;
            }
            curr = curr.next;
        }
        curr.next = (l1 != null) ? l1 : l2;
        return dummy.next;
    }
    ```

### **DSA Questions and Answers in Java (Continued)**

#### **Linked Lists (Continued)**

14. **Find the middle element of a linked list.**
    ```java
    public static int findMiddle(Node head) {
        Node slow = head, fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow.data;
    }
    ```

15. **Find the nth node from the end of a linked list.**
    ```java
    public static Node findNthFromEnd(Node head, int n) {
        Node first = head, second = head;
        for (int i = 0; i < n; i++) {
            if (first == null) return null;
            first = first.next;
        }
        while (first != null) {
            first = first.next;
            second = second.next;
        }
        return second;
    }
    ```

16. **Remove duplicates from a sorted linked list.**
    ```java
    public static Node removeDuplicates(Node head) {
        Node current = head;
        while (current != null && current.next != null) {
            if (current.data == current.next.data) {
                current.next = current.next.next;
            } else {
                current = current.next;
            }
        }
        return head;
    }
    ```

17. **Flatten a linked list.**
    ```java
    public static Node flatten(Node head) {
        if (head == null || head.next == null) return head;
        Node temp = flatten(head.next);
        return mergeTwoLists(head, temp);
    }
    ```

18. **Find the length of a linked list.**
    ```java
    public static int findLength(Node head) {
        int length = 0;
        Node current = head;
        while (current != null) {
            length++;
            current = current.next;
        }
        return length;
    }
    ```

---

#### **Stacks**

19. **Implement a stack using arrays.**
    ```java
    class Stack {
        int[] arr;
        int top;
        Stack(int size) {
            arr = new int[size];
            top = -1;
        }
        void push(int value) {
            if (top == arr.length - 1) System.out.println("Stack overflow");
            else arr[++top] = value;
        }
        int pop() {
            if (top == -1) {
                System.out.println("Stack underflow");
                return -1;
            }
            return arr[top--];
        }
        int peek() {
            if (top == -1) return -1;
            return arr[top];
        }
    }
    ```

20. **Implement a stack using two queues.**
    ```java
    class StackUsingQueues {
        Queue<Integer> q1 = new LinkedList<>();
        Queue<Integer> q2 = new LinkedList<>();
        
        void push(int x) {
            q1.add(x);
        }
        
        int pop() {
            if (q1.isEmpty()) return -1;
            while (q1.size() > 1) {
                q2.add(q1.remove());
            }
            int popped = q1.remove();
            Queue<Integer> temp = q1;
            q1 = q2;
            q2 = temp;
            return popped;
        }
    }
    ```

21. **Evaluate an expression using stack (Infix to Postfix).**
    ```java
    public static int evaluatePostfix(String expression) {
        Stack<Integer> stack = new Stack<>();
        for (char c : expression.toCharArray()) {
            if (Character.isDigit(c)) {
                stack.push(c - '0');
            } else {
                int b = stack.pop();
                int a = stack.pop();
                switch (c) {
                    case '+': stack.push(a + b); break;
                    case '-': stack.push(a - b); break;
                    case '*': stack.push(a * b); break;
                    case '/': stack.push(a / b); break;
                }
            }
        }
        return stack.pop();
    }
    ```

22. **Check for balanced parentheses using a stack.**
    ```java
    public static boolean isBalanced(String str) {
        Stack<Character> stack = new Stack<>();
        for (char c : str.toCharArray()) {
            if (c == '(') stack.push(c);
            else if (c == ')') {
                if (stack.isEmpty()) return false;
                stack.pop();
            }
        }
        return stack.isEmpty();
    }
    ```

---

#### **Queues**

23. **Implement a queue using two stacks.**
    ```java
    class QueueUsingStacks {
        Stack<Integer> stack1 = new Stack<>();
        Stack<Integer> stack2 = new Stack<>();
        
        void enqueue(int x) {
            stack1.push(x);
        }
        
        int dequeue() {
            if (stack2.isEmpty()) {
                if (stack1.isEmpty()) return -1;
                while (!stack1.isEmpty()) {
                    stack2.push(stack1.pop());
                }
            }
            return stack2.pop();
        }
    }
    ```

24. **Implement a circular queue.**
    ```java
    class CircularQueue {
        int[] arr;
        int front, rear, size;
        CircularQueue(int capacity) {
            arr = new int[capacity];
            front = -1;
            rear = -1;
            size = capacity;
        }
        void enqueue(int value) {
            if ((rear + 1) % size == front) System.out.println("Queue is full");
            else {
                if (front == -1) front = 0;
                rear = (rear + 1) % size;
                arr[rear] = value;
            }
        }
        int dequeue() {
            if (front == -1) return -1;
            int value = arr[front];
            if (front == rear) front = rear = -1;
            else front = (front + 1) % size;
            return value;
        }
    }
    ```

25. **Implement priority queue using a heap.**
    ```java
    class PriorityQueueExample {
        PriorityQueue<Integer> pq = new PriorityQueue<>();
        
        void enqueue(int value) {
            pq.add(value);
        }
        
        int dequeue() {
            return pq.isEmpty() ? -1 : pq.poll();
        }
    }
    ```

### **DSA Questions and Answers in Java (Continued)**

#### **Logical Problems**

26. **Find the missing number in an array of 1 to N.**
   ```java
   public static int findMissingNumber(int[] arr, int n) {
       int totalSum = n * (n + 1) / 2;
       int sumOfArray = 0;
       for (int num : arr) {
           sumOfArray += num;
       }
       return totalSum - sumOfArray;
   }
   ```

27. **Find the factorial of a number using recursion.**
   ```java
   public static int factorial(int n) {
       if (n == 0) return 1;
       return n * factorial(n - 1);
   }
   ```

28. **Find the GCD (Greatest Common Divisor) of two numbers.**
   ```java
   public static int gcd(int a, int b) {
       if (b == 0) return a;
       return gcd(b, a % b);
   }
   ```

29. **Find the sum of digits of a number.**
   ```java
   public static int sumOfDigits(int num) {
       int sum = 0;
       while (num > 0) {
           sum += num % 10;
           num /= 10;
       }
       return sum;
   }
   ```

30. **Check if a number is prime.**
   ```java
   public static boolean isPrime(int num) {
       if (num <= 1) return false;
       for (int i = 2; i * i <= num; i++) {
           if (num % i == 0) return false;
       }
       return true;
   }
   ```

31. **Find the sum of the first N natural numbers.**
   ```java
   public static int sumOfNaturalNumbers(int n) {
       return n * (n + 1) / 2;
   }
   ```

32. **Count the number of set bits in an integer.**
   ```java
   public static int countSetBits(int num) {
       int count = 0;
       while (num > 0) {
           count += num & 1;
           num >>= 1;
       }
       return count;
   }
   ```

33. **Find the power of a number using recursion.**
   ```java
   public static int power(int base, int exp) {
       if (exp == 0) return 1;
       return base * power(base, exp - 1);
   }
   ```

34. **Find the Armstrong number (Narcissistic number) for a given number of digits.**
   ```java
   public static boolean isArmstrong(int num) {
       int sum = 0, temp = num, digits = (int) Math.log10(num) + 1;
       while (temp > 0) {
           sum += Math.pow(temp % 10, digits);
           temp /= 10;
       }
       return sum == num;
   }
   ```

35. **Check if a number is a perfect number.**
   ```java
   public static boolean isPerfectNumber(int num) {
       int sum = 0;
       for (int i = 1; i <= num / 2; i++) {
           if (num % i == 0) sum += i;
       }
       return sum == num;
   }
   ```

---

#### **Arrays (Continued)**

36. **Find the maximum product of two integers in an array.**
   ```java
   public static int maxProduct(int[] arr) {
       int max = Integer.MIN_VALUE, secondMax = Integer.MIN_VALUE;
       int min = Integer.MAX_VALUE, secondMin = Integer.MAX_VALUE;
       for (int num : arr) {
           if (num > max) {
               secondMax = max;
               max = num;
           } else if (num > secondMax) {
               secondMax = num;
           }
           if (num < min) {
               secondMin = min;
               min = num;
           } else if (num < secondMin) {
               secondMin = num;
           }
       }
       return Math.max(max * secondMax, min * secondMin);
   }
   ```

37. **Find the longest increasing subsequence in an array.**
   ```java
   public static int longestIncreasingSubsequence(int[] arr) {
       int n = arr.length;
       int[] lis = new int[n];
       Arrays.fill(lis, 1);
       for (int i = 1; i < n; i++) {
           for (int j = 0; j < i; j++) {
               if (arr[i] > arr[j] && lis[i] < lis[j] + 1) {
                   lis[i] = lis[j] + 1;
               }
           }
       }
       return Arrays.stream(lis).max().getAsInt();
   }
   ```

38. **Find the majority element in an array (element that appears more than n/2 times).**
   ```java
   public static int findMajorityElement(int[] arr) {
       int count = 0, candidate = -1;
       for (int num : arr) {
           if (count == 0) candidate = num;
           count += (num == candidate) ? 1 : -1;
       }
       return candidate;
   }
   ```

39. **Find the intersection of two arrays.**
   ```java
   public static int[] findIntersection(int[] arr1, int[] arr2) {
       Set<Integer> set = new HashSet<>();
       for (int num : arr1) set.add(num);
       List<Integer> intersection = new ArrayList<>();
       for (int num : arr2) {
           if (set.contains(num)) {
               intersection.add(num);
               set.remove(num);
           }
       }
       return intersection.stream().mapToInt(i -> i).toArray();
   }
   ```

40. **Rotate an array by K positions.**
   ```java
   public static void rotateArray(int[] arr, int k) {
       int n = arr.length;
       k = k % n; // In case k is larger than n
       reverseArray(arr, 0, n - 1);
       reverseArray(arr, 0, k - 1);
       reverseArray(arr, k, n - 1);
   }

   private static void reverseArray(int[] arr, int start, int end) {
       while (start < end) {
           int temp = arr[start];
           arr[start] = arr[end];
           arr[end] = temp;
           start++;
           end--;
       }
   }
   ```

---

#### **Stacks (Continued)**

41. **Sort a stack using recursion.**
   ```java
   public static void sortStack(Stack<Integer> stack) {
       if (stack.isEmpty()) return;
       int temp = stack.pop();
       sortStack(stack);
       insertSorted(stack, temp);
   }

   private static void insertSorted(Stack<Integer> stack, int temp) {
       if (stack.isEmpty() || stack.peek() <= temp) {
           stack.push(temp);
           return;
       }
       int val = stack.pop();
       insertSorted(stack, temp);
       stack.push(val);
   }
   ```

42. **Check if parentheses are balanced using a stack.**
   ```java
   public static boolean isParenthesesBalanced(String expr) {
       Stack<Character> stack = new Stack<>();
       for (char c : expr.toCharArray()) {
           if (c == '(' || c == '[' || c == '{') {
               stack.push(c);
           } else if (c == ')' && !stack.isEmpty() && stack.peek() == '(') {
               stack.pop();
           } else if (c == ']' && !stack.isEmpty() && stack.peek() == '[') {
               stack.pop();
           } else if (c == '}' && !stack.isEmpty() && stack.peek() == '{') {
               stack.pop();
           } else {
               return false;
           }
       }
       return stack.isEmpty();
   }
   ```
### **DSA Questions and Answers in Java (Continued)**

#### **Queues (Continued)**

43. **Implement a queue using a linked list.**
   ```java
   class QueueUsingLinkedList {
       Node front, rear;

       class Node {
           int data;
           Node next;
           Node(int data) { this.data = data; }
       }

       QueueUsingLinkedList() {
           front = rear = null;
       }

       void enqueue(int data) {
           Node newNode = new Node(data);
           if (rear == null) {
               front = rear = newNode;
               return;
           }
           rear.next = newNode;
           rear = newNode;
       }

       int dequeue() {
           if (front == null) return -1;
           int data = front.data;
           front = front.next;
           if (front == null) rear = null;
           return data;
       }
   }
   ```

44. **Implement a circular queue using arrays.**
   ```java
   class CircularQueue {
       int[] arr;
       int front, rear, size;

       CircularQueue(int capacity) {
           arr = new int[capacity];
           front = rear = -1;
           size = capacity;
       }

       void enqueue(int value) {
           if ((rear + 1) % size == front) System.out.println("Queue is full");
           else {
               if (front == -1) front = 0;
               rear = (rear + 1) % size;
               arr[rear] = value;
           }
       }

       int dequeue() {
           if (front == -1) return -1;
           int value = arr[front];
           if (front == rear) front = rear = -1;
           else front = (front + 1) % size;
           return value;
       }
   }
   ```

45. **Find the size of a queue (using an array implementation).**
   ```java
   public static int getQueueSize(int[] queue, int front, int rear, int size) {
       if (front == -1) return 0;
       if (rear >= front) return rear - front + 1;
       return size - front + rear + 1;
   }
   ```

---

#### **Strings (Continued)**

46. **Find the longest common prefix of an array of strings.**
   ```java
   public static String longestCommonPrefix(String[] strs) {
       if (strs.length == 0) return "";
       String prefix = strs[0];
       for (int i = 1; i < strs.length; i++) {
           while (strs[i].indexOf(prefix) != 0) {
               prefix = prefix.substring(0, prefix.length() - 1);
               if (prefix.isEmpty()) return "";
           }
       }
       return prefix;
   }
   ```

47. **Check if a string has all unique characters.**
   ```java
   public static boolean hasUniqueChars(String str) {
       Set<Character> set = new HashSet<>();
       for (char c : str.toCharArray()) {
           if (!set.add(c)) return false;
       }
       return true;
   }
   ```

48. **Find the longest substring without repeating characters.**
   ```java
   public static int longestSubstringWithoutRepeatingChars(String s) {
       Set<Character> set = new HashSet<>();
       int left = 0, maxLength = 0;
       for (int right = 0; right < s.length(); right++) {
           while (set.contains(s.charAt(right))) {
               set.remove(s.charAt(left));
               left++;
           }
           set.add(s.charAt(right));
           maxLength = Math.max(maxLength, right - left + 1);
       }
       return maxLength;
   }
   ```

49. **Count the number of substrings with exactly K distinct characters.**
   ```java
   public static int countSubstringsWithKDistinctChars(String s, int k) {
       return atMostKDistinctChars(s, k) - atMostKDistinctChars(s, k - 1);
   }

   private static int atMostKDistinctChars(String s, int k) {
       int count = 0;
       Map<Character, Integer> map = new HashMap<>();
       int left = 0;
       for (int right = 0; right < s.length(); right++) {
           map.put(s.charAt(right), map.getOrDefault(s.charAt(right), 0) + 1);
           while (map.size() > k) {
               map.put(s.charAt(left), map.get(s.charAt(left)) - 1);
               if (map.get(s.charAt(left)) == 0) map.remove(s.charAt(left));
               left++;
           }
           count += right - left + 1;
       }
       return count;
   }
   ```

50. **Find the first unique character in a string.**
   ```java
   public static char firstUniqChar(String s) {
       int[] count = new int[256];
       for (char c : s.toCharArray()) {
           count[c]++;
       }
       for (char c : s.toCharArray()) {
           if (count[c] == 1) return c;
       }
       return '\0';
   }
   ```

---

#### **Arrays (Continued)**

51. **Find the equilibrium index of an array.**
   ```java
   public static int findEquilibriumIndex(int[] arr) {
       int totalSum = 0, leftSum = 0;
       for (int num : arr) totalSum += num;
       for (int i = 0; i < arr.length; i++) {
           totalSum -= arr[i];
           if (leftSum == totalSum) return i;
           leftSum += arr[i];
       }
       return -1;
   }
   ```

52. **Find the subarray with the maximum sum (Kadane's algorithm).**
   ```java
   public static int maxSubArraySum(int[] arr) {
       int maxSum = arr[0], currentSum = arr[0];
       for (int i = 1; i < arr.length; i++) {
           currentSum = Math.max(arr[i], currentSum + arr[i]);
           maxSum = Math.max(maxSum, currentSum);
       }
       return maxSum;
   }
   ```

53. **Find the union of two arrays.**
   ```java
   public static int[] findUnion(int[] arr1, int[] arr2) {
       Set<Integer> set = new HashSet<>();
       for (int num : arr1) set.add(num);
       for (int num : arr2) set.add(num);
       int[] result = new int[set.size()];
       int i = 0;
       for (int num : set) result[i++] = num;
       return result;
   }
   ```

54. **Find the intersection of two arrays.**
   ```java
   public static int[] findIntersection(int[] arr1, int[] arr2) {
       Set<Integer> set1 = new HashSet<>();
       for (int num : arr1) set1.add(num);
       Set<Integer> intersection = new HashSet<>();
       for (int num : arr2) {
           if (set1.contains(num)) intersection.add(num);
       }
       int[] result = new int[intersection.size()];
       int i = 0;
       for (int num : intersection) result[i++] = num;
       return result;
   }
   ```

55. **Find the common elements in three sorted arrays.**
   ```java
   public static List<Integer> findCommonElements(int[] arr1, int[] arr2, int[] arr3) {
       List<Integer> result = new ArrayList<>();
       int i = 0, j = 0, k = 0;
       while (i < arr1.length && j < arr2.length && k < arr3.length) {
           if (arr1[i] == arr2[j] && arr2[j] == arr3[k]) {
               result.add(arr1[i]);
               i++;
               j++;
               k++;
           } else if (arr1[i] < arr2[j]) i++;
           else if (arr2[j] < arr3[k]) j++;
           else k++;
       }
       return result;
   }
   ```
### **DSA Questions and Answers in Java (Continued)**

#### **Linked Lists (Continued)**

56. **Reverse a linked list.**
   ```java
   class Node {
       int data;
       Node next;
       Node(int data) { this.data = data; }
   }

   public static Node reverseLinkedList(Node head) {
       Node prev = null, current = head, next = null;
       while (current != null) {
           next = current.next;
           current.next = prev;
           prev = current;
           current = next;
       }
       return prev;
   }
   ```

57. **Detect a cycle in a linked list (Floyd's Tortoise and Hare algorithm).**
   ```java
   public static boolean hasCycle(Node head) {
       Node slow = head, fast = head;
       while (fast != null && fast.next != null) {
           slow = slow.next;
           fast = fast.next.next;
           if (slow == fast) return true;
       }
       return false;
   }
   ```

58. **Find the middle element of a linked list.**
   ```java
   public static Node findMiddle(Node head) {
       if (head == null) return null;
       Node slow = head, fast = head;
       while (fast != null && fast.next != null) {
           slow = slow.next;
           fast = fast.next.next;
       }
       return slow;
   }
   ```

59. **Merge two sorted linked lists.**
   ```java
   public static Node mergeSortedLists(Node list1, Node list2) {
       if (list1 == null) return list2;
       if (list2 == null) return list1;
       if (list1.data < list2.data) {
           list1.next = mergeSortedLists(list1.next, list2);
           return list1;
       } else {
           list2.next = mergeSortedLists(list1, list2.next);
           return list2;
       }
   }
   ```

60. **Remove the nth node from the end of a linked list.**
   ```java
   public static Node removeNthFromEnd(Node head, int n) {
       Node fast = head, slow = head;
       for (int i = 0; i < n; i++) {
           if (fast == null) return null;
           fast = fast.next;
       }
       if (fast == null) return head.next;
       while (fast.next != null) {
           fast = fast.next;
           slow = slow.next;
       }
       slow.next = slow.next.next;
       return head;
   }
   ```

---

#### **Stacks (Continued)**

61. **Implement a stack using two queues.**
   ```java
   class StackUsingQueues {
       Queue<Integer> q1 = new LinkedList<>();
       Queue<Integer> q2 = new LinkedList<>();

       void push(int x) {
           q2.add(x);
           while (!q1.isEmpty()) {
               q2.add(q1.poll());
           }
           Queue<Integer> temp = q1;
           q1 = q2;
           q2 = temp;
       }

       int pop() {
           if (q1.isEmpty()) return -1;
           return q1.poll();
       }

       int top() {
           if (q1.isEmpty()) return -1;
           return q1.peek();
       }

       boolean isEmpty() {
           return q1.isEmpty();
       }
   }
   ```

62. **Implement a stack with a minimum element.**
   ```java
   class StackWithMin {
       private Stack<Integer> stack = new Stack<>();
       private Stack<Integer> minStack = new Stack<>();

       void push(int value) {
           stack.push(value);
           if (minStack.isEmpty() || value <= minStack.peek()) {
               minStack.push(value);
           }
       }

       int pop() {
           int value = stack.pop();
           if (value == minStack.peek()) {
               minStack.pop();
           }
           return value;
       }

       int getMin() {
           return minStack.peek();
       }
   }
   ```

63. **Evaluate a postfix expression.**
   ```java
   public static int evaluatePostfix(String expr) {
       Stack<Integer> stack = new Stack<>();
       for (char c : expr.toCharArray()) {
           if (Character.isDigit(c)) {
               stack.push(c - '0');
           } else {
               int operand2 = stack.pop();
               int operand1 = stack.pop();
               switch (c) {
                   case '+': stack.push(operand1 + operand2); break;
                   case '-': stack.push(operand1 - operand2); break;
                   case '*': stack.push(operand1 * operand2); break;
                   case '/': stack.push(operand1 / operand2); break;
               }
           }
       }
       return stack.pop();
   }
   ```

64. **Evaluate a prefix expression.**
   ```java
   public static int evaluatePrefix(String expr) {
       Stack<Integer> stack = new Stack<>();
       for (int i = expr.length() - 1; i >= 0; i--) {
           char c = expr.charAt(i);
           if (Character.isDigit(c)) {
               stack.push(c - '0');
           } else {
               int operand1 = stack.pop();
               int operand2 = stack.pop();
               switch (c) {
                   case '+': stack.push(operand1 + operand2); break;
                   case '-': stack.push(operand1 - operand2); break;
                   case '*': stack.push(operand1 * operand2); break;
                   case '/': stack.push(operand1 / operand2); break;
               }
           }
       }
       return stack.pop();
   }
   ```

65. **Check for balanced parentheses using a stack.**
   ```java
   public static boolean isBalanced(String expr) {
       Stack<Character> stack = new Stack<>();
       for (char c : expr.toCharArray()) {
           if (c == '(' || c == '[' || c == '{') {
               stack.push(c);
           } else {
               if (stack.isEmpty()) return false;
               char top = stack.pop();
               if (c == ')' && top != '(' || c == ']' && top != '[' || c == '}' && top != '{') {
                   return false;
               }
           }
       }
       return stack.isEmpty();
   }
   ```

---

#### **Queues (Continued)**

66. **Implement a priority queue (using a heap).**
   ```java
   class PriorityQueueExample {
       private PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());

       void add(int element) {
           pq.add(element);
       }

       int remove() {
           return pq.poll();
       }

       int peek() {
           return pq.peek();
       }

       boolean isEmpty() {
           return pq.isEmpty();
       }
   }
   ```

67. **Implement a queue using two stacks.**
   ```java
   class QueueUsingTwoStacks {
       private Stack<Integer> stack1 = new Stack<>();
       private Stack<Integer> stack2 = new Stack<>();

       void enqueue(int value) {
           stack1.push(value);
       }

       int dequeue() {
           if (stack2.isEmpty()) {
               while (!stack1.isEmpty()) {
                   stack2.push(stack1.pop());
               }
           }
           if (stack2.isEmpty()) {
               return -1;
           }
           return stack2.pop();
       }
   }
   ```

68. **Check if a given queue is palindrome.**
   ```java
   public static boolean isPalindromeQueue(Queue<Integer> queue) {
       Stack<Integer> stack = new Stack<>();
       Queue<Integer> tempQueue = new LinkedList<>();
       while (!queue.isEmpty()) {
           int value = queue.poll();
           stack.push(value);
           tempQueue.add(value);
       }

       while (!tempQueue.isEmpty()) {
           if (tempQueue.poll() != stack.pop()) {
               return false;
           }
       }
       return true;
   }
   ```
It looks like you’re getting ready for some serious interviews, especially with the AT&T drive coming up! If you're focusing on algorithms and data structures, you're on the right track. Here’s the continuation of the questions:

---

#### **Arrays (Continued)**

69. **Find the longest increasing subsequence in an array.**
   ```java
   public static int longestIncreasingSubsequence(int[] arr) {
       int n = arr.length;
       int[] dp = new int[n];
       Arrays.fill(dp, 1);
       for (int i = 1; i < n; i++) {
           for (int j = 0; j < i; j++) {
               if (arr[i] > arr[j]) {
                   dp[i] = Math.max(dp[i], dp[j] + 1);
               }
           }
       }
       return Arrays.stream(dp).max().getAsInt();
   }
   ```

70. **Find the first missing positive integer.**
   ```java
   public static int firstMissingPositive(int[] nums) {
       int n = nums.length;
       for (int i = 0; i < n; i++) {
           while (nums[i] > 0 && nums[i] <= n && nums[nums[i] - 1] != nums[i]) {
               int temp = nums[nums[i] - 1];
               nums[nums[i] - 1] = nums[i];
               nums[i] = temp;
           }
       }
       for (int i = 0; i < n; i++) {
           if (nums[i] != i + 1) return i + 1;
       }
       return n + 1;
   }
   ```

71. **Sort an array of 0s, 1s, and 2s (Dutch National Flag Problem).**
   ```java
   public static void sortColors(int[] nums) {
       int low = 0, mid = 0, high = nums.length - 1;
       while (mid <= high) {
           if (nums[mid] == 0) {
               swap(nums, low++, mid++);
           } else if (nums[mid] == 1) {
               mid++;
           } else {
               swap(nums, mid, high--);
           }
       }
   }

   private static void swap(int[] nums, int i, int j) {
       int temp = nums[i];
       nums[i] = nums[j];
       nums[j] = temp;
   }
   ```

72. **Find the majority element in an array (Boyer-Moore Voting Algorithm).**
   ```java
   public static int majorityElement(int[] nums) {
       int candidate = nums[0], count = 1;
       for (int i = 1; i < nums.length; i++) {
           if (nums[i] == candidate) count++;
           else count--;
           if (count == 0) {
               candidate = nums[i];
               count = 1;
           }
       }
       return candidate;
   }
   ```

---

#### **Linked Lists (Continued)**

73. **Reverse a linked list in groups of size k.**
   ```java
   public static Node reverseKGroup(Node head, int k) {
       Node current = head;
       int count = 0;
       while (current != null && count != k) {
           current = current.next;
           count++;
       }
       if (count == k) {
           current = reverseKGroup(current, k);
           while (count-- > 0) {
               Node temp = head.next;
               head.next = current;
               current = head;
               head = temp;
           }
           head = current;
       }
       return head;
   }
   ```

74. **Flatten a linked list (next pointer and child pointer).**
   ```java
   public static Node flatten(Node head) {
       if (head == null) return null;
       Node temp = head.next;
       if (head.child != null) {
           head.next = flatten(head.child);
           head.child = null;
       }
       if (head.next != null) {
           temp = flatten(temp);
           head.next = temp;
       }
       return head;
   }
   ```

---

#### **Stacks (Continued)**

75. **Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.**
   ```java
   class MinStack {
       private Stack<Integer> stack = new Stack<>();
       private Stack<Integer> minStack = new Stack<>();

       public void push(int val) {
           stack.push(val);
           if (minStack.isEmpty() || val <= minStack.peek()) {
               minStack.push(val);
           }
       }

       public void pop() {
           if (stack.peek().equals(minStack.peek())) {
               minStack.pop();
           }
           stack.pop();
       }

       public int top() {
           return stack.peek();
       }

       public int getMin() {
           return minStack.peek();
       }
   }
   ```

76. **Implement a stack using a linked list.**
   ```java
   class StackLinkedList {
       private Node top;

       class Node {
           int data;
           Node next;
           Node(int data) { this.data = data; }
       }

       public void push(int data) {
           Node newNode = new Node(data);
           newNode.next = top;
           top = newNode;
       }

       public int pop() {
           if (top == null) return -1;
           int data = top.data;
           top = top.next;
           return data;
       }

       public int peek() {
           return top != null ? top.data : -1;
       }
   }
   ```

---

#### **Queues (Continued)**

77. **Implement a deque (double-ended queue) using two stacks.**
   ```java
   class DequeUsingTwoStacks {
       private Stack<Integer> stack1 = new Stack<>();
       private Stack<Integer> stack2 = new Stack<>();

       void pushFront(int x) {
           stack1.push(x);
       }

       void pushRear(int x) {
           stack2.push(x);
       }

       int popFront() {
           if (stack1.isEmpty()) return -1;
           return stack1.pop();
       }

       int popRear() {
           if (stack2.isEmpty()) return -1;
           return stack2.pop();
       }
   }
   ```

---

#### **General Algorithms**

78. **Find the largest rectangle in a histogram.**
   ```java
   public static int largestRectangleArea(int[] heights) {
       Stack<Integer> stack = new Stack<>();
       int maxArea = 0, index = 0;
       while (index < heights.length) {
           if (stack.isEmpty() || heights[index] >= heights[stack.peek()]) {
               stack.push(index++);
           } else {
               int topOfStack = stack.pop();
               int area = heights[topOfStack] * (stack.isEmpty() ? index : index - stack.peek() - 1);
               maxArea = Math.max(maxArea, area);
           }
       }
       while (!stack.isEmpty()) {
           int topOfStack = stack.pop();
           int area = heights[topOfStack] * (stack.isEmpty() ? index : index - stack.peek() - 1);
           maxArea = Math.max(maxArea, area);
       }
       return maxArea;
   }
   ```

79. **Find all prime numbers up to a given number (Sieve of Eratosthenes).**
   ```java
   public static void sieveOfEratosthenes(int n) {
       boolean[] prime = new boolean[n + 1];
       Arrays.fill(prime, true);
       prime[0] = prime[1] = false;
       for (int p = 2; p * p <= n; p++) {
           if (prime[p]) {
               for (int i = p * p; i <= n; i += p) {
                   prime[i] = false;
               }
           }
       }
       for (int i = 2; i <= n; i++) {
           if (prime[i]) System.out.print(i + " ");
       }
   }
   ```

80. **Find the kth largest element in an array.**
   ```java
   public static int findKthLargest(int[] nums, int k) {
       PriorityQueue<Integer> pq = new PriorityQueue<>();
       for (int num : nums) {
           pq.add(num);
           if (pq.size() > k) pq.poll();
       }
       return pq.peek();
   }
   ```
### **DSA Questions and Answers in Java (Continued)**

#### **Trees (Continued)**

69. **Inorder traversal of a binary tree.**
   ```java
   class TreeNode {
       int data;
       TreeNode left, right;

       TreeNode(int data) {
           this.data = data;
           left = right = null;
       }
   }

   public static void inorderTraversal(TreeNode root) {
       if (root != null) {
           inorderTraversal(root.left);
           System.out.print(root.data + " ");
           inorderTraversal(root.right);
       }
   }
   ```

70. **Preorder traversal of a binary tree.**
   ```java
   public static void preorderTraversal(TreeNode root) {
       if (root != null) {
           System.out.print(root.data + " ");
           preorderTraversal(root.left);
           preorderTraversal(root.right);
       }
   }
   ```

71. **Postorder traversal of a binary tree.**
   ```java
   public static void postorderTraversal(TreeNode root) {
       if (root != null) {
           postorderTraversal(root.left);
           postorderTraversal(root.right);
           System.out.print(root.data + " ");
       }
   }
   ```

72. **Level order traversal of a binary tree.**
   ```java
   public static void levelOrderTraversal(TreeNode root) {
       if (root == null) return;
       Queue<TreeNode> queue = new LinkedList<>();
       queue.offer(root);
       while (!queue.isEmpty()) {
           TreeNode node = queue.poll();
           System.out.print(node.data + " ");
           if (node.left != null) queue.offer(node.left);
           if (node.right != null) queue.offer(node.right);
       }
   }
   ```

73. **Check if a binary tree is balanced.**
   ```java
   public static boolean isBalanced(TreeNode root) {
       return height(root) != -1;
   }

   private static int height(TreeNode node) {
       if (node == null) return 0;
       int leftHeight = height(node.left);
       int rightHeight = height(node.right);
       if (leftHeight == -1 || rightHeight == -1 || Math.abs(leftHeight - rightHeight) > 1)
           return -1;
       return Math.max(leftHeight, rightHeight) + 1;
   }
   ```

74. **Find the height of a binary tree.**
   ```java
   public static int height(TreeNode root) {
       if (root == null) return 0;
       int leftHeight = height(root.left);
       int rightHeight = height(root.right);
       return Math.max(leftHeight, rightHeight) + 1;
   }
   ```

75. **Find the diameter of a binary tree.**
   ```java
   public static int diameter(TreeNode root) {
       int[] maxDiameter = new int[1];
       heightAndDiameter(root, maxDiameter);
       return maxDiameter[0];
   }

   private static int heightAndDiameter(TreeNode node, int[] maxDiameter) {
       if (node == null) return 0;
       int leftHeight = heightAndDiameter(node.left, maxDiameter);
       int rightHeight = heightAndDiameter(node.right, maxDiameter);
       maxDiameter[0] = Math.max(maxDiameter[0], leftHeight + rightHeight);
       return Math.max(leftHeight, rightHeight) + 1;
   }
   ```

76. **Check if a binary tree is a valid binary search tree (BST).**
   ```java
   public static boolean isValidBST(TreeNode root) {
       return isValidBST(root, Long.MIN_VALUE, Long.MAX_VALUE);
   }

   private static boolean isValidBST(TreeNode node, long min, long max) {
       if (node == null) return true;
       if (node.data <= min || node.data >= max) return false;
       return isValidBST(node.left, min, node.data) && isValidBST(node.right, node.data, max);
   }
   ```

---

#### **Graphs (Continued)**

77. **Implement Depth-First Search (DFS) for a graph.**
   ```java
   class Graph {
       private Map<Integer, List<Integer>> adjList = new HashMap<>();

       void addEdge(int v, int w) {
           adjList.computeIfAbsent(v, k -> new ArrayList<>()).add(w);
       }

       public void dfs(int start) {
           Set<Integer> visited = new HashSet<>();
           dfsUtil(start, visited);
       }

       private void dfsUtil(int v, Set<Integer> visited) {
           visited.add(v);
           System.out.print(v + " ");
           for (int neighbor : adjList.getOrDefault(v, Collections.emptyList())) {
               if (!visited.contains(neighbor)) {
                   dfsUtil(neighbor, visited);
               }
           }
       }
   }
   ```

78. **Implement Breadth-First Search (BFS) for a graph.**
   ```java
   class Graph {
       private Map<Integer, List<Integer>> adjList = new HashMap<>();

       void addEdge(int v, int w) {
           adjList.computeIfAbsent(v, k -> new ArrayList<>()).add(w);
       }

       public void bfs(int start) {
           Set<Integer> visited = new HashSet<>();
           Queue<Integer> queue = new LinkedList<>();
           queue.add(start);
           visited.add(start);

           while (!queue.isEmpty()) {
               int node = queue.poll();
               System.out.print(node + " ");
               for (int neighbor : adjList.getOrDefault(node, Collections.emptyList())) {
                   if (!visited.contains(neighbor)) {
                       visited.add(neighbor);
                       queue.add(neighbor);
                   }
               }
           }
       }
   }
   ```

79. **Find the shortest path in an unweighted graph (using BFS).**
   ```java
   class Graph {
       private Map<Integer, List<Integer>> adjList = new HashMap<>();

       void addEdge(int v, int w) {
           adjList.computeIfAbsent(v, k -> new ArrayList<>()).add(w);
       }

       public void shortestPath(int start, int target) {
           Map<Integer, Integer> distance = new HashMap<>();
           Queue<Integer> queue = new LinkedList<>();
           queue.add(start);
           distance.put(start, 0);

           while (!queue.isEmpty()) {
               int node = queue.poll();
               if (node == target) {
                   System.out.println("Shortest path length: " + distance.get(node));
                   return;
               }
               for (int neighbor : adjList.getOrDefault(node, Collections.emptyList())) {
                   if (!distance.containsKey(neighbor)) {
                       distance.put(neighbor, distance.get(node) + 1);
                       queue.add(neighbor);
                   }
               }
           }
       }
   }
   ```

80. **Detect a cycle in a directed graph (using DFS).**
   ```java
   class Graph {
       private Map<Integer, List<Integer>> adjList = new HashMap<>();

       void addEdge(int v, int w) {
           adjList.computeIfAbsent(v, k -> new ArrayList<>()).add(w);
       }

       public boolean hasCycle() {
           Set<Integer> visited = new HashSet<>();
           Set<Integer> recursionStack = new HashSet<>();
           for (int node : adjList.keySet()) {
               if (dfsCycle(node, visited, recursionStack)) {
                   return true;
               }
           }
           return false;
       }

       private boolean dfsCycle(int node, Set<Integer> visited, Set<Integer> recursionStack) {
           if (recursionStack.contains(node)) return true;
           if (visited.contains(node)) return false;

           visited.add(node);
           recursionStack.add(node);

           for (int neighbor : adjList.getOrDefault(node, Collections.emptyList())) {
               if (dfsCycle(neighbor, visited, recursionStack)) return true;
           }

           recursionStack.remove(node);
           return false;
       }
   }
   ```

---

This concludes the set of **80 DSA questions and answers** covering a variety of topics, from **arrays** to **graphs**, including code snippets.