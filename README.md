# STC ML School

Задание выполнено для отборочного этапа летней школы <https://mlschool.speechpro.ru>

#### Мотивация

Ранее я не работала с аудиоданными и вообще в целом с обработкой сигналов, потому это был мой первый опыт, основанный на различных источниках из интернета. В этом году я буду писать диплом про анализ мультмодальных данных, а потому посещение STC ML School было бы очень инетерсно и полезно. Надеюсь полученный результат будет не слишком низким для прохождения отбора.

### Задание
Реализовать классификатор, работающий на представленных акустических событиях. В обучающей выборке предоставлены аудио 8 классов: 
door, tool, knocking_door, bags, keyboard, background, ring, speech. В тестовой помимо этих 8 классов предоставлены аудио с меткой unknown, класс которых в основном не был предоставлен в обучающей выборке.

**Описание файлов:**

* входные данные:
  - каталог ./audio - wav файлы для построения модели
  - каталог ./test - wav файлы валидирующего тестсета
* assignment.ipynb - jupyter-notebook с кодом реализации классификатора, который надо запустить
* meta.txt - метки класса wav файлов из каталога ./audio 
* выходные данные:
  - result.txt - результат обработки классификатором валидирующего тестсета из папки test (строки вида "file1.wav  0.95  door")

Дополнительные датасеты ***не были*** использованы.

*Важное замечание:* параметры моделей были подобраны на основе отложенной части обучающей выборки, после чего код был изменен и для окончательного обучения была использована вся обучающая выборка, сравнение моделей на основе валидирующего тестсета (./test) или на отложенной подвыборке почти не отличается (catboost в обоих случаях лучше всех), поэтому считаю это действие в целом корректным.

### Используемые библиотеки
* librosa
* catboost
* sklearn, numpy, pandas

Чтобы воспроизвести код из ноутбука, достаточно, чтобы тетрадка лежала в общей папке с остальными файлами и папками, то есть ровно так, как в репозитории, а в папках ./audio и ./test лежали файлы обучающей и валидационной выборок соответственно (не получилось загрузить данные папки ./audio).

### Краткий обзор
 
1. Обработка аудио с помощью librosa, выделение фичей mfccs, chroma, mel, contrast, tonnetz
2. Сравнение известных алгоритмов классификации (RFC, KNN, LogReg, Perceptron, CatBoost)
3. Запись лучшего результата в файл result.txt
