### HashMap

```java
HashMap<Integer, Integer> map = new HashMap<>();
map.put("key", "value");
map.containsKey("key");
```

### PriorityQueue

* 优先队列

```java
PriorityQueue<Integer> MinQueue = new PriorityQueue<>(); // 小根堆
PriorityQueue<Integer> MaxQueue = new PriorityQueue<>(new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                return o2 - o1;
            }
        }); // 大根堆

peek()//返回队首元素
poll()//返回队首元素，队首元素出队列
offer()//添加元素
size()//返回队列元素个数
isEmpty()//判断队列是否为空，为空返回true,不空返回false
```

