Array와 Linked List의 차이
* 데이터 접근 속도
  * Array는 인덱스를 통한 Random Access를 지원하므로 시간 복잡도 O(1)로 빠르게 찾을 수 있다.
  * LinkedList는 순차 접근 방식을 사용하므로 시간 복잡도 O(N)이 걸린다.
  
* 데이터의 삽입/삭제 속도
  * Array는 데이터를 중간이나 맨 앞에 삽입/삭제하는 경우 shift가 필요하므로 데이터가 많을수록 비효율적이다.
  * LinkedList는 중간 삽입/삭제는 똑같이 O(N)의 시간 복잡도를 갖지만, 맨 앞 또는 뒤에 삽입할 경우 O(1)의 시간복잡도를 갖는다.
  * 다만 LinkedList는 데이터 삽입/삭제마다 메모리 할당/해제가 일어나므로 시간복잡도는 빠를지라도 시스템 콜(System Call)에 있어서 Array보다 더 시간이 걸린다.
  
* 메모리 할당
  * Array는 정적 메모리 할당이 이루어진다. (Compile time)
  * LinkedList는 동적 메모리 할당이 이루어진다. (Runtime)
  * Array의 경우 데이터 삽입 시 모든 공간이 다 차버렸다면 새로운 메모리 공간이 필요하지만 LinkedList는 동적으로 할당받을 수 있다.
  데이터 삽입/삭제가 빈번하다면 LinkedList를 사용하는 것이 좋고, 데이터 접근 속도가 중요하다면 Array를 사용하는 것이 좋다.