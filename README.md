```c
#define _CRT_SECURE_NO_DEPRECATE
#include <stdio.h>
#include <locale.h>
#define size 15

int check(double x, double y);
int fi(double st, char sim);
int pr(double x, double y);

int main() {
    setlocale(LC_CTYPE, "RUS");
    double x = 0;
    double y = 0;
    double st = 3.0 / size;
    char sim;
    int choice;
    do {
        printf("Меню\n");
        printf("1 - Проверка попадания точки в область\n");
        printf("2 - Нарисовать фигуру\n");
        printf("0 - Выход\n");
        printf("Ваш выбор: ");
        scanf("%d", &choice);
        switch (choice) {
        case 1:
            pr(x, y);
            break;
        case 2:
            printf("Введите символ: ");
            scanf(" %c", &sim);
            fi(st, sim);
            break;
        case 0:
            printf("Завершение работы\n");
            break;
        default:
            printf("Неверный пункт меню\n");
            break;
        }
    } while (choice != 0);
    return 0;
}

int check(double x, double y) {
    if (x * x + y * y <= 4 && y >= x && x >= 0) {
        return 1;
    }
    else {
        return 0;
    }
}

int fi(double st, char sim) {
    for (int row = size - 1; row >= 0; row--) {
        for (int l = 0; l < 5; l++) {
            putchar(' ');
        }
        for (int col = 0; col < size; col++) {
            double x = col * st;
            double y = row * st;
            if (check(x, y) == 1) {
                putchar(sim);
            }
            else {
                putchar(' ');
            }
        }
        printf("\n");
    }
    for (int p = 0; p < 3; p++) {
        printf("\n");
    }
    return 0;
}

int pr(double x, double y) {
    printf("Проверка попадания точки в заштрихованную область\n");
    printf("Введите координаты точки (x и y): ");
    scanf("%lf %lf", &x, &y);
    if (check(x, y) == 1) {
        printf("Точка (%.2lf, %.2lf) попадает в заштрихованную область.\n", x, y);
    }
    else {
        printf("Точка (%.2lf, %.2lf) не попадает в заштрихованную область.\n", x, y);
    }
    return 0;
}
```
