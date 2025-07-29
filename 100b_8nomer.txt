from itertools import *

old = [''.join(i) for i in product(sorted('ДАЙТЕРБОУ'), repeat=5)] #список всех слов
new_1 = [word for i, word in enumerate(old, 1) if i % 3 != 0 and i % 5 != 0] #список всех слов после удаления 3-их и 5-ых слов
ne_podhod = []
for i in range(len(new_1)):
    if new_1[i] == new_1[i][::-1]: #проверка на палиндром
        if i != 0: #пропускаем первое слово
            for j in range(i, i - 5, -1):
                ne_podhod.append(new_1[j]) #удаление палиндрома и 4-ех слов до него
itog = []
for i in new_1:
    if i not in ne_podhod:
        itog.append(i) #список слов после проверки на палиндромы
itog = [''] + itog
for i in range(1, len(itog)):
    if i % 3 != 0 and i % 5 != 0 and all(j in 'ДЙРБ' for j in itog[i]): #проверка номера на делимость и состав букв(должны быть только звонкие)
        print(itog[i], i)