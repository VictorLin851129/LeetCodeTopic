# 146. LRU Cache
## Solution
```
class LRUCache {
    
    class DoubleNode {
        int key;
        int value;
        DoubleNode front;
        DoubleNode rear;

        DoubleNode(){

        }
    }
    int Capacity;
    int count;
    HashMap<Integer, DoubleNode> table = new HashMap<Integer, DoubleNode>();
    DoubleNode head  = new DoubleNode(), tail = new DoubleNode();

    public LRUCache(int capacity) {
        this.Capacity = capacity;
        this.count = 0;
        head.rear = tail;
        tail.front = head;
    }

    public int get(int key) {
        if(table.containsKey(key)) {
            DoubleNode temp = table.get(key);
            temp.front.rear = temp.rear;
            temp.rear.front = temp.front;
            tail.front.rear = temp;
            temp.front = tail.front;
            temp.rear = tail;
            tail.front = temp;
            return temp.value;
        }
        return -1;
    }

    public void put(int key, int value) {
        if(table.containsKey(key)) {
            DoubleNode temp = table.get(key);
            temp.value = value;
            temp.front.rear = temp.rear;
            temp.rear.front = temp.front;
            tail.front.rear = temp;
            temp.front = tail.front;
            temp.rear = tail;
            tail.front = temp;
            table.put(key, temp);
        }else {
            DoubleNode newNode = new DoubleNode();
            newNode.key = key;
            newNode.value = value;
            if(count >= this.Capacity) {
                table.remove(head.rear.key);
                head.rear = head.rear.rear;
                head.rear.front = head;
            }
            count++;
            tail.front.rear = newNode;
            newNode.front = tail.front;
            newNode.rear = tail;
            tail.front = newNode;
            table.put(key, newNode);
        }
    }
}

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache obj = new LRUCache(capacity);
 * int param_1 = obj.get(key);
 * obj.put(key,value);
 */
```
### Time complexity: O(1)
### Space complexity: O(n)
#### Where n is given capacity