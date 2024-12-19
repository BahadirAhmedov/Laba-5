# Лабораторная работа 5

Сделал: `Ахмедов Бахадыр`
## Часть 1
Для того чтобы создать `bash`-скрипт,который будет выполнять проверку того, что коммитится файл формата .txt и в файле присутствует какой-то текст, нужно пройти в каталог `.git/hooks` где находятся Хуки.

<img width="500" src="./images/image1.png"/>

Открываем файл `pre-commit.sample` и в нем пишем наш `bash`-скрипт, который проверяет что коммитится файл формата .txt и в файле присутствует текст. 

<img width="500" src="./images/image2.png"/>

```
#!/bin/sh

all_files=$(git diff --cached --name-only)


for file in $all_files; do
if [[ $file  == *.txt ]] && [ -s $file ]
then
  echo "$file .txt format and is not empty"
elif [ ! -s $file ]
then
  echo " $file file is empty"
  exit 1
else
  echo "$file is not .txt format"
  exit 1
fi
done

exit 0
```

Cохраняем изменения в файле, и уберем из имени скрипта расширение `.sample` 

<img width="500" src="./images/image3.png"/>


Проверяем:

Проверка на то что коммитится файл формата `.txt`.

- В этом случае коммитится файл формата `.py`, и хук не дал нам закоммитить файл формата `.py`.

<img width="500" src="./images/image4.png"/>

Проверка на содержимое файла.
- В этом случае коммитится пустой файл формата `.txt`, и хук нам не дал закоммитить пустой файл. 

<img width="500" src="./images/image5.png"/>

Проверим с правильным форматом файла
- На этот раз коммитится не пустой файл с правильным форматом

<img width="500" src="./images/image6.png"/>

## Часть 2


##### Инициализация Git Flow

<img width="500" src="./images/image7.png"/>

<img width="500" src="./images/image8.png"/>


##### Создадим ветку для новой функциональности

<img width="500" src="./images/image9.png"/>

##### Внесем изменения в код для добавления функционала управления задачами

<img width="500" src="./images/image10.png"/>

<img width="500" src="./images/image11.png"/>

##### Выполним коммит изменения

<img width="500" src="./images/image12.png"/>

##### Завершим фичу и объединим ее с основной веткой:

<img width="500" src="./images/image13.png"/>

##### Создадим релиз

<img width="500" src="./images/image14.png"/>

##### Внесем изменения, связанные с релизом
<img width="500" src="./images/image15.png"/>

##### Завершим релиз и объедините его с ветками "develop" и "main":

<img width="500" src="./images/image16.png"/>

##### Создадим hotfix

<img width="500" src="./images/image17.png"/>

##### Внесем изменения для исправления ошибки и закоммитим:

<img width="500" src="./images/image18.png"/>

##### Завершим hotfix и объединим его с ветками "develop" и "main":

<img width="500" src="./images/image19.png"/>

 ##### Отправим изменения на удаленный репозиторий:

<img width="500" src="./images/image20.png"/>
