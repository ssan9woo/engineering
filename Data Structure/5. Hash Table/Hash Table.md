#  Hash Table
- [key, value] 로 데이터를 저장하고, 데이터를 빠르게 검색할 수 있는 자료구조
<br><br>

## 특징
- Python에서는 hash함수를 이용해 Key값을 받아오고, 그 Key값을 특정 길이로 mod연산을 하게되면 index를 만들 수 있다.
- Hash Table의 크기를 미리 지정하여 사용한다.
- 내부적으로 배열(버킷)을 사용하여 데이터를 저장하기 때문에 빠른 검색속도를 제공
- 각각의 Key값에 `해시함수` 를 적용해 고유한 index를 생성하여 사용함

## 활용
- 데이터 관리
- 캐싱
<br><br>

### 장점 
- 자료의 검색, 삽입, 삭제가 빈번한 경우에 용이
- Hash Key에 대한 Data가 중복인지 확인하기 쉽다.

### 단점
- 공간복잡도가 늘어난다. 속도를 늘리기 위해서 메모리를 더 많이 쓰는 자료구조
- Hash Key에 대한 index가 중복될 경우 충돌이 생긴다.

### 복잡도
- 저장/검색/삭제 : O(1)
- 최악의 경우, Collision이 발생하면 모든 버킷의 value를 찾아봐야 하는 경우가 발생하여 최대 O(n)의 복잡도가 될 수 있다.
<br><br><br>

## 1. Hash Function [Hash Method]
```
Data의 Key값을 고유한 index로 만들어주는 함수
```

### 특징
  - 이 메소드에 의해 반환된 데이터의 고유 숫자 값을 `hashcode` 라고 한다.
  - 메소드를 통해 key값을 `작은 범위의 값` 으로 바꿔준다.
<br><br><br>

## 2. Collision [충돌]
```
서로 다른 두 개의 Key가 같은 index로 hasing되면 충돌하여 같은 곳에 저장할 수 없게 되는 현상
```
<br><br>

### 2-1. Open Address 방식 (개방 주소법)
```
Collision이 발생하면, 다른 hash 버킷에 해당 자료를 삽입하는 방식.
```

-  **Linear Probing** : 순차적으로 탐색하며 비어있는 버킷을 찾을 때 까지 계속 진행된다.
-  **Quadratic Probing** : 2차 함수를 이용해 탐색할 위치를 찾는다.
-  **Double Hasing Probing** : 하나의 해쉬 함수에서 충돌이 발생하면 2차 Hash Function을 이용해 새로운 주소를 할당한다. 이는 많은 연산량이 요구된다
<br>

### 2-2. Separate Chaining 방식 (분리 연결법)
```
Collision이 일어나면 해당 버킷을 확장시켜 데이터를 추가시키는 방식
```
-  **Linked List** : 버킷을 연결 리스트로 만들어 Collision이 일어나면 해당 버킷의 list에 추가하는 방식. 
-  **Tree** : 기본적인 알고리즘은 동일하지만, 버킷을 Tree 형태로 만든 방식.

<br><br><br>
