# Документация разработчика

## Текст программы

### Наименование программы

**ClippingAlgorithmsApp** — приложение для реализации и визуализации алгоритмов отсечения отрезков с использованием библиотеки Qt.

### Область применения

Программа предназначена для изучения и демонстрации работы алгоритмов отсечения отрезков, таких как:
- Алгоритм Коэна-Сазерленда (Central point algorithm).
- Алгоритм Cyrus-Beck.

Она может быть использована как учебный инструмент для студентов и преподавателей, занимающихся компьютерной графикой, а также для анализа и тестирования алгоритмов отсечения.

### Назначение программы

- Реализация и визуализация алгоритмов отсечения отрезков:
  - Коэна-Сазерленда.
  - Cyrus-Beck.
- Считывание данных из файла и отображение их на графической сцене.
- Визуализация исходных отрезков, области отсечения и результатов работы алгоритмов.
- Предоставление графического интерфейса для выбора алгоритмов и взаимодействия с пользователем.

---

## Описание программы

### Структура программы

Программа состоит из следующих компонентов:

1. **Главное окно (`MainWindow`)**
   - Отображает кнопки для выбора алгоритмов отсечения.
   - Отвечает за создание и управление виджетом для рисования графических элементов.

2. **Плоскость (`plane`)**
   - Основной класс для работы с графическими данными.
   - Выполняет чтение входных данных из файла.
   - Реализует алгоритмы отсечения.
   - Отвечает за отрисовку исходных данных, области отсечения и результатов.

3. **Входной файл (`input.txt`)**
   - Содержит данные об отрезках, области отсечения и многоугольнике для алгоритма Cyrus-Beck.

---

### Основные файлы программы

#### **`main.cpp`**
Точка входа в программу. Создает объект приложения `QApplication` и главное окно `MainWindow`.

#### **`mainwindow.h` и `mainwindow.cpp`**
Класс главного окна:
- Содержит кнопки для выбора алгоритмов отсечения.
- Реализует переключение между алгоритмами через слоты:
  - `showCentral()` — для алгоритма Коэна-Сазерленда.
  - `showCirus()` — для алгоритма Cyrus-Beck.
- Использует макет `QGridLayout` для размещения виджетов.

#### **`plane.h` и `plane.cpp`**
Класс для визуализации данных и реализации алгоритмов отсечения:
- Чтение данных из файла.
- Реализация алгоритмов:
  - `clipSegments` — алгоритм Коэна-Сазерленда.
  - `Cirus` — алгоритм Cyrus-Beck.
- Отрисовка данных с использованием метода `paintEvent`.

#### **`mainwindow.ui`**
Файл интерфейса, созданный с помощью Qt Designer. Определяет компоновку главного окна и его основные элементы.

---

### Формат входных данных (`input.txt`)

Файл `input.txt` содержит данные в следующем формате:

1. Количество отрезков \( n \).
2. Координаты отрезков: \( x_1, y_1, x_2, y_2 \) для каждого отрезка.
3. Границы окна отсечения: \( X_{\text{min}}, Y_{\text{min}}, X_{\text{max}}, Y_{\text{max}} \).
4. Количество сторон многоугольника \( m \).
5. Координаты сторон многоугольника: \( x_1, y_1, x_2, y_2 \) для каждой стороны.

Пример:
```txt
6
4 9 -2 1
5 -2 7 2
-3 2 5 4
5 -4 0 9
-7 -5 3 2
4 -2 1 1
-5 -4 3 3
6
5 0 3 -4
3 -4 -1 -4
-1 -4 -3 1
-3 1 -1 4
-1 4 3 4
3 4 5 0
```

---

### Алгоритмы

#### **Алгоритм Коэна-Сазерленда**
Используется для отсечения отрезков прямоугольным окном:
1. Каждая точка отрезка кодируется с помощью четырех бит, определяющих положение точки относительно окна.
2. Если обе точки отрезка находятся внутри окна (код = 0), отрезок полностью видим.
3. Если логическое И (&) кодов двух точек не равно 0, отрезок полностью невидим.
4. В остальных случаях вычисляются точки пересечения отрезка с границами окна.

Методы:
- `clipSegments` — основной метод алгоритма.
- `getCode` — вычисляет код для точки.
- `intersectionPoint` — находит точку пересечения отрезка с границей окна.

#### **Алгоритм Cyrus-Beck**
Используется для отсечения отрезков произвольным выпуклым многоугольником:
1. Для каждой стороны многоугольника вычисляется скалярное произведение нормали к стороне и направляющего вектора отрезка.
2. Находятся параметры \( t_1 \) и \( t_2 \), определяющие видимую часть отрезка.
3. Если \( t_1 > t_2 \), отрезок полностью невидим.

Методы:
- `Cirus` — основной метод алгоритма.
- `ClipByCirus` — выполняет отсечение одного отрезка.
- `getT` — вычисляет параметр \( t \) для пересечения отрезка с одной из сторон многоугольника.
- `ScalarMultiply` — вычисляет скалярное произведение.

---

### Визуализация

Метод `paintEvent` класса `plane` отвечает за отрисовку:
- Системы координат.
- Исходных отрезков (красным цветом).
- Области отсечения (синим цветом).
- Отсеченных отрезков (зеленым цветом).

---

## Инструкция по установке и запуску

### Требования

- **Qt**: установленный Qt Creator с поддержкой C++.
- **Операционная система**: Windows, macOS или Linux.

### Установка

1. Скачайте и установите Qt Creator с официального сайта Qt.
2. Создайте новый проект Qt Widgets Application.
3. Добавьте файлы программы (`main.cpp`, `mainwindow.h`, `mainwindow.cpp`, `plane.h`, `plane.cpp`, `mainwindow.ui`).
4. Убедитесь, что файл `input.txt` находится в директории, указанной в коде.

### Запуск

1. Откройте проект в Qt Creator.
2. Соберите проект (`Ctrl+B`).
3. Запустите приложение (`Ctrl+R`).

---

## Инструкция пользователя

1. Запустите приложение.
2. Выберите алгоритм отсечения, нажав на одну из кнопок:
   - **"Central point Algorithm"** — для алгоритма Коэна-Сазерленда.
   - **"Cirus-Beck Algorithm"** — для алгоритма Cyrus-Beck.
3. Исходные данные будут считаны из файла `input.txt` и отображены на экране.
4. Результаты работы алгоритма будут визуализированы:
   - Красные линии — исходные отрезки.
   - Синие линии — область отсечения (окно или многоугольник).
   - Зеленые линии — отсеченные отрезки.

---

## Требования к техническим характеристикам

- **Процессор**: с тактовой частотой не менее 1 ГГц.
- **Оперативная память**: не менее 512 МБ.
- **Дисплей**: с разрешением не менее 1024x768 пикселей.

---

## Обработка ошибок

- Если файл `input.txt` отсутствует или имеет некорректный формат, программа завершится с ошибкой.
- При отсутствии данных для отрисовки выводится сообщение в консоль.

---

## Заключение

Программа предоставляет удобный инструмент для изучения алгоритмов отсечения отрезков. Ее структура и документация соответствуют стандартам, что облегчает сопровождение и дальнейшее развитие.