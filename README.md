# Практическое занятие №3.
## Задача 1. Реализовать на Jsonnet приведенный ниже пример в формате JSON. Использовать в реализации свойство программируемости и принцип DRY.
```
local student(name, age, group) =
{
  name: name,
  age: age,
  group: group,
};
local groups = [
  "ИКБО-1-20",
  "ИКБО-2-20",
  "ИКБО-3-20",
  "ИКБО-4-20",
  "ИКБО-5-20",
  "ИКБО-6-20",
  "ИКБО-7-20",
  "ИКБО-8-20",
  "ИКБО-9-20",
  "ИКБО-10-20",
  "ИКБО-11-20",
  "ИКБО-12-20",
  "ИКБО-13-20",
  "ИКБО-14-20",
  "ИКБО-15-20",
  "ИКБО-16-20",
  "ИКБО-17-20",
  "ИКБО-18-20",
  "ИКБО-19-20",
  "ИКБО-20-20",
  "ИКБО-21-20",
  "ИКБО-22-20",
  "ИКБО-23-20",
  "ИКБО-24-20",
];
local students = [
  student("Иванов И.И.", 19, "ИКБО-4-20"),
  student("Петров П.П.", 18, "ИКБО-5-20"),
  student("Сидоров С.С.", 18, "ИКБО-5-20"),
  student("Безфамильный Е.Г.", 19, "ИКБО-6-20"), 
];
{
  groups: groups,
  students: students,
  subject: "Конфигурационное управление",
}
```
<img width="1134" alt="Снимок экрана 2024-11-01 в 13 17 51" src="https://github.com/user-attachments/assets/11a1e291-a430-4527-b3d6-def15759a391">

## Задача 2. Реализовать на Dhall приведенный ниже пример в формате JSON. Использовать в реализации свойство программируемости и принцип DRY.
```
let Student = { name: Text, age: Natural, group: Text }
let mkStudent : Text -> Natural -> Text -> Student =
      λ(name : Text) →
      λ(age : Natural) →
      λ(group : Text) →
      { name = name, age = age, group = group }
let groups : List Text =
      [ "ИКБО-1-20"
      , "ИКБО-2-20"
      , "ИКБО-3-20"
      , "ИКБО-4-20"
      , "ИКБО-5-20"
      , "ИКБО-6-20"
      , "ИКБО-7-20"
      , "ИКБО-8-20"
      , "ИКБО-9-20"
      , "ИКБО-10-20"
      , "ИКБО-11-20"
      , "ИКБО-12-20"
      , "ИКБО-13-20"
      , "ИКБО-14-20"
      , "ИКБО-15-20"
      , "ИКБО-16-20"
      , "ИКБО-17-20"
      , "ИКБО-18-20"
      , "ИКБО-19-20"
      , "ИКБО-20-20"
      , "ИКБО-21-20"
      , "ИКБО-22-20"
      , "ИКБО-23-20"
      , "ИКБО-24-20"
      ]
let students : List Student =
      [ mkStudent "Иванов И.И." 19 "ИКБО-4-20"
      , mkStudent "Петров П.П." 18 "ИКБО-5-20"
      , mkStudent "Сидоров С.С." 18 "ИКБО-5-20"
      , mkStudent "Безфамильный Е.Г." 19 "ИКБО-6-20" 
      ]


in  { groups = groups, students = students, subject = "Конфигурационное управление" }
```
<img width="1224" alt="Снимок экрана 2024-11-01 в 13 19 24" src="https://github.com/user-attachments/assets/efc5df52-8afc-4b2a-a8f2-c746f5600276">

## Задача 3. Язык нулей и единиц.
```
import random


def parse_bnf(text):
    '''
    Преобразовать текстовую запись БНФ в словарь.
    '''
    grammar = {}
    rules = [line.split('=') for line in text.strip().split('\n')]
    for name, body in rules:
        grammar[name.strip()] = [alt.split() for alt in body.split('|')]
    return grammar


def generate_phrase(grammar, start):
    '''
    Сгенерировать случайную фразу.
    '''
    if start in grammar:
        seq = random.choice(grammar[start])
        return ''.join([generate_phrase(grammar, name) for name in seq])
    return str(start)


BNF = '''
E = 0 E | 1 E |
'''

for i in range(10):
    print(generate_phrase(parse_bnf(BNF), 'E'))

```
<img width="170" alt="Снимок экрана 2024-10-24 в 23 21 33" src="https://github.com/user-attachments/assets/96e5ee6b-0bed-40d0-962a-f6629692ddc0">


## Задача 4. Язык правильно расставленных скобок двух видов.
```
import random


def parse_bnf(text):
    '''
    Преобразовать текстовую запись БНФ в словарь.
    '''
    grammar = {}
    rules = [line.split('=') for line in text.strip().split('\n')]
    for name, body in rules:
        grammar[name.strip()] = [alt.split() for alt in body.split('|')]
    return grammar


def generate_phrase(grammar, start):
    '''
    Сгенерировать случайную фразу.
    '''
    if start in grammar:
        seq = random.choice(grammar[start])
        return ''.join([generate_phrase(grammar, name) for name in seq])
    return str(start)


BNF = '''
E = ( E ) | { E } |
'''

for i in range(10):
    print(generate_phrase(parse_bnf(BNF), 'E'))

```
<img width="127" alt="Снимок экрана 2024-10-24 в 23 23 02" src="https://github.com/user-attachments/assets/e8f033d8-314e-4cae-b39a-63ff5484d363">


## Задача 5. Язык выражений алгебры логики.
```
import random


def parse_bnf(text):
    '''
    Преобразовать текстовую запись БНФ в словарь.
    '''
    grammar = {}
    rules = [line.split('=') for line in text.strip().split('\n')]
    for name, body in rules:
        grammar[name.strip()] = [alt.split() for alt in body.split('|')]
    return grammar


def generate_phrase(grammar, start):
    '''
    Сгенерировать случайную фразу.
    '''
    if start in grammar:
        seq = random.choice(grammar[start])
        return ''.join([generate_phrase(grammar, name) for name in seq])
    return str(start)


BNF = '''
E = "~" E | E "&" E | E "|" E | "(" E ")" | "x" | "y"
'''

for i in range(10):
    print(generate_phrase(parse_bnf(BNF), 'E'))
```
<img width="452" alt="Снимок экрана 2024-11-01 в 13 32 21" src="https://github.com/user-attachments/assets/e5207ad8-2702-4d82-89ce-e3dd9bbe859c">
