---
layout: post
title:  "memory structure"
date:   2020-08-25 20:00
categories: blog
---

#### 메모리 구조는 어떻게 되어있는가?

![memory](/blog_img/gdb-memory.png)

먼저 크게 메모리 구조에는 code 영역 , 데이터 영역 , 힙 역역 , 스택 영역으로 나뉘어져있다.

__memory code__

__memory data__

__memory heap__

__memory stack__

#### file consloe_test.c


###### 위에 설명을 다 읽었는데도 이해가 잘 안간다면 직접 소스코드를 작성하여 해당 전젹 지역 등의 변수들이

###### 어디 메모리 주소에 할당되는지 테스트를 해보자

###### 일단 파일을 3개 만들고 각 c언어로 작성을 해보았다.

```cpp
#include "code.h"
#include "function.h"

static int global_variable_one = 0, global_variable_two = 0;
int noT_static_global = 0;

int locAl_variable(int variaBle) 
{
	int function_int_vb = 0;
	static int function_static_int = 0;
	printf("main file function ㅡㅡㅡㅡㅡ\n");
	printf("type(int) ->		0x%X\n", &variaBle);
	printf("type(int) ->		0x%X\n", &function_int_vb);
	printf("type(static int) ->	0x%X\n\n\n", &function_static_int);

	return 0;
}
int main()
{
	int result = sum(4, 5),main_var;
	static int main_variable;
	printf("main ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ\n");
	printf("type(int) ->		0x%X\n", &result);
	printf("type(int) ->		0x%X\n\n\n", &main_var);
	
	printf("type(int) ->		0x%X\n", &noT_static_global);
	printf("type(static int) ->	0x%X\n", &global_variable_one);
	printf("type(static int) ->	0x%X\n\n\n", &global_variable_two);

	locAl_variable(1);

	printf("type(static int) ->	0x%X\n", &main_variable);
}
```

#### file function.h

```cpp
#include <stdio.h>

int sum(int a, int b)
{
	printf("extern function ㅡㅡㅡㅡㅡㅡㅡㅡ\n");
	printf("type(int) ->		0x%X\n", &a);
	printf("type(int) ->		0x%X\n\n\n", &b);
	return 0;
}
```

#### file code.h

```cpp
#include <stdio.h>

extern int sum(int a, int b);

```

###### 이렇게 파일이 3개가 있는데 그중 메인 파일은 consloe_test.c 파일이다.

###### 해당 c언어 파일의 소스코드를 살펴보자면 전역변수 외부함수 등을 각각 변수 선언한다음 해당 변수들 해당 함수들을 %X 형식으로 메로리 주소를 출력하게 해보았다.

###### 이제 각 메모리 주소들이 메모리 구조에서 각 영역이 생기게 된다.

![memory_structure](/blog_img/c_test_variable.png)

에렇게 각 코드 , 데이터 , 힙 , 스택 중에서 각 변수 함수들의 영역이 생기게 된다.

