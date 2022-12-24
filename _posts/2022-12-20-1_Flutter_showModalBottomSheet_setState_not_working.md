---
layout: single
title:  "Flutter showModalBottomSheet setState not working"
search: true 
---

# Flutter `showModalBottomSheet` setState not working

`setState()`는 `StatefulWidget` 에서 특정 오브젝트의 상태(값)를 변경하기 위해 사용하는 메소드이다.

근데 이번에 `showModalBottomSheet`에서 요일을 선택하는 기능을 가진 화면을 작업하다가 

setState 를 통해 상태 변경을 호출해도 화면이 변경되지 않는 현상을 발견했다. 

```dart
showModalBottomSheet(
    context: context,
    builder: (context) {return StatefulBuilder(
          builder: (BuildContext context, StateSetter setModalState /*해당 부분 이름을 바꾸어 사용!*/) {
        return Container(
          height: heightOfModalBottomSheet,
          child: RaisedButton(onPressed: () {
            setModalState(() {
              heightOfModalBottomSheet += 10;
            });
          }),
        );
      });
});
```



```dart
//This sets modal state
setModalState(() {
    heightOfModalBottomSheet += 10;
});//This sets parent widget state
setState(() {
     heightOfModalBottomSheet += 10;
});
```


출처 :  [https://stackoverflow.com/a/56972160](https://stackoverflow.com/a/56972160)


  
해결방법은 간단하다 StatefulBuilder 를 추가하고 


StateSetter setModalState 를 이용하여 상태 변경을 호출해주면 정상적으로 UI 변경이 된다.