# systemprograming
# 💡 C언어 비트 계산기

이 프로그램은 C언어를 이용해 **0~255 사이의 숫자**를 입력받아 다음 기능을 수행합니다:

- 입력 숫자의 8비트 2진수 출력
- 1의 개수 계산
- 상위 4비트 출력

---

## 📂 소스 코드 (`bit_program.c`)

```c
#include <stdio.h>

int main() {
    int num;
    int i, count = 0;

    // 사용자 입력 받기
    printf("0에서 255 사이의 정수를 입력하세요: ");
    scanf("%d", &num);

    // 입력값 유효성 검사
    if (num < 0 || num > 255) {
        printf("입력 값이 유효하지 않습니다. (0~255 사이여야 합니다)\n");
        return 1;
    }

    printf("2진수(8비트): ");
    for (i = 7; i >= 0; i--) {
        int bit = (num >> i) & 1;
        printf("%d", bit);
        if (bit == 1) count++;
    }

    printf("\n1의 개수: %d개\n", count);

    // 상위 4비트 출력
    int high4 = (num >> 4) & 0x0F;
    printf("상위 4비트(2진수): ");
    for (i = 3; i >= 0; i--) {
        printf("%d", (high4 >> i) & 1);
    }

    printf("\n");

    return 0;
}

아래는 프로그램을 컴파일하고 실행한 결과

```bash
$ gcc bit_program.c -o bit_program
$ ./bit_program
0에서 255 사이의 정수를 입력하세요: 173
2진수(8비트): 10101101
1의 개수: 5개
상위 4비트(2진수): 1010
