## Stubs
We can stub a data Service Layer here.

First We are creating an Data Service Interface
```java
public interface SomeDataService {
    int[] retrieveAllData();
}
```

Then we are implemeting the Interface
```java
public class SomeBusinessImplementation {

    private SomeDataService someDataService;

    public SomeDataService getSomeDataService() {
        return someDataService;
    }

    public void setSomeDataService(SomeDataService someDataService) {
        this.someDataService = someDataService;
    }

    public int calculateSum(int[] intArr){
        int sum=0;
        for(int value:intArr){
            sum=sum+value;
        }
        return sum;
    }

    public int calculateSumUsingDataService(){
        int[] intArr=someDataService.retrieveAllData();
        int sum=0;
        for(int value:intArr){
            sum=sum+value;
        }
        return sum;
    }
}
```

Then the test Cases by using stub will be like

```java
class SomeDataServiceImpl implements SomeDataService {

    @Override
    public int[] retrieveAllData() {
        return new int[]{1,2,3};
    }
}

//Stubbing the SomeData Service
class SomeDataServiceEmptyImpl implements SomeDataService {

    @Override
    public int[] retrieveAllData() {
        return new int[]{};
    }
}

public class Test_SomeBusinessStubTests {

    /**
     * @description : Basic Unit Testing. Some Value
     */
    @Test
    public void calculateSumUsingDataService_Basics(){
        SomeBusinessImplementation business=new SomeBusinessImplementation();
        business.setSomeDataService(new SomeDataServiceImpl());

        int actualResult=business.calculateSumUsingDataService();
        int expectedResult=6;
        assertEquals(expectedResult,actualResult);
    }

    /**
     * @description : Basic Unit Testing. Empty Array
     */
    @Test
    public void calculateSum_Basics_empty(){
        SomeBusinessImplementation business=new SomeBusinessImplementation();
        business.setSomeDataService(new SomeDataServiceEmptyImpl());
        int actualResult=business.calculateSumUsingDataService();
        int expectedResult=0;
        assertEquals(expectedResult,actualResult);
    }


}
```


## Mock
By Mocks we can programatically create classes ( Implenetation Classes of the Data Service Interfaces)