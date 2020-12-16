# Взлом алгоритма рандомизации в Python

Данная программа "предугадывает" числа, сгенерированные модулем рандома Python.

# Принцып работы

Генератор случайных числовых последовательностей основан на Вихре Мерсенна - алгоритме, который способен генерировать числа, статистически не отличающихся от абсолютно случайных. Однако данный алгоритм не является криптографически стойким, т.е. его можно "взомать".
Программа работает следующим образом: сначала она получает на вход первые 624 32-битных числа, сгенерированных с помощью рандомайзера, тем самым получая наиболее вероятное состояние матрицы Вихря Мерсенна, которое является внутренним состоянием. Далее алгоритм способен предугадывать последующие числа, генерируемые модулем рандома.

# Используемые методы

У основного класса - Cracker'а - есть один метод для аггрегирования случайно сгенерированных чисел - submit(n). После того, как он получит на вход 624 числа, он перестанет принимать последующие. С этого момента их можно будет предсказать с помощью методов: predict_getrandbits, predict_randbelow, predict_randrange, predict_randint и predict_choice.

# Точность 

Данный алгоритм взлома не абсолютно точен. Он способен выдавать 100% точности на первых 624-х 32-битных генерациях, приблизительно 99.5% на первой 1000, 95% на 10000. Примерно к 50000-ой генерации точность падает приблизительно до 50%.
