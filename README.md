# js-module
# ⚡ Модуль JS: Основы программирования и логика

В этом репозитории собраны все мои практические задания и домашние работы по модулю JavaScript в одном скрипте. 

## 📚 Изученные темы
- Переменные (`let`, `const`), типы данных (`typeof`), операторы сравнения (`==`, `===`).
- Условия (`if/else`, `||`, `&&`), интерполяция строк.
- Массивы и их методы (`push`, `pop`, `length`).
- Циклы (`for`), генерация случайных чисел (`Math.random`, `Math.floor`).
- Функции, параметры и `return`.

---

## 💻 Полный код (Class Work + Home Work)

```javascript
/* ==========================================
   1. БАЗОВЫЕ ОПЕРАЦИИ И ТИПЫ ДАННЫХ
   ========================================== */
let x = 5;
console.log(x);
x = 6;
console.log(x);

const y = 5;
// y = 6; // Ошибка: Assignment to constant variable
console.log(y);

const num = 5;
console.log(typeof num); // number

const str = "5";
console.log(typeof str); // string

const isSunny = true;
console.log(typeof isSunny); // boolean

const f = function() {}
console.log(typeof f); // function

const arr = []; 
console.log(typeof arr); // object

const o = {}
console.log(typeof o); // object

console.log(1 == "1"); // true (нестрогое)
console.log(1 === "1"); // false (строгое)

const fullName = "John Smith";
const age = 19;
console.log(fullName + " is " + age + " years old"); // Конкатенация
console.log(`${fullName} is ${age} years old`); // Интерполяция

/* ==========================================
   2. УСЛОВИЯ И ФУНКЦИИ
   ========================================== */
const a = 5;
const b = 6;

if (a == 5 || b == 5) {
    console.log("OK (OR)");
}
if (a == 5 && b == 5) {
    console.log("OK (AND)");
}

function ab2() {
    const a = 5;
    const b = 6;
    return a + b;
}
console.log(ab2()); // 11

function ab3(a, b) {
    return a + b;
}
console.log(ab3(5, 6)); // 11

/* ==========================================
   3. МАССИВЫ И ЦИКЛЫ
   ========================================== */
const cars = ["MB", "BMW", "AUDI", "FORD"];
console.log(cars[1]); // BMW
console.log(cars.length); // 4

cars.push("TESLA");
console.log(cars);

cars.pop(); // удаляет последний элемент
console.log(cars);

const fruits = ["APPLE", "PEAR", "WATERMELON", "MELON", "GRAPE"];
for (let i = 0; i < fruits.length; i++) {
    console.log(fruits[i]); 
}

// Генерация случайных чисел
const randomNum = Math.floor(Math.random() * 5);
console.log(`Random number is: ${randomNum}`);

const colors = ["Black", "White", "Blue", "Green", "Red"];
const randomColorIndex = Math.floor(Math.random() * colors.length);
console.log(`Random color is: ${colors[randomColorIndex]}`);


/* ==========================================
   4. ДОМАШНИЕ ЗАДАНИЯ
   ========================================== */

// Задание 1: Времена года (getSeason)
function getSeason(month, temperature) {
    if (typeof month !== 'number' || typeof temperature !== 'number') {
        return "Ошибка: Неверный Тип данных";
    }
    if (month < 1 || month > 12) {
        return "Ошибка - такого месяца нету";
    }
    
    if ((month === 12 || month === 1 || month === 2) && temperature <= 5) {
        return "Зима";
    } else if (month >= 3 && month <= 5 && temperature < 20) {
        return "Весна";
    } else if (month >= 6 && month <= 8 && temperature > 20) {
        return "Лето";
    } else if (month >= 9 && month <= 11 && temperature >= 5 && temperature <= 20) {
        return "Осень";
    } else {
        return "Несоответствие сезона";
    }
}
console.log("Сезон:", getSeason(12, 0));


// Задание 2: Калькулятор (calculator)
function calculator(a, b, operator) {
    if (typeof a !== 'number' || typeof b !== 'number') {
        return "Ошибка: Параметры должны быть числами";
    }
    switch (operator) {
        case '+': return a + b;
        case '-': return a - b;
        case '*': return a * b;
        case '/': 
            if (b === 0) return "Ошибка: на ноль делить нельзя";
            return a / b;
        default: return "Ошибка: неизвестный оператор";
    }
}
console.log("Калькулятор:", calculator(10, 0, '/'));


// Задание 3 и 4: Добавление чисел и анализ (addNumber, calculateAverage, analyzeNumbers)
const numbersArray = [];

function addNumber(number) {
    numbersArray.push(number);
    console.log(`Число ${number} добавлено в массив.`);
}

function calculateAverage() {
    if (numbersArray.length === 0) return 0;
    const sum = numbersArray.reduce((acc, curr) => acc + curr, 0);
    console.log(`Среднее значение: ${(sum / numbersArray.length).toFixed(2)}`);
}

function analyzeNumbers() {
    let positive = 0, negative = 0, zero = 0;
    for (let i = 0; i < numbersArray.length; i++) {
        if (numbersArray[i] > 0) positive++;
        else if (numbersArray[i] < 0) negative++;
        else zero++;
    }
    console.log(`Анализ: Положительных: ${positive}, Отрицательных: ${negative}, Нулей: ${zero}`);
}
addNumber(10);
addNumber(-5);
addNumber(0);
calculateAverage();
analyzeNumbers();


// Задание 5: Камень, ножницы, бумага
function rockPaperScissors(playerChoice) {
    const choices = ['rock', 'paper', 'scissors'];
    const computerChoice = choices[Math.floor(Math.random() * 3)];
    console.log(`Вы: ${playerChoice}, Компьютер: ${computerChoice}`);

    if (playerChoice === computerChoice) return "Ничья";
    if (
        (playerChoice === 'rock' && computerChoice === 'scissors') ||
        (playerChoice === 'paper' && computerChoice === 'rock') ||
        (playerChoice === 'scissors' && computerChoice === 'paper')
    ) {
        return "Ты выйграл";
    }
    return "Ты проиграл";
}
console.log("Игра:", rockPaperScissors('rock'));


// Задание 6: Угадай число
function guessNumber(secretNumber, userNumber) {
    if (userNumber === secretNumber) return "Угадал";
    if (userNumber > secretNumber) return "Число больше";
    return "Число меньше";
}
console.log("Угадайка:", guessNumber(50, 75));


// Задание 7: Генератор паролей
const charset = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()_+";
function generatePassword(length) {
    let password = "";
    for (let i = 0; i < length; i++) {
        password += charset[Math.floor(Math.random() * charset.length)];
    }
    return password;
}
console.log("Пароль:", generatePassword(10));


// Задание 8: Система управления рейсами
const flights = [];

function addFlight(flightNumber, destination, departureTime, capacity) {
    flights.push({ flightNumber, destination, departureTime, capacity, passengers: [] });
    console.log(`Рейс ${flightNumber} добавлен.`);
}

function cancelFlight(flightNumber) {
    const index = flights.findIndex(f => f.flightNumber === flightNumber);
    if (index !== -1) {
        flights.splice(index, 1);
        console.log(`Рейс ${flightNumber} отменен.`);
    } else {
        console.log(`Рейс ${flightNumber} не найден.`);
    }
}

function registerPassenger(flightNumber, passengerName) {
    const flight = flights.find(f => f.flightNumber === flightNumber);
    if (flight) {
        if (flight.passengers.length < flight.capacity) {
            flight.passengers.push(passengerName);
            console.log(`Пассажир ${passengerName} зарегистрирован на рейс ${flightNumber}.`);
        } else {
            console.log(`На рейс ${flightNumber} нет свободных мест.`);
        }
    } else {
        console.log(`Рейс ${flightNumber} не найден.`);
    }
}

function findFlightByNumber(flightNumber) {
    const flight = flights.find(f => f.flightNumber === flightNumber);
    if (flight) {
        console.log(`Рейс: ${flight.flightNumber}, Куда: ${flight.destination}, Время: ${flight.departureTime}, Мест: ${flight.capacity}`);
    }
}

function showAllFlights() {
    console.log("Все рейсы:");
    flights.forEach(f => console.log(`- ${f.flightNumber} в ${f.destination}`));
}

function showFlightPassengers(flightNumber) {
    const flight = flights.find(f => f.flightNumber === flightNumber);
    if (flight) console.log(`Пассажиры рейса ${flightNumber}:`, flight.passengers);
}

// Тест системы рейсов
const flights = [];
function addFlight(flightNumber, destination, departureTime, capacity){
    console.log(`рейс ${flightNumber} в ${destination} добавден`);
}
/*function cancelFlight(flightNumber){
    const index = flights.findIndex(flightNumber === flightNumber);
    if(index !== -1){
        flights(index, 1);
        console.log(`Рейс ${flightNumber} отменен.`);
    } else {
        console.log(`Рейс ${flightNumber} не найден.`);
    }
}
*/
function registerPassenger(flightNumber, passengerName){
    const flight = flight.find(f => f.flightNumber === flightNumber);  
    if (!flight){
        console.log(`Рейс ${flightNumber} не найден.`);
        return;
    }  
    if (flight.passengers.length >= flight.capacity) {
        console.log(` на рейсе ${flightNumber} нет свободных мест.`);
        return;
    }
    flight.passengers.push(passengerName);
    console.log(`Пассажир ${passengerName} успешно зарегистрирован на рейс ${flightNumber}.`);
}
function findFlightByNumber(flightNumber){
    const flight = flights.find(f => f.flightNumber === flightNumber);
    
    if (flight) {
        console.log(`Найдено: Рейс ${flight.flightNumber}, Куда: ${flight.destination}, Время: ${flight.departureTime}, Мест: ${flight.capacity}`);
    } else {
        console.log(`Рейс ${flightNumber} не найден.`);
    }
}
function showAllFlights(){
    if (flights.length === 0) {
        console.log("Нет доступных рейсов.");
        return;
    }
    
    console.log("Список всех рейсов:");
    flights.forEach(flight => {
        console.log(`- Рейс ${flight.flightNumber} -> ${flight.destination} (${flight.departureTime}), Свободно мест: ${flight.capacity - flight.passengers.length}/${flight.capacity}`);
    });
}
function showFlightPassengers(flightNumber){
    const flight = flights.find(f => f.flightNumber === flightNumber);
    
    if (!flight) {
        console.log(`Рейс ${flightNumber} не найден.`);
        return;
    }
    
    console.log(`Пассажиры рейса ${flight.flightNumber} (${flight.destination}):`);
    if (flight.passengers.length === 0) {
        console.log("  Пока нет зарегистрированных пассажиров.");
    } else {
        flight.passengers.forEach((name, index) => {
            console.log(`  ${index + 1}. ${name}`);
        });
    }
}
addFlight("AB-123", "Москва", "14:30", 2);
addFlight("qw-123", "almaty", "13:30", 2);
/*cancelFlight("qw-123");*/
registerPassenger("AB-123", "Эльнур");
registerPassenger("AB-123", "Иван"); 
showFlightPassengers("AB-123");
