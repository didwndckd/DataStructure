# 스택(Stack)



## 개념

- 한쪽 끝에서만 자료를 넣고 뺄 수 있는 자료구조
  - LIFO(Last In First Out)
  - 중간에 데이터를 빼거나 넣는 경우라면 stack을 사용하면 안된다
  - 마지막에 넣은것이 처음으로 나오는 경우, 또는 그 반대의 경우에 의미가 있음



## 구현

- 배열을 이용한 구현

  ```swift
  
  class Stack<T> {
      private var stack = [T]()
      private var size = 0
      
      func push(_ data: T) {
          stack.append(data)
          size += 1
      }
      
      func pop() -> T {
          let data = stack[size - 1]
          stack.remove(at: size - 1)
          size -= 1
          return data
      }
      
      func peek() -> T {
          return stack[size - 1]
      }
      
      func isEmpty() -> Bool {
          return size == 0
      }
      
  }
  ```

- Single linked List(단일 연결 리스트)를 이용한 구현

  ```swift
  class Stack<T> {
      
      private class Node {
          let data: T
          var next: Node?
          
          init(data: T) {
              self.data = data
          }
      }
      
      private var top: Node?
      var isEmpty: Bool { top == nil }
      
      func push(data: T) {
          let node = Node(data: data)
          node.next = top
          self.top = node
      }
      
      func pop() -> T? {
          let data = top?.data
          self.top = top?.next
          return data
      }
      
      func peek() -> T? {
          return top?.data
      }
      
  }
  ```

  