## **Лабораторна робота № 1**
# **Основи роботи з зображеннями. Найпростіші операції з зображеннями.**
- - -
## **Мета роботи:**
Ознайомитись з базовими принципами обробки зображень, що застосовуються у пакеті SciKit-Imge; вивчити основні команди пакету для зчитування, запису та виведення зображень (Matplotlib).

## **Засоби виконання роботи:**
Для виконання роботи можливо використовувати довільний iнтерпретатор мови [PYTHON](https://www.python.org/downloads/), також [IDE Anaconda](https://anaconda.org/) (Jupyter Lab / Jupyter Notebook, Spyder) або [Microsoft Visual Studio](https://visualstudio.microsoft.com).
## **Теоретичні відомості**
Зображення у SciKit-Imge предствлені масивами **ndarray**, що визначені у пакеті **NumPy**. Усі загальні маніпуляції з зображенням можливо виконувати штатними засобами  **NumPy**.
Кольорове зображення представлено 3-вимірним масивом з структурою:
- перший вимір - рядки зображення від 0 до n-1 (з верху зображення до нізу),  де n - кількість рядків,
- другий вимір - колонки зображення  від 0 до m-1 (зліва направо),  де m - кількість колонок,
- третій вимір - 3 кольори: R,G,B відповідно, задані у форматі np.uint8 (байт на колір, кожна кольорова компонента змінюється в межах **від 0 до 255**) або np.float32 (кожна кольорова компонента змінюється в межах від **0.0 до 1.0**).  

Структуру зображення за змінною **image**  можна визначити функцією
```
image.shape
```
Розмір зображення зображення за змінною **image** можна визначити  функцією
```
image.size
```
Маніпулювання зображенням зводиться до роботи  з індексами масиву.  
Наприклад, є кольорове зображення test_im з структурою 900 рядків, 900 колонок.  
Необхідно сформувати нове зображення, як частину орігінального (450*450) та повернутого на 90 градусів.
```
image_crop_ = np.zeros ((450, 450 , 3), dtype=np.uint8)
for i in  range (450):
    for j in  range (450):
        image_crop_ [i, j, :] = test_im [ j , 450-i, :]
```

## **Завдання до виконання**
1. Зчитати оригінальне зображення у відповідності за варіантом завдання.
1. Вивести структуру та розмір орігінального зображення.тВивести кольори заданого [i,j] пиксела.
1. Сформувати  **ОДНОКОЛЬОРОВЕ** зображення з  відповідного каналу орігінального зображення. Вивести на екран. Зберігти у файл в форматі JPG.
1. Сформувати **НАПІВТОНОВЕ** зображення з  орігінального зображення. Вивести на екран. Зберігти у файл в форматі BMP.
1. Сформувати **ПЕРЕТВОРЕНЕ** зображення за дпомогою перетворення оригінального зображення відповідно до завдання. Вивести на екран. Зберігти у файл в форматі JPG.

## **Варіанти завдання**
|Варіант|[Файл Зображення](/Test_Images)| [i,j] |Канал| Функція перетворення зображення|
|:-------|:-------|:--------------- |:--------|:--------
|**1**|COCO_000012774.jpg |10 15|R| Горизонтальне симетричне відображення|
|**2**|COCO_000015322.jpg  |20 15|G| Вертикальне симетричне відображення  |
|**3**|COCO_000025391.jpg  |30 15|B| Поворот  на +90 градусів |
|**4**|COCO_000028877.jpg  |40 15|R| Поворот  на -90 градусів  |
|**5**|COCO_000040672.jpg  |50 15|G| Змістити зображення по горізонталі на 100 пикселів  |
|**6**|COCO_000049940.jpg  |60 15|B| Змістити зображення по вертікалі на 200 пикселів  |
|**7**|COCO_000104571.jpg  |70 15|R| Виділити ліву половину  зображення  |
|**8**|COCO_000112142.jpg  |80 15|G| Виділити праву половину зображення    |
|**9**|COCO_000117357.jpg  |90 15|B| Виділити нижню половину зображення    |
|**10**|COCO_000170013.jpg  |100 15|R| Виділити верхню половину зображення      |
|   | |   |
|**21**|COCO_000173164.jpg |10 25|R| Горизонтальне симетричне відображення  |
|**22**|COCO_000176388.jpg |10 35|G| Вертикальне симетричне відображення |
|**23**|COCO_000180783.jpg |10 45|B| Поворот  на +90 градусів  |
|**24**|COCO_000186732.jpg |10 55|R| Поворот  на -90 градусів  |
|**25**|COCO_000224540.jpg |10 65|G| Змістити зображення по вертікалі на 200 пикселів  |
|**26**|COCO_000277143.jpg |10 75|B| Виділити нижню половину зображення      |
|**27**|COCO_000286630.jpg |10 85|R| Виділити верхню половину зображення      |
|**28**|COCO_000366557.jpg |10 95|G| Виділити ліву половину зображення      |
|**29**|COCO_000390755.jpg |10 105|B| Виділити праву половину зображення      |
|**30**|COCO_000411389.jpg |10 125|R| Виділити праву чверть зображення        |
|**31**|COCO_000495977.jpg |10 135|G| Виділити ліву чверть зображення          |

## **Типові прийоми роботи з зображенням**
- ### **Завантаження бібліотек**
На початку програми потрібно завантажити пакети та модулі, що використвуються
```
import matplotlib.pyplot as plt
import skimage.io as io
import numpy as np
```
- ### **Завантаження файлу зображення**
Для завантаження зображення з файлу рекомендуємо використовувати функцию skimage.io.imread() з пакету SciKit-Image.
Наприклад, потрібно завантажити зображення з файлу ***c:/test_image_in.jpg*** (повне імя файлу) до змінної ***test_im***
```
filename = 'с:/test_image_in.jpg'
test_im = io.imread(filename)
```
- ### **Зберігання зображення до файлу**
Для зберігання зображення  у файлі рекомендуємо використовувати функцию  skimage.io.imsave() з пакету SciKit-Image.
Наприклад, потрібно зберігти зображення представлене змінною ***my_image*** до файлу ***c:/test_image_out.jpg*** (повне імя файлу)
```
out_filename = 'c:/test_image_out.jpg'
io.imsave(out_filename,my_image_)
```
- ### **Вивід зображення на екран**
Для виводу зображення на екран, рекомендуємо використовувати можливості пакету Matplotlib.
Наприклад, потрібно вивести зображення представлене змінною ***image_out*** на екран дисплею.
```
plt.title('IMAGE')
plt.imshow(image_out)
```

### **ВАЖЛИВІ примітки використання Matplotlib**.
#### Функція Matplotlib.imshow(image) за замовчуванням відображає **ТІЛЬКИ ТРИКАНАЛЬНІ (R,G,B)** зображення.
#### Всі кольори R, G, B в  масиві *image_out* повинні бути представлені в одному з двох форматів:
#### А) як масив елементів *np.uint8* ( кожний кольір приймає значення від 0 до 255)
#### Б) як масив елементів *np.float32* ( кожний кольір приймає значенняв ід 0.0 до 1.0)

### **Приклади виконання дивись**
[Lab1 Завдання 1, 2, 3](Lab_1_Example_1.ipynb) ,  
[Lab1 Завдання 4](Lab_1_Example_2.ipynb) ,  
[Lab1 Завдання 5](Lab_1_Example_3.ipynb) .