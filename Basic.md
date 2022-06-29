# Basic

## Contents

- [Abstract Data Type(추상 자료형)](#abstract-data-type추상-자료형)
- [Data Structure(자료 구조)](#data-structure자료-구조)
- [Types of Data Structure(자료 구조의 종류)](#types-of-data-structure자료-구조의-종류)
- [Principles(원칙)](#principles원칙)
- [Complexity(복잡성)](#complexity복잡성)
- [Common Asymptotic Notations(표기법)](#common-asymptotic-notations표기법)





## Abstract Data Type(추상 자료형)

> 어떤 문제를 해결하기 위한 자료 형태와 그것을 다루는 연산을 수학적으로 정의한 모델
>
> 데이터와 연산 두 가지 부분에 대한 명세서(Specification)로 구성

- 인터페이스와 구현을 분리하여 추상화 계층(인터페이스)을 둔것
- 내부 구현을 알지 못해도 ADT 명세만 알면 활용 가능
  - EX) TV 리모콘을 누를때 내부 구현을 알지 못해도 버튼만 누르면 동작 - powerOn(), volumeUp()
- 관련 자료형의 기본 특성은 가지지만 정해진 표준은 없고 정의하는 회사나 사람에 따라 다를 수 있음
- 연산에 대한 복잡도나 구현 내용은 정의하지 않음

💡추상 자료 구조: 추상 자료형에 각 연산에 대한 복잡도까지 정의한 가상의 자료 구조



## Data Structure(자료 구조)

> 자료를 효율적으로 이용할 수 있도록 저장하는 방법을 의미
>
> 1차원 형태의 메모리 공간과 현실 세계의 다차원 데이터를 어떻게 변환할 것인지 다루는 일이기도 함
>
> 추상자료형에서 정의한 내용을 실제로 구체화한 형태
>
> - 추상화 - 무엇(What)을 할 것인가
> - 구체화 - 어떻게(How) 할 것인가
>
> 잘 짜여진 자료구조는 적은 메모리 용량과 연산 시간을 갖게 되므로 효솨적인 알고리즘 구현에 중요한 역할
>
> 주요 관점: 검색, 삽입, 변경, 삭제



## Types of Data Structure(자료 구조의 종류)

- Primitive Data Structure(원시 자료 구조)
  - Integer
  - Float
  - Character
  - Boolean
- Non - Primitive Data Structure(비 원시 자료 구조)
  - Linear Data Structure(선형 자료 구조)
    - Arrays
    - Linked List
    - Stack
    - Queue
  - Non - Linear Data Structure(비 선형 자료 구조)
    - Trees
    - Graphs



## Principles(원칙)

> 자료 구조가 가져야 하는 특징

- 정확성(Correctness): 필요한 자료에 필요한 연산을 정확히 적용 할 수 있어야 함
- 효율성(Efficiency): 상황에 맞는 구조를 사용하여 자료 처리의 효율성 상승
- 추상화(Abstraction): 복잡한 자료의 핵심 개념 또는 기능을 추상화 하여 간단하고 쉽게 사용할 수 있도록 설계
- 재사용성(Reusability): 추상화된 개념을 모듈화하여 독립적이고 쉽게 재사용 가능하도록 함



자료 구조 선택 기준

- 자료의 크기와 처리시간
- 자료의 활용 및 갱신 빈도
- 활용 용이성

| Data Structure             | Advantages                                                   | Disadvantages                                                |
| -------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Array(배열)                | Quick inserts<br />Fast access if index known                | Slow search<br />Slow deletes<br />Fixed size                |
| Ordered Array(정렬된 배열) | Faster search than unsorted array                            | Slow inserts<br />Slow deletes<br />Fixed size               |
| Stack(스택)                | Last-in, first-out access                                    | Slow access to other items                                   |
| Queue(큐)                  | First-in, first-out access                                   | Slow access to other items                                   |
| Linked List                | Quick inserts<br />Quick deletes                             | Slow search                                                  |
| Binaty Tree                | Quick search<br />Quick inserts<br />Quick deletes<br />(If the tree remains balanced) | Deletion algorithm is complex                                |
| Red-Black Tree             | Quick search<br />Quick inserts<br />Quick deletes<br />(Tree always remains balanced) | Complex to implement                                         |
| 2-3-4 Tree                 | Quick search<br />Quick inserts<br />Quick deletes<br />(Tree always remains balanced)<br />(Similar trees good for disk storage) | Complex to implement                                         |
| Hash Table                 | Very fast access if key is known<br />Quick inserts          | Slow deletes<br />Access slow if key is not known<br />Inefficient memory usage |
| Heap                       | Quick inserts<br />Quick deletes<br />Access to largest item | Slow access to other items                                   |
| Graph                      | Best models real-workd situations                            | Some algorithms are slow and very complex                    |





## Complexity(복잡성)

> 시간복잡성 - 데이터 연산 시간은 가능한 작아야 함
>
> 공간복잡성 - 데이터 연산 및 저장에 필요한 메모리 공간은 가능한 작아야 함



- Worst Case
  - 빅-오 (O, Big-Oh) 표기법
  - 최악의 경우를 가정. 시간 복잡도를 말할때 가장 일반적으로 사용
- Average Case
  - 세타 (θ, Theta) 표기법
  - 평균적인 경우를 가정
- Best Case
  - 빅-오메가 (Ω, Big-Omega) 표기법
  - 최선의 경우를 가정

## Common Asymptotic Notations(표기법)

|                     |            |
| ------------------- | ---------- |
| constant(불변)      | O(1)       |
| logarithmic(대수의) | O(log n)   |
| linear(선형)        | O(n)       |
| n log n             | O(n log n) |
| quadratic           | O(n²)      |
| cubic               | O(n³)      |
| polynomial          | nº(1)      |
| exponential         | 2º(n)      |





















