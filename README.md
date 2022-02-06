# hack_oop
хакатон в Яндекс.Практикуме 18.09.21

# Мини-проект "игра-арена"

Цель данной активности - получить удовольствие от применения ООП.

В результате выполнения у вас должна получиться мини-игра арена, на которую вы выпустите своих 
персонажей и заставите их сражаться между собой. Играющая сама в себя и выдающая вам только результат своей работы. 

Если вы улучшите игру так, чтобы можно было влиять на игровой процесс **не из кода(!)**, обязательно поделитесь, мы с удовольствием потестируем! 

Для работы вам потребуется только среда разработки, через которую можно запускать код для выполнения. 
Подойдет тот же VSC, в котором вы наверняка и работаете при обучении :)


## Техническое задание

Ваша программа должна иметь следующие классы и функции: 
1. Вещи: `class Thing`
    Класс содержит в себе следующие параметры - название, процент защиты, атаку и жизнь; Это могут быть предметы одежды, магические кольца, всё что угодно)

2. Персонаж: `class Person`
    Класс, содержащий в себе следующие параметры: 
    - Имя, кол-во hp/жизней, базовую атаку, базовый процент защиты. Параметры передаются через конструктор;
    - метод, принимающий на вход список вещей *`set_things(things)`*;
    - метод вычитания жизни на основе входной атаки, а также методы для выполнения алгоритма, представленного ниже;

3. Паладин: `class Paladin`
    Класс наследуется от персонажа, при этом количество присвоенных жизней и процент защиты умножается на 2 в конструкторе;

4. Воин: `class Warrior`
    Класс наследуется от персонажа, при этом атака умножается на 2 в конструкторе.

## Алгоритм проведения боя:
1. Шаг 1 - создаем произвольное количество вещей с различными параметрами, процент защиты не должен превышать 10%(0.1). 
    Сортируем по проценту защиты, по возрастанию;

2. Шаг 2 - создаем произвольно 10 персонажей, кол-во воинов и паладинов произвольно. 
    Имена персонажам тоже рандомные из созданного списка 20 имен. 
    Придумайте своих уникальных персонажей или заставьте сражаться знаменитостей, посмотрим кто сильнее =) 

3. Шаг 3 - одеваем персонажей рандомными вещами. 
    Кому-то 1, кому-то больше, но не более 4 вещей в одни руки;

4. Шаг 4 - отправляем персонажей на арену, и в цикле в произвольном порядке выбирается пара Нападающий и Защищающийся.
    1. У Защищающегося вызывается метод вычитания жизни на основе атаки `(attack_damage)` Нападающего. 
    2. Количество получаемого урона рассчитывается по формуле: `(attack_damage - attack_damage*finalProtection)`
    3. Общий процент защиты `(finalProtection)` вычисляется по формуле (базовый процент защиты + процент защиты от всех надетых вещей)
    4. Жизнь вычитается по формуле `(HitPoints - (attack_damage - attack_damage*finalProtection))`, где `finalProtection` - коэффициент защиты в десятичном виде;

Цикл идет до тех пор, пока не останется последнего выжившего. 
Как только кол-во жизней меньше или равно 0, персонаж удаляется из арены (списка). 
Для отслеживания процесса битвы выведите информацию в таком виде: `{атакующий персонаж} наносит удар по {защищающийся персонаж} на {кол-во урона} урона`


## Критерии оценки:
1) Работоспособность программы
2) Соответствие программы условиям задания, корректность работы алгоритма
3) Расширение функционала программы (не обязательно)

## Идеи по расширению:
1) Игрок против компьютера (возможно, это выбор персонажей или выбор конкретных предметов на бой)
2) Подсветить разными цветами разные события, используем colorama
3) Добавить 3 расу, например, эльфов
4) Интегрировать игру в Django (самое простое - отдавать результаты случайной игры на странице, чуть сложнее - пусть пользователь создаст своего персонажа, и он поучаствует в битве)
