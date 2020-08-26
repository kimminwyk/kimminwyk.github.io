---
layout: post
title:  "memory structure"
date:   2020-08-25 20:00
categories: blog
---

#### 메모리 구조는 어떻게 되어있는가?

![memory](/blog_img/memory_structure.png)

먼저 크게 메모리 구조에는 code 영역 , 데이터 영역 , 힙 역역 , 스택 영역으로 나뉘어져있다.

__memory code__

__memory data__

__memory heap__

__memory stack__

```cpp

#### file consloe_test.c

#include "code.h"
#include "function.h"

static int global_variable_one = 0, global_variable_two = 0;
int noT_static_global = 0;

int locAl_variable(int variaBle) 
{
	int function_int_vb = 0;
	static int function_static_int = 0;

	printf("type(int) ->		0x%X\n", &variaBle);
	printf("type(int) ->		0x%X\n", &function_int_vb);
	printf("type(static int) ->	0x%X\n\n\n", &function_static_int);

	return 0;
}
int main()
{
	int result = sum(4, 5),main_var;
	static int main_variable;

	printf("type(int) ->		0x%X\n", &result);
	printf("type(int) ->		0x%X\n\n\n", &main_var);
	
	printf("type(int) ->		0x%X\n", &noT_static_global);
	printf("type(static int) ->	0x%X\n", &global_variable_one);
	printf("type(static int) ->	0x%X\n\n\n", &global_variable_two);

	locAl_variable(1);

	printf("type(static int) ->	0x%X\n", &main_variable);
}

```

```cpp

#### file function.h

int sum(int a, int b)
{
	return a + b;
}

```

```cpp

#### file code.h

#include <stdio.h>

extern int sum(int a, int b);

```