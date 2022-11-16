#  Заголовок первого уровня #

    a = input('Введите имя производителя: ')
    v_drons = []
    for drone in drone_list:
      if a.upper() in drone.upper() :
          v_drons.append(drone)
    if v_drons == [] :
      print('Я делала это задание 4 часа :( Я тупая блин блинский')
    else :
      print('Дроны данного производителя:\n','\n '.join(v_drons),'\n Количество дронов:',len(v_drons))



