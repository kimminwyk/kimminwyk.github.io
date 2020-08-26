---
layout: post
title:  "memory structure"
date:   2020-08-25 20:00
categories: blog
---

#### 메모리란 무엇인가?

메모리 : 주 기정장치라고도 불리며 시스템의 데이터 스토리치로 실시간으로 사용되고있는 정보를 저장하고 

이 메모리는 시스템에서 많은 프로그램을 실행할수록 더 많은 메모리 공간이 필요하게된다.

#### 메모리 구조는 어떻게 되어있는가?

![memory](/blog_img/gdb-memory.png)
[출저](https://bpsecblog.wordpress.com/2016/03/08/gdb_memory_1/)

먼저 크게 메모리 구조에는 code 영역 , 데이터 영역 , 힙 역역 , 스택 , 커널 영역으로 나뉘어져있다.

__memory code : 코드 자체를 구성하고있는 메모리의 영역으로 hex , bin 파일 등의 메모리다.__

__memory data : 전역 정적 변수, 배열, 구조체 등이 저장되는영역__ 

__memory heap : 할당된 메모리나 동적 데이터 영역이다.__

__memory stack : 프로그램이 자동으로 사용하는 임시 메모리 영역이다. 지역 매개 변수, 리턴값 등 잠시 사용되었다가 사라지는 데이터를 저장하는 영역이다.__

__memory kernel : 이 영역들 중에서 유저 영역을 제외한 나머지 영역을 커널 영역이라고한다.__

###### 이해가 잘 안간다면 직접 소스코드를 작성하여 해당 전젹 지역 등의 변수들이

###### 어디 메모리 주소에 할당되는지 테스트를 해보자

###### 일단 파일을 3개 만들고 각 c언어로 작성을 해보았다.

#### file consloe_test.c

```cpp
#include "code.h"
#include "function.h"
#include <malloc.h>
static int global_variable_one = 0, global_variable_two = 0;
int noT_static_global = 0;

int locAl_variable(int variaBle) 
{
	int function_int_vb = 0;
	static int function_static_int = 0;
	printf("main file function ㅡㅡㅡㅡㅡ\n");
	printf("* type(function) -> locAl_variable        0x%X\n\n", &locAl_variable);
	printf("type(int) -> variaBle 			0x%X\n", &variaBle);
	printf("type(int) -> function_int_vb		0x%X\n", &function_int_vb);
	printf("type(static int) -> function_static_int	0x%X\n\n\n", &function_static_int);

	return 0;
}
int main()
{
	int result = sum(4, 5),main_var;
	static int main_variable;
	int malloc_variable = malloc(sizeof(int));
	printf("main ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ\n");

	printf("* malloc function ->	malloc		0x%X\n\n", &malloc);
	printf("type(int) -> malloc_variable		0x%X\n\n\n", &malloc_variable);

	printf("* type(function) -> main 0x%X\n\n", &main);
	printf("type(int) -> result			0x%X\n", &result);
	printf("type(int) -> main_var			0x%X\n\n\n", &main_var);
	
	printf("type(int) -> noT_static_global		0x%X\n", &noT_static_global);
	printf("type(static int) -> global_variable_one	0x%X\n", &global_variable_one);
	printf("type(static int) -> global_variable_two	0x%X\n\n\n", &global_variable_two);

	locAl_variable(1);

	printf("type(static int) -> main_variable	0x%X\n\n\n", &main_variable);

	printf("* free function -> free			0x%X\n\n\n", &free);
	free(malloc_variable);
}
.
```

#### file function.h

```cpp
#include <stdio.h>

int sum(int a, int b)
{
	
	printf("extern function ㅡㅡㅡㅡㅡㅡㅡㅡ\n");
	printf("* type(function) -> sum   0x%X\n\n",&sum);
	printf("type(int) -> a		0x%X\n", &a);
	printf("type(int) -> b		0x%X\n\n\n", &b);
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

이제 이 소스코드들을 실행시켜보면 

![image_memory](/blog_img/memory_location.png)

각 변수, 함수 들의메모리 주소가 출력되서 다 다른것을 확인할 수 가있다.

단) 변수들의 메모리 주소는 항상 같지 않고 각 영역 안 에서 메모리 주소가 달라진다.

근데 이런 프로그램 같은것들은 어디어디에 영역이 있는지 알기위해 다른 예제 설명을 살펴보자


![test](/blog_img/c_test.png)

[출저](http://contents.kocw.or.kr/document/CPP01_C%20Language%20Review.pdf)

위의 사진에서 보이는것처럼 프로그램과 메모리 역역이 있다.

char name[] = "test"; 같은 전역변수는 데이터 부분 

int main() 안에있는 int a; 같은경우에는 지역변수 이런식으로

각 변수에 영역이 존재하게된다.

