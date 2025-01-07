## Cодержание

1. [Отчет по лабораторной работе № N](#отчет-по-лабораторной-работе--n)
2. [Критерии оценивания](#критерии-оценивания)

## Отчет по лабораторной работе № 1

#### № группы: ПМ-2403

#### Выполнил: Шопот Николай Игоревич

#### Вариант: 29

### 1. Постановка задачи

- Условия задачи

На вход программы подается шесть натуральных чисел — все
возможные расстояния между четырьмя точками на плоскости. Определить,
являются ли эти 4 точки вершинами ромба (YES/NO).

Допустим A=6, B=6, C=7, D=6, E=12, F=11. Они не могут образовать ромб, так как A, B, D не равны C

### 2. Входные и выходные данные

На вход подаются 6 натуральных чисел 
min = 1
max = 10^9
Выходные данные - YES/NO

### 3. Выбор структуры данных

Программа получает целочисленные элементы типа int

### 4. Алгоритм
 
Программа считывает значения A, B, C, D, E, F
Программа проверяет равенство сторон A, B, C, D и условие для диагоналей ромба
Программа выводит YES, когда фигура является ромбом, если нет, то NO

```markdown
    ```mermaid
        ([Начало]) --> B[/Ввести: a, b, c, d, e, f]
        B --> C{Считает расстояние, i<6}
        C -- Нет --> D{NO}
        C -- Да --> D{YES}
        D --> E([Конец])
    ``` 
```
![Image alt](https://github.com/nickshopot/README(2)/raw//LAB1/LAB1.jpg)


### 5. Программа

import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class RhombusCheck {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int[] distances = new int[6];

        System.out.println("Введите 6 натуральных чисел (расстояния):");
        for (int i = 0; i < 6; i++) {
            distances[i] = scanner.nextInt();
        }

        if (isRhombus(distances)) {
            System.out.println("YES");
        } else {
            System.out.println("NO");
        }
    }

    private static boolean isRhombus(int[] distances) {
        Map<Integer, Integer> countMap = new HashMap<>();

        // Подсчитываем количество вхождений каждого расстояния
        for (int distance : distances) {
            countMap.put(distance, countMap.getOrDefault(distance, 0) + 1);
        }

        // Проверяем условия для ромба
        int sideCount = 0;
        int diagonalCount = 0;

        for (Map.Entry<Integer, Integer> entry : countMap.entrySet()) {
            if (entry.getValue() == 4) {
                sideCount++;
            } else if (entry.getValue() == 2) {
                diagonalCount++;
            }
        }

        return sideCount == 1 && diagonalCount == 1; // Одна длина стороны и одна длина диагонали
    }
}
                                                                                                                                          | **0** - **100** |

