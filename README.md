# C언어 기초

## 상수
상수: 프로그램 실행 중에 값이 변하지 않는 데이터
```c
#include <stdio.h>

#define PI 3.14159        // 매크로 상수 정의
const int MAX_SIZE = 100; // const 키워드를 사용한 상수 선언

int main() {
    // 리터럴 상수 사용 예
    printf("원주율은 %f\n", PI);
    printf("최대 크기는 %d\n", MAX_SIZE);
    return 0;
}
```

## 변수
변수: 프로그램 실행 중에 값이 변할 수 있는 메모리 공간
```c
#include <stdio.h>

int main() {
    // 다양한 데이터 타입의 변수 선언
    int age = 25;         // 정수형 변수
    float height = 175.5; // 실수형 변수
    char grade = 'A';     // 문자형 변수
    
    printf("나이: %d\n", age);
    printf("키: %.1f\n", height);
    printf("등급: %c\n", grade);
    return 0;
}
```

## 데이터 입력
사용자로부터 데이터를 입력받는 방법
```c
#include <stdio.h>

int main() {
    int num;
    char name[50];
    
    // 정수 입력 받기
    printf("숫자를 입력하세요: ");
    scanf("%d", &num);
    while(getchar() != '\n');  // 입력 버퍼 비우기
    
    // 문자열 입력 받기
    printf("이름을 입력하세요: ");
    scanf("%49s", name);    // 배열 크기보다 1 작은 값으로 제한
    
    printf("입력된 숫자: %d\n", num);
    printf("입력된 이름: %s\n", name);
    return 0;
}
```

## 산술, 관계, 논리 연산자
다양한 연산을 수행하는 연산자
```c
#include <stdio.h>

int main() {
    // 산술 연산자: +, -, *, /, %
    int a = 10, b = 3;
    printf("덧셈: %d\n", a + b);
    printf("나눗셈: %d\n", a / b);
    printf("나머지: %d\n", a % b);
    
    // 관계 연산자: >, <, >=, <=, ==, !=
    printf("a가 b보다 큰가? %d\n", a > b);
    
    // 논리 연산자: &&, ||, !
    int x = 1, y = 0;
    printf("AND 연산: %d\n", x && y);
    printf("OR 연산: %d\n", x || y);
    return 0;
}
```

## 비트 연산자와 그외 연산자
비트 단위의 연산과 기타 연산자
```c
#include <stdio.h>

int main() {
    // 비트 연산자: &, |, ^, ~, <<, >>
    unsigned char a = 0x0F; // 00001111
    unsigned char b = 0xA5; // 10100101
    
    printf("AND: %02X\n", a & b);
    printf("OR: %02X\n", a | b);
    printf("XOR: %02X\n", a ^ b);
    printf("Left Shift: %02X\n", a << 1);
    
    // 기타 연산자: sizeof, 조건 연산자
    int x = 10;
    printf("x의 크기: %zu\n", sizeof(x));  // %lu 대신 %zu 사용
    printf("조건 연산: %d\n", x > 5 ? 1 : 0);
    return 0;
}
```

## if문
조건에 따른 분기를 처리하는 제어문
```c
#include <stdio.h>

int main() {
    int score = 85;
    
    // 단순 if문
    if (score >= 60) {
        printf("합격입니다!\n");
    }
    
    // if-else문
    if (score >= 90) {
        printf("A등급\n");
    } else if (score >= 80) {
        printf("B등급\n");
    } else {
        printf("C등급\n");
    }
    return 0;
}
```

## switch - case 문
다중 분기를 처리하는 제어문
```c
#include <stdio.h>

int main() {
    char grade = 'B';
    
    switch (grade) {
        case 'A':
            printf("훌륭합니다!\n");
            break;
        case 'B':
            printf("좋습니다!\n");
            break;
        case 'C':
            printf("노력하세요!\n");
            break;
        default:
            printf("잘못된 등급입니다.\n");
    }
    return 0;
}
```

## while문
조건이 참인 동안 반복 실행하는 반복문
```c
#include <stdio.h>

int main() {
    int i = 1;
    int sum = 0;
    
    // 1부터 10까지의 합 계산
    while (i <= 10) {
        sum += i;
        i++;
    }
    
    printf("1부터 10까지의 합: %d\n", sum);
    return 0;
}
```

## for 문
초기식, 조건식, 증감식을 포함하는 반복문
```c
#include <stdio.h>

int main() {
    int i, factorial = 1;
    
    // 5 팩토리얼 계산
    for (i = 1; i <= 5; i++) {
        factorial *= i;
    }
    
    printf("5! = %d\n", factorial);
    return 0;
}
```

## do while문
조건 검사 전에 최소 한 번은 실행되는 반복문
```c
#include <stdio.h>

int main() {
    int num;
    
    do {
        printf("양수를 입력하세요: ");
        scanf("%d", &num);
        while(getchar() != '\n');  // 입력 버퍼 비우기
    } while (num <= 0);   // 양수가 입력될 때까지 반복
    
    printf("입력된 양수: %d\n", num);
    return 0;
}
```

## 함수 작성과 사용
코드를 모듈화하고 재사용하기 위한 함수
```c
#include <stdio.h>

// 함수 선언
int add(int a, int b);
void printMessage(void);

int main() {
    // 함수 호출
    int result = add(5, 3);
    printf("덧셈 결과: %d\n", result);
    
    printMessage();
    return 0;
}

// 함수 정의
int add(int a, int b) {
    return a + b;
}

void printMessage(void) {
    printf("함수가 호출되었습니다!\n");
}
```

## 배열의 선언과 사용
동일한 타입의 데이터를 연속적으로 저장하는 자료구조
```c
#include <stdio.h>

int main() {
    // 배열 선언과 초기화
    int numbers[5] = {1, 2, 3, 4, 5};
    
    // 배열 요소 접근
    for (int i = 0; i < 5; i++) {
        printf("%d번째 요소: %d\n", i+1, numbers[i]);
    }
    
    // 2차원 배열
    int matrix[2][3] = {
        {1, 2, 3},
        {4, 5, 6}
    };
    return 0;
}
```

## 문자를 저장하는 배열
문자열을 저장하고 처리하는 문자 배열
```c
#include <stdio.h>
#include <string.h>

int main() {
    // 문자 배열 선언과 초기화
    char str1[10] = "Hello";
    char str2[10];
    
    // 문자열 복사 (보안 강화)
    strncpy(str2, str1, sizeof(str2) - 1);
    str2[sizeof(str2) - 1] = '\0';  // null 종료 문자 보장
    
    // 문자열 길이
    printf("문자열 길이: %zu\n", strlen(str1));  // %lu 대신 %zu 사용
    
    // 문자열 비교
    if (strcmp(str1, str2) == 0) {
        printf("두 문자열이 같습니다.\n");
    }
    return 0;
}
```

## 포인터
메모리 주소를 저장하고 참조하는 변수
```c
#include <stdio.h>

int main() {
    int num = 10;
    int *ptr;     // 포인터 선언
    
    ptr = &num;   // 주소 할당
    
    printf("num의 값: %d\n", num);
    printf("num의 주소: %p\n", (void*)&num);
    printf("ptr이 가리키는 값: %d\n", *ptr);
    
    // 포인터를 통한 값 변경
    *ptr = 20;
    printf("변경된 num의 값: %d\n", num);
    return 0;
}
```
