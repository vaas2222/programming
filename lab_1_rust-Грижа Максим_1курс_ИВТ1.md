## Лабораторная работа №1

## Тема: Rust

## Задача 1 – Вывод приветственного сообщения с использованием введённого имени

### Постановка задачи 
 Напишите программу, которая запрашивает у пользователя имя и выводит на экран привет
 ственное сообщение с использованием этого имени.

### Список идентификаторов

| Имя переменной | Тип данных  | Смысловое обозначение                                         |
|----------------|-------------|----------------------------------------------------------------|
| name           | String      | Переменная для хранения введённого имени пользователя         |
| io::stdin()    | Stdin       | Стандартный поток ввода                                       |
| read_line      | Метод       | Метод для чтения строки из потока ввода                       |
| trim()         | Метод       | Метод для удаления пробельных символов в начале и в конце     |


### Код программы
```c
use std::io::{self, Write};

fn main() {
    let mut name = String::new();
    io::stdin().read_line(&mut name).unwrap();
    let name = name.trim();
    println!("Hello, {}!", name);
}

```
### Результаты работы программы
![image](https://github.com/user-attachments/assets/ce17079f-52e7-461b-b504-1d8e3349815f)

## Задача 2 – Работа с беззнаковыми целыми типами данных: создание, изменение и вывод значения

### Постановка задачи 
 Создайте переменную типа целое беззнаковое число и выведите ее значение на экран. Явно
 укажите тип переменной. Затем измените значение переменной и снова выведите его.

### Список идентификаторов

| Имя переменной | Тип данных | Смысловое обозначение                                |
|----------------|------------|-------------------------------------------------------|
| value          | u32        | Целое беззнаковое 32-битное число                    |


### Код программы
```c
fn main() {
    let mut value: u32 = 10;
    println!("{}", value);
    value = 42;
    println!("{}", value);
}

```
### Результаты работы программы
![image](https://github.com/user-attachments/assets/7212a22b-ce9a-40da-924e-42fb49a2a7c4)

## Задача 3 – Определение длины строки с использованием пользовательской функции

### Постановка задачи 
Напишите функцию, которая принимает строку и возвращает ее длину (количество символов).
 Затем вызовите эту функцию с различными строками.

### Список идентификаторов

| Имя переменной | Тип данных     | Смысловое обозначение                                                |
|----------------|----------------|------------------------------------------------------------------------|
| s              | &str           | Строковый срез, передаваемый в функцию                                |
| examples       | [&str; 5]      | Массив строковых литералов для тестирования функции                   |
| string_length  | fn(&str) -> usize | Функция, возвращающая количество символов в строке (в Unicode-кодовых точках) |


### Код программы
```c
fn string_length(s: &str) -> usize {
    s.chars().count()
}

fn main() {
    let examples = [
        "Hello, world!",
        "Привет",
        "Rust 🦀",
        "",
        "😊👍🏼",
    ];

    for &s in &examples {
        println!("\"{}\" -> length: {}", s, string_length(s));
    }
}

```
### Результаты работы программы
![image](https://github.com/user-attachments/assets/257b6979-ce44-4aef-8cd5-1c3a7e7189c3)

## Задача 4 – Создание и использование структуры Car в языке Rust

### Постановка задачи 
Задайте структуру Car с полями brand, model и year, и создайте несколько экземпляров этой
 структуры. Выведите информацию о каждой машине на экран.

### Список идентификаторов

| Имя переменной | Тип данных     | Смысловое обозначение                                             |
|----------------|----------------|--------------------------------------------------------------------|
| Car            | struct         | Структура, представляющая автомобиль                               |
| brand          | &'static str   | Статическая строка — марка автомобиля                              |
| model          | &'static str   | Статическая строка — модель автомобиля                             |
| year           | u16            | Год выпуска автомобиля                                             |
| cars           | [Car; 3]       | Массив из трёх экземпляров структуры `Car`                         |
| car            | &Car           | Переменная для итерации по массиву `cars`                          |

### Код программы
```c
struct Car {
    brand: &'static str,
    model: &'static str,
    year: u16,
}

fn main() {
    let cars = [
        Car { brand: "Toyota", model: "Camry", year: 2020 },
        Car { brand: "Ford",   model: "Mustang", year: 1967 },
        Car { brand: "Tesla",  model: "Model S", year: 2022 },
    ];

    for car in &cars {
        println!("Brand: {}, Model: {}, Year: {}", car.brand, car.model, car.year);
    }
}

```
### Результаты работы программы
![image](https://github.com/user-attachments/assets/6256acdb-31f5-48ff-82e7-76c1365f1a02)

## Задача 5 – Вычисление N-го числа Фибоначчи с использованием рекурсии

### Постановка задачи 
 Напишите программу, которая запрашивает у пользователя число 𝑁 и выводит на экран 𝑁ное
 число Фибоначчи. Используйте рекурсию для решения этой задачи.

### Список идентификаторов

| Имя переменной | Тип данных     | Смысловое обозначение                                                  |
|----------------|----------------|-------------------------------------------------------------------------|
| fib            | fn(u32) -> u32 | Рекурсивная функция вычисления n-го числа Фибоначчи                    |
| n              | u32            | Введённое пользователем значение — индекс числа Фибоначчи              |
| buf            | String         | Буфер для хранения ввода пользователя из стандартного потока           |


### Код программы
```c
use std::io;

fn fib(n: u32) -> u32 {
    if n < 2 {
        n
    } else {
        fib(n - 1) + fib(n - 2)
    }
}

fn main() {
    let mut buf = String::new();
    io::stdin().read_line(&mut buf).unwrap();
    let n: u32 = buf.trim().parse().unwrap();
    println!("{}", fib(n));
}

```
### Результаты работы программы
![image](https://github.com/user-attachments/assets/4960ce33-04a8-4ac3-8af4-353c869998f2)

## Задача 6 – Использование перечисления (enum) для дней недели и вычисление следующего дня

### Постановка задачи 
Реализуйте перечисление DayOfWeekдляднейнедели.Напишитефункцию,котораяпринимает
 день недели и возвращает следующий день. Обработайте случаи перехода на следующий день
 недели, если текущий день– воскресенье.

### Список идентификаторов

| Имя переменной | Тип данных       | Смысловое обозначение                                                 |
|----------------|------------------|------------------------------------------------------------------------|
| DayOfWeek      | enum             | Перечисление дней недели от Monday до Sunday                          |
| next_day       | fn(DayOfWeek)    | Функция, возвращающая следующий день недели                           |
| days           | [DayOfWeek; 7]   | Массив всех дней недели                                                |
| d              | DayOfWeek        | Переменная в цикле, представляющая текущий день недели                 |

### Код программы
```c
#[derive(Debug, Copy, Clone)]
enum DayOfWeek {
    Monday,
    Tuesday,
    Wednesday,
    Thursday,
    Friday,
    Saturday,
    Sunday,
}

fn next_day(day: DayOfWeek) -> DayOfWeek {
    match day {
        DayOfWeek::Monday    => DayOfWeek::Tuesday,
        DayOfWeek::Tuesday   => DayOfWeek::Wednesday,
        DayOfWeek::Wednesday => DayOfWeek::Thursday,
        DayOfWeek::Thursday  => DayOfWeek::Friday,
        DayOfWeek::Friday    => DayOfWeek::Saturday,
        DayOfWeek::Saturday  => DayOfWeek::Sunday,
        DayOfWeek::Sunday    => DayOfWeek::Monday,
    }
}

fn main() {
    use DayOfWeek::*;
    let days = [Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday];
    for &d in &days {
        println!("{:?} → {:?}", d, next_day(d));
    }
}

```
### Результаты работы программы
![image](https://github.com/user-attachments/assets/cf305ea3-c57e-4b8b-8054-f681f89e7f97)

## Задача 7 – Работа со структурами и перечислениями: фильтрация и вывод информации о товарах

### Постановка задачи 
Создайте структуру Product с полями name, price и category, а также перечисление (enum)
 Category для категорий товаров. Напишите метод для вывода информации о продукте и
 ассоциированную функцию для подсчета общей суммы товаров в заданной категории из
 массива продуктов.

### Список идентификаторов

| Имя переменной              | Тип данных            | Смысловое обозначение                                                     |
|-----------------------------|------------------------|----------------------------------------------------------------------------|
| Category                    | enum                   | Перечисление категорий товаров                                            |
| Electronics, Grocery, Clothing | enum variants       | Значения перечисления `Category`                                          |
| fmt::Display                | trait                  | Трейд для форматированного вывода значений перечисления                   |
| Product                     | struct                 | Структура, представляющая товар                                           |
| name                        | String                 | Название товара                                                           |
| price                       | f64                    | Цена товара                                                               |
| category                    | Category               | Категория товара                                                          |
| display_info                | метод Product          | Метод вывода форматированной информации о товаре                          |
| total_price_in_category     | ассоциированная функция | Функция для подсчёта общей стоимости товаров по заданной категории        |
| products                    | Vec<Product>           | Вектор товаров                                                            |
| p                           | &Product               | Переменная для итерации по ссылкам на товары                             |
| cat                         | Category               | Текущая категория в цикле подсчёта                                        |
| total                       | f64                    | Общая стоимость товаров в заданной категории                              |


### Код программы
```c
use std::fmt;

#[derive(Debug, Clone, Copy, PartialEq, Eq)]
enum Category {
    Electronics,
    Grocery,
    Clothing,
}

impl fmt::Display for Category {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        let name = match self {
            Category::Electronics => "Electronics",
            Category::Grocery     => "Grocery",
            Category::Clothing    => "Clothing",
        };
        write!(f, "{}", name)
    }
}

struct Product {
    name: String,
    price: f64,
    category: Category,
}

impl Product {
    // Метод для вывода информации о продукте
    fn display_info(&self) {
        println!(
            "Product: {:<15} | Price: ${:>8.2} | Category: {}",
            self.name, self.price, self.category
        );
    }

    // Ассоциированная функция для подсчёта общей цены товаров в заданной категории
    fn total_price_in_category(products: &[Product], category: Category) -> f64 {
        products
            .iter()
            .filter(|p| p.category == category)
            .map(|p| p.price)
            .sum()
    }
}

fn main() {
    let products = vec![
        Product {
            name: "Smartphone".into(),
            price: 699.99,
            category: Category::Electronics,
        },
        Product {
            name: "T-shirt".into(),
            price: 19.95,
            category: Category::Clothing,
        },
        Product {
            name: "Laptop".into(),
            price: 1299.00,
            category: Category::Electronics,
        },
        Product {
            name: "Apple".into(),
            price: 0.99,
            category: Category::Grocery,
        },
        Product {
            name: "Jeans".into(),
            price: 49.50,
            category: Category::Clothing,
        },
    ];

    // Выводим информацию по каждому продукту
    println!("All products:");
    for p in &products {
        p.display_info();
    }
    println!();

    // Считаем суммарную цену для каждой категории
    for &cat in &[Category::Electronics, Category::Grocery, Category::Clothing] {
        let total = Product::total_price_in_category(&products, cat);
        println!(
            "Total price for category {:<11}: ${:.2}",
            cat, total
        );
    }
}

```
### Результаты работы программы
![image](https://github.com/user-attachments/assets/975f8c61-a9e5-49de-83d8-d7dba05c92d3)

## Задача 8 – Работа со структурами и перечислениями: фильтрация сотрудников по должности

### Постановка задачи 
Создайте структуру Employee с полями name, position, salary, а также перечисление
 Position для должностей сотрудников. Напишите функцию, которая принимает вектор
 сотрудников и возвращает вектор сотрудников заданной должности.

### Список идентификаторов

| Имя переменной         | Тип данных       | Смысловое значение                                |
|------------------------|------------------|---------------------------------------------------|
| `Position`             | `enum`           | Перечисление должностей                           |
| `Manager`              | `Position`       | Менеджер                                           |
| `Developer`            | `Position`       | Разработчик                                        |
| `Designer`             | `Position`       | Дизайнер                                           |
| `Tester`               | `Position`       | Тестировщик                                        |
| `Employee`             | `struct`         | Структура сотрудника                               |
| `name`                 | `String`         | Имя сотрудника                                     |
| `position`             | `Position`       | Должность сотрудника                               |
| `salary`               | `f64`            | Зарплата сотрудника                                |
| `filter_by_position`   | `fn`             | Функция фильтрации сотрудников по должности        |
| `employees`            | `Vec<Employee>`  | Список всех сотрудников                            |
| `devs`                 | `Vec<Employee>`  | Список сотрудников с нужной должностью             |
| `e`                    | `Employee`       | Переменная цикла при выводе сотрудников            |


### Код программы
```c
use std::fmt;

#[derive(Debug, Clone, PartialEq, Eq)]
enum Position {
    Manager,
    Developer,
    Designer,
    Tester,
}

impl fmt::Display for Position {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        let s = match self {
            Position::Manager   => "Manager",
            Position::Developer => "Developer",
            Position::Designer  => "Designer",
            Position::Tester    => "Tester",
        };
        write!(f, "{}", s)
    }
}

#[derive(Debug, Clone)]
struct Employee {
    name: String,
    position: Position,
    salary: f64,
}

fn filter_by_position(employees: &[Employee], position: Position) -> Vec<Employee> {
    employees
        .iter()
        .filter(|e| e.position == position)
        .cloned()
        .collect()
}

fn main() {
    let employees = vec![
        Employee {
            name: "Alice".into(),
            position: Position::Manager,
            salary: 80_000.0,
        },
        Employee {
            name: "Bob".into(),
            position: Position::Developer,
            salary: 70_000.0,
        },
        Employee {
            name: "Carol".into(),
            position: Position::Developer,
            salary: 75_000.0,
        },
        Employee {
            name: "Dave".into(),
            position: Position::Tester,
            salary: 60_000.0,
        },
    ];

    let devs = filter_by_position(&employees, Position::Developer);
    println!("Developers:");
    for e in devs {
        println!("  {} – {} – ${:.2}", e.name, e.position, e.salary);
    }
}

```
### Результаты работы программы
![image](https://github.com/user-attachments/assets/6fc04866-3273-4ce2-acb2-c8a41f38754b)

## Информация о студенте

Грижа Максим Игоревич ИВТ-1 ПГ-1

