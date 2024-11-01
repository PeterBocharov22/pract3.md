### Задача 1
Реализовать на Jsonnet приведенный ниже пример в формате JSON. Использовать в реализации свойство программируемости и принцип DRY.
```bash
{
  groups: [
    std.join("-", ["ИКБО", std.toString(i), "20"]) for i in std.range(1, 24)
  ],

  students: [
    { age: 19, group: "ИКБО-5-20", name: "Иванов И.И." },
    { age: 18, group: "ИКБО-6-20", name: "Киселев П.В." },
    { age: 18, group: "ИКБО-7-20", name: "Сидоров М.С." },
    { age: 20, group: "ИКБО-8-20", name: "Скворцов Е.Н." } // новый студент
  ],

  subject: "Конфигурационное управление"
}
```

![image](https://github.com/user-attachments/assets/f0268671-2d75-4a95-93ab-930ee577a996)

### Задача 2
Реализовать на Dhall приведенный ниже пример в формате JSON. Использовать в реализации свойство программируемости и принцип DRY.
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
      [ mkStudent "Иванов И.И." 19 "ИКБО-5-20"
      , mkStudent "Киселев П.В." 18 "ИКБО-6-20"
      , mkStudent "Сидоров М.С." 18 "ИКБО-7-20"
      , mkStudent "Скворцов Е.Н." 19 "ИКБО-8-20" 
      ]


in  { groups = groups, students = students, subject = "Конфигурационное управление" }
```

![image](https://github.com/user-attachments/assets/9615d2ed-43d2-4737-9818-d1b7921fdcd2)

### Задача 3
Язык нулей и единиц.

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

![image](https://github.com/user-attachments/assets/1d968017-39ab-4416-a87c-619fefd165a3)

### Задача 4
Язык правильно расставленных скобок двух видов.

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

![image](https://github.com/user-attachments/assets/57d4fa82-30fb-4429-a046-c020d431f21f)


### Задача 5
Язык выражений алгебры логики.

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

![image](https://github.com/user-attachments/assets/55f65680-3f48-4f3a-9036-a6475ba7a563)
