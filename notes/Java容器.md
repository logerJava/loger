
## Java 容器

- [List](#list)
  * [ArrayList](#arraylist)
  * [LinkedList](#linkedlist)
  * [Vector](#vector)
- [Map](#map)
  * [HashMap](#hashmap)
  * [ConcurrentHashMap](#concurrenthashmap)
- [Set](#set)
  * [HashSet](#hashset)
  * [TreeSet](#treeset)

## List

### ArrayList

- 数据结构 : 数组
- 查找访问效率高, 增删效率低, 需要进行 navite 方法的数组拷贝复制
- 默认数组大小 : 10, 每次扩容为原来的 1.5 倍
- ArrayList 存在指定 index 新增与直接新增, 在新增前会有一步校验长度的判断 ensureCapacityInternal, 如果长度不够需要扩容
- ArrayList线程不安全, 线程安全版本的数组容器是Vector
- 与 LinkedList 遍历效率对比, 性能高很多, ArrayList 遍历最大的优势在于内存的连续性，CPU 的内部缓存结构会缓存连续的内存片段，可以大幅降低读取内存的性能开销

### LinkedList

- 数据结构: 双向链表, 既可以向前遍历也可以向后遍历
- 因为链表的结构，插入、删除操作速度很快，而也是因为链表的结构随机访问速度会变慢，需要指针一点点进行移动

### Vector

- 数据结构 : 数组
- Vector 的所有方法均为 synchronized 修饰，性能损耗较大
- Vector 初始 length 是 10 超过 length 时 以 100% 比率增长，相比于 ArrayList 更多消耗内存

## Map

### HashMap

- JDK 1.7
  - 数据结构: 数组 + 链表
  - 头插法 : 新来的值会取代原有的值，原有的值就顺推到链表中去
  - JDK 1.7 在多线程操作HashMap时可能引起死循环，原因是扩容转移后前后链表顺序倒置，在转移过程中修改了原来链表中节点的引用关系, 可能形成环形链表
- JDK 1.8
  - 数据结构: 数组+链表+红黑树 
  - HashMap 中的链表大小超过八个时会自动转化为红黑树，当删除小于六时重新变为链表
    - 根据泊松分布，在负载因子默认为0.75的时候，单个hash槽内元素个数为8的概率小于百万分之一，所以将7作为一个分水岭，等于7的时候不转换，大于等于8的时候才进行转换，小于等于6的时候就化为链表
  - 尾插法
  - JDK 1.8 在同样的前提下并不会引起死循环，原因是扩容转移后前后链表顺序不变，保持之前节点的引用关系
- LoadFactory 默认0.75
- 扩容
  - 创建一个新的 Entry 空数组，长度是原数组的 2 倍
  - 遍历原 Entry 数组，把所有的 Entry 重新 Hash 到新数组(ReHash)
- 为什么要ReHash而不进行复制 ? 
  - 因为长度扩大以后，Hash的规则也随之改变
  - Hash的公式 : `index = HashCode(Key) & (Length - 1)` 原来长度 `(Length)` 是 8 位运算出来的值是 2, 新的长度是 16 位运算出来的值不同
- 线程不安全
  - HashMap 源码中 put/get 方法都没有加同步锁, 无法保证上一秒 put 的值，下一秒 get 的时候还是原值，所以线程安全无法保证
- 初始化
  - 创建 HashMap 时最好赋初始值, 而且最好为 2 的幂, 为了位运算的方便
  - 默认初始化大小为16
    - 实现均匀分布, 在使用不是 2 的幂的数字的时候，`Length-1` 的值是所有二进制位全为 1，这种情况下，index 的结果等同于 HashCode 后几位的值, 只要输入的 HashCode 本身分布均匀，Hash 算法的结果就是均匀的
- 重写 equals 必须重写 HashCode
  - HashMap 是通过 key 的 HashCode 去寻找 index 的, 如果不进行重写, 会出现在一个 index 中链表的 HashCode 相等情况, 所以要确保相同的对象返回相同的 hash 值，不同的对象返回不同的 hash 值,必须要重写 equals

### ConcurrentHashMap

- 安全失败机制
  - 这种机制会使你此次读到的数据不一定是最新的数据, 如果你使用 null 值, 就会使得其无法判断对应的 key 是不存在还是为空, 因为你无法再调用一次 `contain(key)` 来对 key 是否存在进行判断，HashTable 同理
- JDK 1.7
  - 数据结构: 数组+链表 (Segment 数组、HashEntry 组成)
  - HashEntry
    - HashEntry 跟 HashMap 差不多的，但是不同点是，他使用 volatile 去修饰了他的数据 Value 还有下一个节点 next
  - 并发度高的原因
    - segment 分段锁
      - 继承了 ReentrantLock
      - 每当一个线程占用锁访问一个 Segment 时，不会影响到其他的 Segment, 如果容量大小是16他的并发度就是16，可以同时允许16个线程操作 16 个 Segment 而且还是线程安全的
    - put
      - 尝试自旋获取锁,如果获取失败肯定就有其他线程存在竞争，则利用 `scanAndLockForPut()` 自旋获取锁
      - 如果重试的次数达到了 `MAX_SCAN_RETRIES `则改为阻塞锁获取，保证能获取成功
    - get
      - 由于 HashEntry 中的 value 属性是用 volatile 关键词修饰的，保证了内存可见性，所以每次获取时都是最新值
      - ConcurrentHashMap 的 get 方法是非常高效的，因为整个过程都不需要加锁
- JDK 1.8
  - 数据结构 : 数组+链表+红黑树
  - 区别 : 抛弃了原有的 Segment 分段锁，而采用了 CAS + synchronized 来保证并发安全性
  - put
    - 根据 key 计算出 hashcode
    - 判断是否需要进行初始化
    - 即为当前 key 定位出的 Node，如果为空表示当前位置可以写入数据，利用 CAS 尝试写入，失败则自旋保证成功
    - 如果当前位置的 `hashcode == MOVED == -1`, 则需要进行扩容
    - 如果都不满足，则利用 synchronized 锁写入数据
    - 如果数量大于 `TREEIFY_THRESHOLD` 则要转换为红黑树
  - get
    - 根据计算出来的 hashcode 寻址，如果就在桶上那么直接返回值
    - 如果是红黑树那就按照树的方式获取值
    - 若不满足那就按照链表的方式遍历获取值

## Set

### HashSet

- 底层实现的就是HashMap，所以是根据HashCode来判断是否是重复元素
- 初始化容量是 ：16, 因为底层实现的是HashMap, 加载因子是0.75
- 无序的
- HashSet不能根据索引去数据，所以不能用普通的 for 循环来取出数据，应该用增强 for 循环,查询性能不好

### TreeSet

- 底层是实现的 TreeMap
- 元素不能够重复，可以有一个 null 值，并且这个 null 值一直在第一个位置上
- 默认容量：16，加载因子是0.75
- TreeMap是有序的，这个有序不是存入的和取出的顺序是一样的，而是根据自然规律拍的序







