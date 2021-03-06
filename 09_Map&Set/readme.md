# Map

Map은 key와 value가 한쌍인 컬렉

    const myMap = new Map();
    myMap.set("Lang","JavaScript");
    
    const myData = new Map([
        ["key1","value1"],
        ["key2","value2"]
    ]);
    console.log(myData.get("key1"));
    
    // 실행결과
    value1
    
초기화하면서 배열로 값을 할당할 수 있으며 get 메서드에 key 를 사용해서 value 를 출력할 수 있음

    
Map 예제2

    const myMap = new Map();
    // myMap.set("Plugin","Update").set("Refactor",6).set("Code",5);
    const myArray = [["Plugin","Update"],["Refactor",6], ["Code",5]];
    
    for(let i of myArray){
        myMap.set(...i);
    }
    myMap.delete("Hello");
    for(let [key, value] of myMap){
        console.log(key + "," + value)
    }
    
    // 실행결과
    Plugin,Update
    Refactor,6
    Code,5
    
set메서드를 연속해서 데이터를 할당 할 수 도 있음

delete메서드에 key를 넣어 삭제할 수 있음.

# MapIterator 활용

for-of, entries(), next(), keys(), values() 사용

    const myMap = new Map();
    const myArray = [["Plugin","Update"],["Refactor",6], ["Code",5]];
    
    for(let i of myArray){
        myMap.set(...i);
    }
    const myKeys = myMap.keys(),
        myValue = myMap.values(),
        myIter = myMap.entries();
    console.log(myKeys);
    console.log(myValue);
    console.log(myIter);
    
    console.log(myIter.next());
    console.log(myIter.next());
    console.log(myIter.next());
    console.log(myIter.next());
    
    // 실행결과
    MapIterator { 'Plugin', 'Refactor', 'Code' }
    MapIterator { 'Update', 6, 5 }
    MapIterator { [ 'Plugin', 'Update' ], [ 'Update', 6 ], [ 'Code', 5 ] }
    { value: ["Plugin", "Update"], done: false }
    { value: ["Refactor", 6], done: false }
    { value: ["Code",5], done: false }
    { value: undefined, done: true }

keys 메서드와 values 메서드는 key를 값으로 가지는 MapIterator, value를 값으로 가지는 MapIterator<br>
entries 메서드는 key, value 를 갖는 MapIterator 를 반환합니다. 

# Map 필터링 실습

Map 을 특정 조건으로 필터링하여 다른 Map 에 담기.

    const myMap = new Map();
    const myArray = [["Plugin","Update"],["Refactor",6], ["Code",5]];
    
    for(let i of myArray){
        myMap.set(...i);
    }
    const newMap = new Map (
        [...myMap].filter(([a,b])=> b ==6)
    );
    console.log(newMap)

    // 실행결과
    Map {"Refactor" => 6}
    
# Set

중복을 허용하지 않는 집합

    var set = new Set();
    set.add("ECMAScript").add("6");
    console.log(set.has("ECMAScript"));
    console.log(set.size);
    console.log(...set.values());
    
    // 실행결과
    true
    2
    ECMAScript 6
    
has 메서드를 통해 해당 값의 존재 여부를 알 수 있음

size 메서드로 개수를 알 수 있음

# 정리하기

Map은 key와 value 가 한쌍

Set은 value로만 이루어진 집합