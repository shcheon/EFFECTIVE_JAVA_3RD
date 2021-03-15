
# Create and Destorying Objects
>
- Objects의 생성,파괴를 시기적절하게 이루어 질 수 있도록 관리하는 방법에 관하여 알아보자

## Item 1 : Consider Static factory methods instead of constructors
> 
- 생성자 대신 static factory method를 고려하라 (Design Pattern의 Factory Method를 말하는 것이 아님)

### static factory method를 사용하면 얻는 이점

#### 1. 생성자와 달리 이름을 가질 수 있다.
```
- 이름을 가지고 있으므로, API를 사용하는 입장에서 가독성이 좋아진다.
- 파라미터가 여러개인 생성자의 경우는 Document의 설명을 보지 않고는 사용방법을 알 수 가 없다.
  ex) BinInteger(int, int, Random) : Parameter는 뭘 의미하는지 알수가 없다.
      BigInteger.probablePrime() : 소수에 관한 메소드인지 직관적으로 이해가능
```
#### 2. 매번 불러올 때마다 Object를 새로 생성할 필요가 없다.
```java
- 아래 예시를 보면 Boolean 객체를 불러올 때 마다 Object를 생성하지 않는다. (객체 생성에 대한 비용 Save)
public static Boolean valueOf(boolean b) {
  return b ? Boolean.TRUE : Boolean.FALSE;
}
- 
```
#### 3. They can return an object of any subtype of their return type.  

#### 4. the class of the returned object can vary from call to call as a function of the input parameters.

#### 5. class에 Method가 포함되어 있어도, Object는 존재하지 않아도 된다.
```
- Service provider framework 구현 시 많이 사용된다.
```

### static factory method의 단점
#### 1. 클래스 상속이 불가능하여, 상속받은 생성자를 사용할 수 없다.
```
- Composition을 사용할 수 
```

