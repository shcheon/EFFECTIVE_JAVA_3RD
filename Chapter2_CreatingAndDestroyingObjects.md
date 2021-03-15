
# Create and Destorying Objects
>
- Objects의 생성,파괴를 시기적절하게 이루어 질 수 있도록 관리하는 방법에 관하여 알아보자

## Item 1 : Consider Static factory methods instead of constructors
> 
- 생성자 대신 static factory method를 고려하라 (Design Pattern의 Factory Method를 말하는 것이 아님)
- static factory method를 사용하면 얻는 이점
### 1. 생성자와 달리 이름을 가질 수 있다
- 이름을 가지고 있으므로, API를 사용하는 입장에서 가독성이 좋아진다.
  (파라미터가 여러개인 생성자의 경우는 Document의 설명을 보지 않고는 사용방법을 알 수 가 없다)

