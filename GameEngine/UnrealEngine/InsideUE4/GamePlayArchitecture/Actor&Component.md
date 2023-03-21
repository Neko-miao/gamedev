# GamePlay Architecture -- Actor & Component  
## UObject  
```C++
class UObject 
{
    GC;
    MetaData;
    Reflection;
    Serialization;
    Editable;
    Class Default Object;
}
```

## Actor  
```C++
class AActor:UObject
{
    TArray<AActor*> Children;
    void Tick(float delta);

    AActor* Owner;(weak)
}
```

- Actor之间可以相互嵌套  
- Actor没有自带Transform，因为Actor可以代表游戏世界的信息、状态、规则等，而不单单是“GameObject”。
- Transform被封装进了SceneComponent中作为RootComponent，当然，为了获取方便，大部分Actor其实是有Transform的，但其内部实现都是转发到RootComponent。  

## Component
