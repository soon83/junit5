# junit5

## 생명주기
### 꼴베기 싫게 생명주기가 있음

#### @BeforeEach
- 얘는 각 테스트가 실행되기 전 한번씩 돌아감
- 초기화작업 같은거 하면 될 듯
  - DB삭제나 객체생성이나 뭐 그런것들,,

#### @AfterEach
- 야는 각 테스트가 실행된 후에 한번씩 돌아감
- 얘도 뭐 초기화 같은거 하면 될 것 같음

```
#### 예제
##### @BeforeEach
##### @AfterEach

class OfTheTest_ByTheTest_ForTheTest {

    public static int count = 0;

    @BeforeEach
    void beforeEach() {
        System.out.println("#######################");
        System.out.println("# BeforeEach: " + count);
    }

    @Test
    void test0() {
        System.out.println("# 이거슨 TEST 0");
    }

    @Test
    void test1() {
        System.out.println("# 이거슨 TEST 1");
    }

    @AfterEach
    void afterEach() {
        System.out.println("# AfterEach: " + count);
        System.out.println("#######################");
        System.out.println();
        count++;
    }
}
```
```
#### 결과
#######################
# BeforeEach: 0
# 이거슨 TEST 0
# AfterEach: 0
#######################
#######################
# BeforeEach: 1
# 이거슨 TEST 1
# AfterEach: 1
#######################
```

#### @BeforeAll
- 얘는 모든 테스트가 실행되기 전 딱 한번 돌아감
- 일단 이런게 있다는 것만 알고넘어가자
- 아 정적메서드에 사용해줘야 함, 안그럼 에러남

#### @AfterAll
- 야는 각 테스트가 실행된 후에 한번씩 돌아감
- 얘도 정적메서드에 사용해줘야 함, 안그럼 에러남

```
#### 예제
##### @BeforeEach
##### @AfterEach

class OfTheTest_ByTheTest_ForTheTest {

    public static int count = 0;

    @BeforeAll
    static void beforeAll() {
        System.out.println("#######################");
        System.out.println("# BeforeAll: " + count);
    }

    @Test
    void test0() {
        System.out.println("# 이거슨 TEST 0");
    }

    @Test
    void test1() {
        System.out.println("# 이거슨 TEST 1");
    }

    @AfterAll
    static void afterAll() {
        System.out.println("# AfterAll: " + count);
        System.out.println("#######################");
        System.out.println();
        count++;
    }
}
```
```
#######################
# BeforeAll: 0
# 이거슨 TEST 0
# 이거슨 TEST 1
# AfterAll: 0
#######################
```

#### 테스트 메서드 간 실행 순서 의존과 필드 공유하지 않기
- 각 테스트 메서드는 서로 독립적으로 동작해야한다
- 테스트순서에 따라 테스트의 결과가 달라진다면 유지보수가 어려워져서 결국, 개 똥이되는 것이다 명심하도록,,






