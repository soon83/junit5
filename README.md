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
class OfTheTest_ByTheTest_ForTheTest {

    public static int count = 0;

    /**
     * 각 테스트가 실행되기 전 한번씩 돌아감
     */
    @BeforeEach
    void beforeEach() {
        System.out.println("#######################");
        System.out.println("# BeforeEach: " + count);
        // ex. 여기서 초기화 같은거 하면 될 것 같음
    }

    @Test
    void test0() {
        System.out.println("# 이거슨 TEST 0");
    }

    @Test
    void test1() {
        System.out.println("# 이거슨 TEST 1");
    }

    /**
     * 각 테스트가 실행된 이후 한번씩 돌아감
     */
    @AfterEach
    void afterEach() {
        System.out.println("# AfterEach: " + count);
        System.out.println("#######################");
        System.out.println();
        count++;
        // ex. 여기서 초기화 같은거 하면 될 것 같음
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
