# 큐(Queue)

## 개념

- 한쪽 끝에서만 자료를 넣고 다른 한쪽에서만 자료를 뺄 수 있는 자료구조
  - **FIFO(First In First Out)** 먼저 들어간 자료가 먼저 나옴



## 용어

- 값을 추가하는 것: Enqueue 또는 Put
- 값을 꺼내오는 것: Dequeue 또는 Get
- Front: Dequeue에 사용될 인덱스
- Rear(Back): Enqueue에 사용될 인덱스 



## 구현

- 배열을 이용한 구현

  ```swift
  class Queue<T> {
      private var queue = [T]()
      var isEmpty: Bool {
          queue.isEmpty
      }
  
      func enqueue(data: T) {
          queue.append(data)
      }
  
      func dequeue() -> T? {
          guard !queue.isEmpty else { return nil }
          let data = queue.removeFirst()
          return data
      }
  
      func peek() -> T? {
          return queue.first
      }
  
  }
  ```

- 연결리스트를 이용한 구현

  ```swift
  class Queue<T> {
      
      private class Node {
          let data: T
          var next: Node?
          
          init(data: T) {
              self.data = data
          }
      }
      
      private var front: Node?
      private var rear: Node?
      var isEmpty: Bool {
          front == nil
      }
      
      func enqueue(data: T) {
          let node = Node(data: data)
          
          if self.front == nil {
              self.front = node
          }
          
          if let rear = self.rear {
              rear.next = node
          }
          
          self.rear = node
      }
      
      func dequeue() -> T? {
          guard let front = self.front else { return nil }
          
          let data = front.data
          let next = front.next
          self.front = next
          
          if next == nil {
              self.rear = nil
          }
          
          return data
      }
      
      func peek() -> T? {
          return front?.data
      }
      
  }
  ```

  