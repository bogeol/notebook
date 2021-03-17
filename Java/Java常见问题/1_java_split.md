> java split不出东西返回啥

```java
public class Test {
    public static void main(String[] args) {
        String test = "sdfjsdkj sdjfksjdk jskdfjks djkf jskd";
        System.out.println("---------split1");
        String[] split1 = test.split(" ");
        System.out.println(split1.length);
        Arrays.stream(split1).forEach(e -> System.out.println(e));

        System.out.println("---------split2");
        String[] split2 = test.split("_");
        System.out.println(split2.length);
        Arrays.stream(split2).forEach(e -> System.out.println(e));
    }
}
>>>
---------split1
5
sdfjsdkj
sdjfksjdk
jskdfjks
djkf
jskd
---------split2
1
sdfjsdkj sdjfksjdk jskdfjks djkf jskd

# 可见,Java split如果分割不出东西,还是会把原来的String => 扔到分割的String[]里面
```

