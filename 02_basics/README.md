# Домашнее задание к занятию «1.2. Отличия от Java: immutability, переменные, типы данных, операторы и приведение типов»

В качестве результата пришлите ссылки на ваши GitHub-проекты в личном кабинете студента на сайте [netology.ru](https://netology.ru).

**Важно**: ознакомьтесь со ссылками на главной странице [репозитория с домашними заданиями](../README.md).

Если у вас что-то не получилось, то оформляйте Issue [по установленным правилам](../report-requirements.md).

Не делайте ДЗ всех занятий в одном репозитории! Иначе потом будет сложно подключать системы Continuous Integration.

## Как сдавать задачи

1. Создайте на вашем компьютере Gradle-проект.
1. Инициализируйте в нём пустой Git-репозиторий.
1. Добавьте в него готовый файл [.gitignore](../.gitignore).
1. Добавьте в этот же каталог остальные необходимые файлы.
1. Сделайте необходимые коммиты.
1. Создайте публичный репозиторий на GitHub и свяжите свой локальный репозиторий с удалённым.
1. Сделайте пуш и удостоверьтесь, что ваш код появился на GitHub.
1. Ссылку на ваш проект отправьте из личного кабинета на сайте [netology.ru](https://netology.ru).
1. Необязательные задачи можно не сдавать — это не повлияет на получение зачёта. В этом ДЗ все задачи обязательные.

## Задача №1 - Денежные переводы

Сейчас можно легко и просто отправить денежный перевод практически через любую систему.

Например, мы можем отправлять переводы через VKontakte:

![](pic/vk-pay.png)

При этом берётся определённая комиссия за совершение перевода:

![](pic/vk-commission.png)

Упростим задачу, чтобы было проще: за переводы с любых карт комиссия 0.75%, минимум 35 рублей.

Что нужно сделать: напишите небольшую программу, в которой в переменной `amount` хранится сумма перевода в рублях.

Ваше приложение должно высчитывать комиссию, которую заплатит пользователь при переводе — комиссия также должна быть в рублях.

Итог: у вас должен быть репозиторий на GitHub, в котором расположен ваш Gradle-проект.

## Задача №2 - "Люди/Человеки"

Русский язык в интерфейсах - достаточно сложная штука, потому что нам постоянно приходится изменять окончания слов после числительных:

![](pic/likes1.png)

![](pic/likes2.png)

Вам нужно провести самостоятельный анализ (да-да, к этому нужно привыкать, не всегда вам дадут чёткую постановку задачи, достаточно часто вы будете получать задачу в формате «Сделай как в Вк») и написать небольшое приложение:
1. В переменной `likes` хранится число лайков.
1. Приложение выводит в консоль соответствующий вариант, вы сами должны их определить, в зависимости от того, что хранится в `likes`

Итог: у вас должен быть репозиторий на GitHub, в котором расположен ваш Gradle-проект.

## Задача №3 - "Меломан"

Вы решили мотивировать пользователей покупать больше музыки.

Схема достаточно простая: чем большую сумму потратил пользователь, тем большую скидку вы ему даёте.

Условия следующие:
* Если сумма покупки от 0 до 1 000 рублей, то никаких скидок нет (как в лекции).
* Если сумма покупки от 1 001 до 10 000 рублей, то стандартная скидка - 100 рублей (как в лекции).
* Если сумма покупки от 10 001 рубль и выше то % составляет 5% от суммы.

Все цены указаны в рублях.

При этом постоянные пользователи — те, кто покупает ежемесячно, назовём их «меломаны», дополнительно получают 1% скидки сверху.

**Важно**: скидки не суммируются, а применяются сверху. Например, у пользователя скидка 5%, значит 1% применяется к 95%:
```
покупка - 100 рублей →

после применения 5% скидки - 95 рублей.

после применения 1% скидки - 94 рубля.
```

Подумайте о том, как вы будете хранить информацию о том, постоянно покупает пользователь музыку или нет.

<details>
  <summary>Подсказка</summary>

  Нехорошо смотреть подсказки 😈!

  Но раз уж вы посмотрели, то вот она: почему бы эту информацию не хранить в виде `Boolean`?
</details>

Итог: у вас должен быть репозиторий на GitHub, в котором будет ваш Gradle-проект.
