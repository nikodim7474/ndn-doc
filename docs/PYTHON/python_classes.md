## 📚 Корисні ресурси

- [Офіційна документація Python 3.7: Classes](https://docs.python.org/3.7/tutorial/classes.html)
- [First Look at Classes (офіційно)](https://docs.python.org/3.7/tutorial/classes.html#a-first-look-at-classes)
- [TutorialsPoint — Python Classes & Objects](https://www.tutorialspoint.com/python/python_classes_objects.htm)

## 🔑 **ТЕРМІНИ**

* **Клас** — це шаблон або креслення для створення об’єктів. Він описує, які властивості (атрибути) та поведінку (методи) матимуть об’єкти (екземпляри) цього класу.
* **Об'єкт** - екземпляр класу

* **self** — це перший параметр усіх методів екземпляра класу в Python. Через нього метод має доступ до атрибутів і методів конкретного об’єкта.Хоча слово self — не зарезервоване (можна назвати як завгодно), це прийнятий стандарт Python, і його завжди потрібно писати першим аргументом у методах об'єкта.

* **класові змінні (class variables) або атрибути класу**
    * Зберігаються на рівні класу.
    * Спільні для всіх екземплярів класу.
    * Якщо змінити їх через клас — зміни побачать усі екземпляри.
    * Оголошуються всередині класу, але поза методами.

```
class Dog:
    species = "Canis lupus"  # класова змінна

    def __init__(self, name):
        self.name = name  # атрибут екземпляра

d1 = Dog("Rex")
d2 = Dog("Buddy")

print(d1.species)  # Canis lupus
print(d2.species)  # Canis lupus

Dog.species = "Canis familiaris"
print(d1.species)  # Canis familiaris
print(d2.species)  # Canis familiaris
```
    
* **атрибути екземпляра (instance attributes)**
    * Створюються в методі __init__ або динамічно.
    * Унікальні для кожного об’єкта (екземпляру класу).
    * Зберігаються в словнику __dict__ кожного об'єкта.


```python
class Dog:
    def __init__(self, name):
        self.name = name  # атрибут екземпляра

d1 = Dog("Rex")
d2 = Dog("Buddy")

print(d1.name)  # Rex
print(d2.name)  # Buddy
```

* **Метод** — це функція, яка належить до класу і працює з його об'єктами (екземплярами) або з самим класом. Розрізняють:
    * Звичайний метод (instance method)
        * Працює з конкретним об'єктом
        * в якості параметра отримує self 
     * Метод класу (class method)
        * Працює з самим класом
        * в якості параметра отримує cls
    * Статичний метод (static method)
        *  Просто утилітна функція в класі

Звичайний метод (instance method)
```python
class Person:
    def __init__(self, name):
        self.name = name

    def say_hello(self):  # звичайний метод
        print(f"Привіт, я {self.name}")

p = Person("Олена")
p.say_hello()  # Привіт, я Олена
```
Метод класу (class method)   
```python
class Cat:
    species = "Кіт"

    @classmethod
    def get_species(cls):
        print(f"Всі належать до: {cls.species}")

Cat.get_species()  # Всі належать до: Кіт      
```
Статичний метод (static method)    
```python

class Math:
    @staticmethod
    def add(a, b):
        return a + b

print(Math.add(3, 5))  # 8
```

## 🔧 **СТАНДАРТНІ МЕТОДИ**

### \_\_new\_\_
Цей метод є реальним конструктором об'єкту (екземпляру класу). Викликається автоматично при створенні функції. І на цьому етапі створюється екземпляр

### \_\_init\_\_
Цей метод в джерелах називається методом конструктором, хоча насправді ним не являється. А насправді є методом ініціалізатором. Бо викликається після методу \_\_new\_\_. При виклику методу вже можна отримати id від селф. Тобто на цей момент об'єкт вже існує.  який викликається автоматично при створенні екземпляру (об'єкту) класу. 

### \_\_del\_\_
Викликається автоматично, при знищенні екземпляру

### \_\_str\_\_ 
Перезаписує логіку прінта об'єкта. Перезаписує яка саме вивожиться інфа для виразу print(obj)

### \_\_repr\_\_ 
Робить те ж саме, що і \_\_str\_\_  Відмінність в тому, що викликається після


* першим параметром цього методу завжди іде self, що вказує на екземпляр
* наступним ідуть довільні параметри, які передаватимуться при створенні об'єкта

## 🧱 **СТВОРЕННЯ КЛАСУ**

```python
class TestClass():
    counter = 0 #змінна(атрибут) класу

    def __init__(self, name, surname): №
        self.name = name #атрибут екземпляру класу, унікальний для кожного
        self.surname = surname


```

## 🧱 **СТВОРЕННЯ ЕКЗЕМПЛЯРУ КЛАСУ**

```python
test_obj_1 = TestClass('Ihor', 'Petrenko')

test_obj_2 = TestClass('Solomia', 'Drizd')

#виклик атрибутів екземплярів (окремих об'єктів)
print(test_obj_1.name)
#Виведе Ihor
print(test_obj_2.name)
#Виведе Solomia

```

## **СТВОРЕННЯ КАСТОМНОГО МЕТОДУ КЛАСУ**

* якщо ми плануємо в кастомному методі працювати з атрибутами екземпляру, то першим параметром методу вказується **self**

```python
class TestClass():
    counter = 0 #змінна(атрибут) класу

    def __init__(self, name, surname): 
        self.name = name #атрибут екземпляру класу, унікальний для кожного
        self.surname = surname

    def do_something(self): #кастомний метод
        print(f'Name: {self.name}')
        print(f'Surname: {self.surname}')


```

## ✏️ **ЗМІНА АТРИБУТІВ**

```python
class Person:
    def __init__(self, name):
        self.name = name

    def greet(self): # метод 
        print(f"Hello, {self.name}!")

p = Person("Alice")
p.greet()  # Hello, Alice!

p.age = 30         # Додаємо новий атрибут
p.name = "Bob"     # Змінюємо існуючий
del p.age          # Видаляємо атрибут
```

## **НАСЛІДУВАННЯ**
**Типи наслідування:**

* Однорівненве (Single) - [Parent ← Child] - Клас доповнює або змінює єдиного батька
* Багаторівневе (Multilevel) [Grandparent ← Parent ←Child] Кілька рівнів спадкоємності
* Ієрархічне (Hierarchical) - [Parent ← {Child1, Child2}] -  Багато дочірніх класів з однаковою базовою поведінкою
* Множинне (Multiple) - [{Base1, Base2} → Sub] - Об’єднання функцій кількох незалежних батьків
* Гібридне (Hybrid) -  Змішана Комбінація multilevel, multiple, hierarchical за потребою

```python
class Animal:
    def speak(self):
        print("Some sound")

class Dog(Animal):
    def speak(self):
        print("Bark!")

d = Dog()
d.speak()  # Bark!
```

* якщо ми не будемо перевизначати логіку метода-ініціалізатора, то нічого не дописуємо в класу нащадкові
* якщо ми плануємо переписувати метод-ініціалізатор (наприклад, для того щоб передавати додаткові аргументи при ініціалізації екземпляру), треба вказувати в новому методі вираз super().\_\_init()\_\_ ЯЯкщо його не застосувати то не буде виконано логіки методу-ініціалізатору батьківського-класу 

```python
class Animal:
    def __init__(self, type):
        self.type = type

    def speak(self):
        print("Some sound")

class Dog(Animal):
    def __init__(self, type, sub_type):
        super().init(type)
        self.sub_type = sub_type

    def speak(self):
        print("Bark!")

d = Dog("савець", 'canis lupus')
print(d.type)
print(d.sub_type)
d.speak()  # Bark!
```

### **MRO**

#### C3 Linearization
<img src='../RES/classes_2.png'></img>
```python
class H:
    pass

class D(H):
    pass
class E(H):
    pass
class F(H):
    pass
class G(H):
    pass
class B(D, E):
    pass
class C(F, G):
    pass
class A(B, C):
    pass

def show_mro(cls_name):
    return [c.__name__ for c in cls_name.mro()]

print(*show_mro(A), sep = ' -> ')
```
```python
# ВИВОДИТЬ
A -> B -> D -> E -> C -> F -> G -> H -> object
```


<img src='../RES/classes_1.png'></img>
```python
class O:
    pass
class C(O):
    pass
class A(O):
    pass
class B(O):
    pass
class D(O):
    pass
class E(O):
    pass
class K1(C, A, B):
    pass
class K2(A, D):
    pass
class K3(B, D, E):
    pass
class Z(K1, K2, K3):
    pass
def show_mro(cls_name):
    return [c.__name__ for c in cls_name.mro()]

print(*show_mro(Z), sep = ' -> ')
```
```python
# ВИВОДИТЬ
Z -> K1 -> C -> K2 -> A -> K3 -> B -> D -> E -> O -> object
```



## **Агрегація і композиція**


