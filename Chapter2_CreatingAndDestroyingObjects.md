
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
#### 1. classes without public or protected constructors cannot be subclassed.

#### 2. Programmer가 API를 찾기 힘들다.
```
- class를 어떻게 instantiate를 하는지 이해하기 어렵다. 
  그러나, static factory method는 API를 쉽게 찾을 수 있도록 일반정인 명명법을 채택하였다.

* from    : Type-Conversion method              
            ex) Date d = Data.from(instant) // instant는 Date로 형 변홤
* of      : 여러 개의 parameters를 받아 하나의 instance로 변환하는 aggregation method 
            ex) Set<Rank> faceCards = EnumSet.of(JACK, QUEEN, KING);
* valueOf : from, of의 대안으로 사용되는 type conversion method
            ex) BigInteger prime = BigInteger.valueOf(Integer.MAX_VALUE);

* instance or getInstance : parameter에 명시된 객체를 반환하는 method
                            ex) StackWalker luke = StackWalker.getInstance(options);
* create or newInstance   : instance or getInstance와 동일하지만, 호출할 떄마다 새로운 instance를 생성함
                            ex) Object newArray = Array.newInstance(classObject, arrayLen);
* getType : instance or getInstance와 동일하지만, Type으로 형을 반환
            ex) FileStore fs = Files.getFileStore(path);
* newType : newInstance와 동일하지만, Type으로 형을 반환
            ex) BufferedReader br = Files.newBufferedReader(path);
* Type : getType, newType의 대안
         ex) List<Complaint> litany = Collections.list(legacyLitany);
```


# Summary
```
생성하지 않는다. (객체 생성에 대한 비용 Save)

22

public static Boolean valueOf(boolean b) {

23

  return b ? Boolean.TRUE : Boolean.FALSE;

24

}

25

- 

26

```

27

#### 3. They can return an object of any subtype of their return type.  

28



29

#### 4. the class of the returned object can vary from call to call as a function of the input parameters.

30



31

#### 5. class에 Method가 포함되어 있어도, Object는 존재하지 않아도 된다.

32

```

33

- Service provider framework 구현 시 많이 사용된다.

34

```

35



36

### static factory method의 단점

37

#### 1. classes without public or protected constructors cannot be subclassed.

38



39

#### 2. Programmer가 API를 찾기 힘들다.

40

```

41

- class를 어떻게 instantiate를 하는지 이해하기 어렵다. 

42

  그러나, static factory method는 API를 쉽게 찾을 수 있도록 일반정인 명명법을 채택하였다.

43



44

* from    : Type-Conversion method              

45

            ex) Date d = Data.from(instant) // instant는 Date로 형 변홤

46

* of      : 여러 개의 parameters를 받아 하나의 instance로 변환하는 aggregation method 

47

            ex) Set<Rank> faceCards = EnumSet.of(JACK, QUEEN, KING);

48

* valueOf : from, of의 대안으로 사용되는 type conversion method

49

            ex) BigInteger prime = BigInteger.valueOf(Integer.MAX_VALUE);

50



51

* instance or getInstance : parameter에 명시된 객체를 반환하는 method

52

                            ex) StackWalker luke = StackWalker.getInstance(options);

53

* create or newInstance   : instance or getInstance와 동일하지만, 호출할 떄마다 새로운 instance를 생성함

54

                            ex) Object newArray = Array.newInstance(classObject, arrayLen);

55

* getType : instance or getInstance와 동일하지만, Type으로 형을 반환

56

            ex) FileStore fs = Files.getFileStore(path);

57

* newType : newInstance와 동일하지만, Type으로 형을 반환

58

            ex) BufferedReader br = Files.newBufferedReader(path);

59

* Type : getType, newType의 대안

60

         ex) List<Complaint> litany = Collections.list(legacyLitany);

61

```

62



63



64

# Summary

65

```

66

static factory method 와 public 생성자의 각각 장점을 활용하static factory method 와 public 생성자의 각각 장점을 활용하
```
