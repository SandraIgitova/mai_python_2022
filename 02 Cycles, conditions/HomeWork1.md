## Исходные данные 

    drone_list = ["DJI Mavic 2 Pro", "DJI Mavic 2 Zoom", "DJI Mavic 2 Enterprise Advanced", "AUTEL Evo II Pro", "DJI Mini 2", "Autel Evo Nano", "Autel Evo Lite Plus", "Parrot Anafi", "Dji Inspire 2", "DJI Mavic 3", "DJI Mavic Air2s", "Ryze Tello", "Eachine Trashcan"]
    
    drone_weight_list = [903, 900, 920, 980, 249, 249, 600, 540, 1500, 1000, 570, 130, 110]

## TODO1

> выведите все дроны производителя, название которого введет пользователь через input, и подсчитайте их количество.  учтите, что:
> 1) DJI и Dji - это один и тот же производитель! такие случаи тоже должны обрабатываться
> 2) при выводе исправьте название производителя, если допущена ошибка. правильный вариант названия: DJI, Autel

```
a = input('Введите имя производителя: ')
v_drons = []
for drone in drone_list:
  if a.upper() in drone.upper() :
      v_drons.append(drone)
if v_drons == [] :
  print('Я делала это задание 4 часа :( Я тупая блин блинский')
else :
  print('Дроны данного производителя:\n','\n '.join(v_drons),'\n Количество дронов:',len(v_drons))
```


## TODO2

> подсчитайте количество моделей дронов каждого производителя из списка drone_list. производители: DJI, Autel, Parrot, Ryze, Eachine

Опять делала это задание пол века. На самом деле у меня была идея, как написать код, который бы работал в случаях, когда производителей очень много и т.п. НО Я НЕ ПОНИМАЮ, КАК РЕАЛИЗОВАТЬ... Это жутко расстраивает, в итоге не смогла и пришлось писать в лоб... И то, тоже сто лет разбиралась. 
Алгоритм, который был сначала в голове: создается переменная-счетчик, которая проходит по списку и сохраняет единицу в другое место(+1 при каждом совпадении), потом выводит количество, обнуляется, проходит снова.
Я не знаю, как это закодить, до слез :(

```
amountDJI = 0 
amountAutel = 0 
amountParrot = 0 
amountRyze = 0 
amountEachine = 0 
for drone in drone_list:
  if drone.split(' ')[0].upper() == "DJI" :
      amountDJI += 1
  elif drone.split(' ')[0].upper() == 'AUTEL' :
      amountAutel += 1 
  elif drone.split(' ')[0].upper() == "PARROT" :
      amountParrot += 1
  elif drone.split(' ')[0].upper() == "RYZE" :
      amountRyze += 1
  elif drone.split(' ')[0].upper() == "EACHINE" :
      amountEachine += 1
print ('Колличество дронов всех производителей: \n', 'Производитель DJI: ',amountDJI,'\n Производитель Autel: ',amountAutel, '\n Производитель Parrot: ',amountParrot, '\n Производитель Ryze: ',amountRyze, '\n Производитель Eachine: ', amountEachine) 
```
    
## TODO3

> выведите все дроны из списка, которые нужно регистрировать (масса больше 150 г), и подсчитайте их количество. 
> сделайте то же самое для всех дронов, которые не нужно регистрировать
> для этого вам нужно параллельно обрабатывать два списка: drone_list и drone_weight_list:
> как работает zip, мы разберем на лекции про списки. пока что просто пользуйтесь

Эта лаба шла немного легче, но опять же сделано как-то тупо... Не смогла понять, как красиво оформить вывод, чтобы без скобок было и т.п.

```
reg = []
nreg = []
a = list(zip(drone_list,  drone_weight_list))
for drone in a:
  if (drone[-1] >= 150) :
    reg.append(drone)
  elif (drone[-1] <= 150) :
    nreg.append(drone)
    
print('Дроны, которые нужно зарегистрировать:\n','\n '.join(str(tup) for tup in reg),'\n','\n Количество дронов:',len(reg))
print('Дроны, которые НЕ нужно зарегистрировать:\n','\n '.join(str(tup) for tup in nreg),'\n','\n Количество дронов:',len(nreg))
```   
   
## TODO4

> для каждого дрона из списка выведите, нужно ли согласовывать полет при следующих условиях:
> высота 100 м, полет над населенным пунктом, вне закрытых зон, в прямой видимости
> помните, что для дронов тяжелее 150 г согласовывать полет над населенным пунктом - обязательно!

Показала код коллеге, не говоря, что писала я. Он сказал "Рабочий, но код - говно. Было немного грустно :( UPD: ночью поняла, что не выполняю условие веса. Посидела опять несколько часов, но так и не смогла привести к норм виду. Посоветовалась с другом, но у меня не получилось :( ниже указан второй вариант, который работает плохо(отличается только конец). при выполнении всех условий, кроме веса - вес не рассматривается. при выводе дронов с большим весом постоянно выводится одна и та же фраза на каждый дрон. 

```
ans = ''
vlos = ''
height = ''
closed_area = ''

print("Ответьте да или нет на следующие вопросы:\n")

print("\nПолёт над населенным пунктом?\n")
while ans.strip().upper() != 'ДА' and ans.strip().upper() != 'НЕТ':
  ans = input()
  if ans.strip().upper() != 'ДА' and ans.strip().upper() != 'НЕТ':
    print("Ввод не верен, повторите попытку")


print("\nПолёт в прямой видимости?\n")
while vlos.strip().upper() != 'ДА' and vlos.strip().upper() != 'НЕТ':
  vlos = input()
  if vlos.strip().upper() != 'ДА' and vlos.strip().upper() != 'НЕТ':
    print("Ввод не верен, повторите попытку")

print("\nПолёт в закрытой зоне?\n")
while closed_area.strip().upper() != 'ДА' and closed_area.strip().upper() != 'НЕТ':
  closed_area = input()
  if closed_area.strip().upper() != 'ДА' and closed_area.strip().upper() != 'НЕТ':
    print("Ввод не верен, повторите попытку")


while True:
    try:
        input_data = int(input("\nВведите высоту полета в метрах: "))
        height = input_data
        break
    except ValueError:
        print("Вы ввели не число. Попробуйте снова: ")
print('\n')

if (vlos.strip().upper()  == 'ДА') and (height <= 150) and (closed_area.strip().upper() == 'НЕТ') :
	print("Не нужно согласовывать, летайте спокойно!")
else:
    conditions = ""
    if (ans.strip().upper()  == 'ДА') :
        conditions += "полет над населенном пунктом; "
    if (vlos.strip().upper()  == 'НЕТ') :
        conditions += "полет вне зоны прямой видимости; "
    if height > 150:
        conditions += "высота полета более 150 м; "
    if (closed_area.strip().upper() == 'ДА') :
        conditions += "полет в закрытой зоне; "
        print(f"Нужно согласовывать, т.к. {conditions}")
```

### ВТОРОЙ ВАРИАНТ КОДА(НЕ РАБОЧИЙ)

```
ans = ''
vlos = ''
height = ''
closed_area = ''

print("Ответьте да или нет на следующие вопросы:\n")

print("\nПолёт над населенным пунктом?\n")
while ans.strip().upper() != 'ДА' and ans.strip().upper() != 'НЕТ':
  ans = input()
  if ans.strip().upper() != 'ДА' and ans.strip().upper() != 'НЕТ':
    print("Ввод не верен, повторите попытку")


print("\nПолёт в прямой видимости?\n")
while vlos.strip().upper() != 'ДА' and vlos.strip().upper() != 'НЕТ':
  vlos = input()
  if vlos.strip().upper() != 'ДА' and vlos.strip().upper() != 'НЕТ':
    print("Ввод не верен, повторите попытку")

print("\nПолёт в закрытой зоне?\n")
while closed_area.strip().upper() != 'ДА' and closed_area.strip().upper() != 'НЕТ':
  closed_area = input()
  if closed_area.strip().upper() != 'ДА' and closed_area.strip().upper() != 'НЕТ':
    print("Ввод не верен, повторите попытку")


while True:
    try:
        input_data = int(input("\nВведите высоту полета в метрах: "))
        height = input_data
        break
    except ValueError:
        print("Вы ввели не число. Попробуйте снова: ")
print('\n')



if (vlos.strip().upper()  == 'ДА') and (height <= 150) and (closed_area.strip().upper() == 'НЕТ') and (ans.strip().upper()  == 'НЕТ') :
  print("Не нужно согласовывать, летайте спокойно!")
else:
      conditions = ""
      if (ans.strip().upper()  == 'ДА') :
          conditions += "полет над населенном пунктом; "
      if (vlos.strip().upper()  == 'НЕТ') :
          conditions += "полет вне зоны прямой видимости; "
      if height > 150:
          conditions += "высота полета более 150 м; "
      if (closed_area.strip().upper() == 'ДА') :
          conditions += "полет в закрытой зоне; "
      for drone, weight in zip(drone_list,  drone_weight_list):
        if weight > 150 :
          conditions += ("Дроны {} слишком тяжелые".format(drone))
      print(f"Нужно согласовывать, т.к. {conditions}")

```

## TODO5

> модифицируйте решение задания TODO1:
> теперь для введенного пользователем производителя вы должны вывести строку, содержащую перечисление моделей и БЕЗ названия производителя.
> например, пользователь ввел "Autel". ваша программа должна вывести вот такой результат: "Evo II Pro, Evo Nano, Evo Lite Plus". для этого вам понадобится несколько функций работы со строками. решить эту задачу можно несколькими разными способами
> производители те же: DJI, Autel, Parrot, Ryze, Eachine

Идея пришла сразу, реализация заняла два дня.... Сначала ничего не работало, а потом работало, но неправильно. Помогли умные друзья понять в чем дело. Не могу сказать, что я идеально врубилась. Не уверена, что смогу с нуля написать это без гугла.

```
a = input('Введите имя производителя: ')
v_drons = []
for drone in drone_list:
  if a.upper() in drone.upper() :
      v_drons.append(drone)
if v_drons == [] :
  print('Я делала это задание 2 дня :( Я тупая блин блинский')
else :
  for i in range(len(v_drons)):
    v_drons[i] = ' '.join(v_drons[i].split()[1:])
  print('Дроны данного производителя:\n','\n '.join(v_drons),'\n Количество дронов:',len(v_drons))

```

## REPLIT В ФАЙЛЕ ghj.py

https://replit.com/join/mmbjgfdxcw-alieksandraighi
