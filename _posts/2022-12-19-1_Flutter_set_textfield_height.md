---
layout: single
title:  "Flutter set text field height"
search: true
---
# Flutter set textField height

TextField의 높이를 그냥 변경 하려고 하면 제대로 동작 하지 않는다.

잡다한 설명은 빼고 바로 해결 방법을 보자.

기본 셋팅으로

```
minLines: null,
maxLines: null,
expands: true 
```

해당 옵션을 넣어줘야 높이 변경이 가능하다.





다음으로는 decoration에 아래와 같이 코드를 추가해보자

```
InputDecoration(
            filled: false,
            constraints: BoxConstraints(minHeight: proportionateHeight(216), maxHeight: proportionateHeight(216)))
```

잘 동작 할 것이다.![](/assets/img/blog/2022-12-19_1.png)
