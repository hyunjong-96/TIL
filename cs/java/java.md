# Java

## 객체 참조
객체 참조란, 객체의 메모리 주소를 공유함을 뜻한다.
```
Item item1 = new Item();    //메모리 주소1
Item item2 = new Item();    //메모리 주소2

item1.setData(1);
item2.setDate(2);

item1.getData(); => 1
item2.getData(); => 2
```
위의 item1, item2는 서로 다른 메모리 주소를 참조하고 있다. 그렇기 때문에 item1과 item2의 data는 서로 영향을 받지 않는다.

![객체참조](https://github.com/user-attachments/assets/4a035c12-bc4d-4310-9620-94af7a6cd627)

```
Item item1 = new Item();
Item item2 = item1;

item1.setData(1);
item2.setData(2);

item1.getData(); => 2
item2.getData(); => 2
```
위의 item1, item2는 서로 동일한 메모리 주소를 참조하고 있다. 그렇기 때문에 item1과 item2의 data는 서로 영향을 받는다.

<img width="808" alt="Image" src="https://github.com/user-attachments/assets/f0b00b8b-2c49-48e5-ae38-33d60b2f0d1c" />

```java
class TestObj {
    List<CaclAmt> customObjList;
}

class CalcAmt {
    Integer cnt;
    Integer totAmt;
}

class ServiceLogic {
    //...
    TestObj testObj = getTestObj();
    
    List<CalcAmt> calcAmtList = testObj.getCustomObjList(); 
    CalcAmt calcAmt = calcAmtList.get(0);
    
    calcAmt.setTotAmt(100000);
    calcAmt.setCnt(2);
    
    testObj.getCustomObjList().get(0).getTotAmt(); //=> 100000
    testObj.getCustomObjList().get(0).getCnt(); //=> 2
    //...
}
```
위에서 TestObj 객체가 있을때 내부 데이터를 꺼내와서 새로운 변수에 선언(메모리 주소 참조) 한 후 데이터를 수정하면 메모리 주소를 공유하고 있기 때문에 값에 영향을 끼친다.