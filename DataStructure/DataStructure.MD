# 자료구조


## 데크
### 💡 정의
데크는 Double Ended Que의 줄임말로 양쪽 끝을 모두 추출할 수 있는, 큐를 일반화한 형태의 ADT(추상자료형)
### 💡 연산 
- insertFront(): 데크 처음에 아이템 추가
- insertLast(): 데크 마지막에 아이템 추가 
- deleteFront(): 데크 처음에 아이템 삭제
- deleteLast(): 데크 마지막에 아이템 삭제 

- getFront(): 데크 처음에 아이템 가져옴(비어있으면 -1 리턴)
- getRear(): 데크 마지막에 아이템 가져옴(비어있으면 -1 리턴)
- isEmpty(): 비어있는지 확인
- isFull(): 가득 차있는지 확인

### 💡 특이사항 
- 특징: 스택과 큐의 특징을 모두 갖고 있음
- 구현: 배열, 연결리스트 모두 가능 (Doubly Linked List가 제일 적절)
- 파이썬: collections 모듈의 deque (collections.deque)

