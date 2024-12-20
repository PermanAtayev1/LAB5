# Пользовательская документация

## 1. Введение

Программа **ClippingAlgorithmsApp** предназначена для визуализации работы алгоритмов отсечения отрезков. Приложение позволяет пользователю выбирать алгоритмы, отображать исходные данные, область отсечения, а также результаты работы алгоритмов. 

Доступны два основных алгоритма отсечения:
- Алгоритм Коэна-Сазерленда.
- Алгоритм Cyrus-Beck.

Программа предоставляет удобный графический интерфейс, что делает её полезной для студентов, преподавателей и всех, кто изучает компьютерную графику.

---

## 2. Системные требования

- **Операционная система**: Windows 7 и выше, macOS, Linux.
- **Программное обеспечение**: Qt Framework версии 5.12 или выше.
- **Аппаратные требования**:
  - Процессор с тактовой частотой не менее 1 ГГц.
  - Оперативная память: не менее 512 МБ.
  - Дисплей с разрешением не менее 1024x768 пикселей.
  - Свободное место на диске: 50 МБ.

---

## 3. Установка

### 3.1 Установка Qt

1. Перейдите на официальный сайт Qt: [https://www.qt.io](https://www.qt.io).
2. Скачайте и установите последнюю версию Qt Framework.
3. Убедитесь, что установлены компоненты для разработки на C++.

### 3.2 Скачивание программы

1. Скачайте исходный код программы (файлы `main.cpp`, `mainwindow.h`, `mainwindow.cpp`, `plane.h`, `plane.cpp`, `mainwindow.ui`) и входной файл `input.txt`.
2. Сохраните файлы в одной директории.

### 3.3 Сборка и запуск программы

1. Откройте Qt Creator.
2. Создайте новый проект Qt Widgets Application.
3. Добавьте файлы программы в проект.
4. Соберите проект (нажмите `Ctrl+B`).
5. Запустите приложение (нажмите `Ctrl+R`).

---

## 4. Использование приложения

### 4.1 Выбор алгоритма

После запуска программы откроется главное окно с двумя кнопками:
- **"Central point Algorithm"** — для выбора алгоритма Коэна-Сазерленда.
- **"Cirus-Beck Algorithm"** — для выбора алгоритма Cyrus-Beck.

Нажмите на одну из кнопок, чтобы перейти к визуализации выбранного алгоритма.

---

### 4.2 Работа с входными данными

Программа считывает данные из файла `input.txt`. Убедитесь, что файл находится в указанной директории и имеет следующий формат:

1. Количество отрезков \( n \).
2. Координаты отрезков: \( x_1, y_1, x_2, y_2 \) для каждого отрезка.
3. Границы окна отсечения: \( X_{\text{min}}, Y_{\text{min}}, X_{\text{max}}, Y_{\text{max}} \).
4. Количество сторон многоугольника \( m \).
5. Координаты сторон многоугольника: \( x_1, y_1, x_2, y_2 \) для каждой стороны.

Пример содержимого файла `input.txt`:
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

### 4.3 Визуализация

После выбора алгоритма программа выполнит следующие действия:
1. Считает данные из файла `input.txt`.
2. Отобразит:
   - Исходные отрезки (красным цветом).
   - Область отсечения:
     - Прямоугольное окно (для алгоритма Коэна-Сазерленда) — синим цветом.
     - Выпуклый многоугольник (для алгоритма Cyrus-Beck) — синим цветом.
   - Отсеченные отрезки (зеленым цветом).

### 4.4 Обновление данных

Для использования новых данных:
1. Измените содержимое файла `input.txt`.
2. Перезапустите приложение.

---

## 5. Пример использования

### Пример 1: Алгоритм Коэна-Сазерленда

1. Откройте файл `input.txt` и убедитесь, что он содержит данные о прямоугольном окне отсечения.
2. Запустите приложение.
3. Нажмите кнопку **"Central point Algorithm"**.
4. Программа отобразит:
   - Красные линии — исходные отрезки.
   - Синее прямоугольное окно — область отсечения.
   - Зеленые линии — отсеченные отрезки.

### Пример 2: Алгоритм Cyrus-Beck

1. Откройте файл `input.txt` и убедитесь, что он содержит данные о выпуклом многоугольнике.
2. Запустите приложение.
3. Нажмите кнопку **"Cirus-Beck Algorithm"**.
4. Программа отобразит:
   - Красные линии — исходные отрезки.
   - Синий многоугольник — область отсечения.
   - Зеленые линии — отсеченные отрезки.

---

## 6. Обратная связь

Если у вас возникли вопросы или вы обнаружили ошибку в работе программы, пожалуйста, свяжитесь с разработчиком:

- Email: **imprmnata00@gmail.com**

---

## 7. Приложения

### Приложение 1. Список реализованных алгоритмов

1. **Алгоритм Коэна-Сазерленда**:
   - Используется для отсечения отрезков прямоугольным окном.
   - Подходит для простых задач с фиксированной областью отсечения.

2. **Алгоритм Cyrus-Beck**:
   - Используется для отсечения отрезков выпуклым многоугольником.
   - Более универсальный алгоритм, подходящий для сложных областей отсечения.

### Приложение 2. Формат входных данных

Пример файла `input.txt`:
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

## 8. Лицензия

Программа распространяется на условиях лицензии MIT. Вы можете использовать, изменять и распространять её свободно при условии сохранения авторских прав в исходном коде.

---

## 9. Дополнительные материалы

- [Документация Qt](https://doc.qt.io)
- [Руководство по алгоритмам отсечения](https://en.wikipedia.org/wiki/Line_clipping)

---

## 10. Обновления документации

Документация обновляется с каждым новым релизом программы. Рекомендуется проверять актуальность документации в репозитории проекта.