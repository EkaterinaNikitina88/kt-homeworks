# Домашнее задание к занятию «2.3. ООП: Композиция, наследование и интерфейсы»

В качестве результата пришлите ссылки на ваши GitHub-проекты в личном кабинете студента на сайте [netology.ru](https://netology.ru).

**Важно**: ознакомьтесь со ссылками на главной странице [репозитория с домашними заданиями](../README.md).

Если у вас что-то не получилось, то оформляйте Issue [по установленным правилам](../report-requirements.md).

Нужно сделать все задачи в **одном** репозитории.

## Как сдавать задачи

1. Создайте на вашем компьютере Gradle-проект.
1. Инициализируйте в нём пустой Git-репозиторий.
1. Добавьте в него готовый файл [.gitignore](../.gitignore).
1. Добавьте в этот же каталог остальные необходимые файлы.
1. Сделайте необходимые коммиты.
1. Создайте публичный репозиторий на GitHub и свяжите свой локальный репозиторий с удалённым.
1. Сделайте пуш и удостоверьтесь, что ваш код появился на GitHub.
1. Ссылку на ваш проект отправьте из личного кабинета на сайте [netology.ru](https://netology.ru).
1. Необязательные задачи можно не сдавать — это не повлияет на получение зачёта.

## Задача №1 - Посты (без Attachments)

Мы с вами изучили `Nullable`, поэтому пришло время закрыть вопросы с постами: привыкайте к тому, что ваш код никуда не исчезает, и вам предстоит поддерживать то, что вы сами же когда-то написали (старая шутка "да кто вообще это писал?"). Поэтому мы в том числе будем отрабатывать и этот навык.

Доработайте первую задачу из предыдущей лекции так, чтобы ваша система отображала все поля объекта (кроме `attachments`), описанного в документации.
Сделайте некоторые из полей `Nullable` (на ваш выбор).  

Если у вас по каким-то причинам не доступен Vk, вы всегда можете воспользоваться сохранённой версией из каталога [assets](assets)

Напоминаем, что у вас должно быть:
1. Data класс `Post`.
1. Внутри `Post` могут быть `Nullable` свойства.
1. `WallService`, который внутри себя хранит посты в массиве. 

Вы можете оформить это как Pull Request к предыдущему проекту (присылайте в личном кабинете ссылку на PR).

**Важно**: после ваших обновлений, функциональность `WallService` должна оставаться работоспособной (т.е. автотесты должны проходить).

## Задача №2 - Attachments

Надеемся, что с постами было не так уж и сложно. А вот с `attachments` ([прямая ссылка](https://vk.com/dev/objects/attachments_w)/[сохраненная копия](assets/attachments.pdf)) будет сложнее.

Почему? Потому что у вас в массиве могут храниться разные объекты.

Сам Vk их хранит вот так: 

```json
{
    "attachments": [
      {
        "type": "photo",
        "photo": {
            "id": 1,
            "album_id": 1,
            "owner_id": 1,
            "user_id": 1
        }
      }, {
        "type": "video",
        "video": {
            "id": 1,
            "album_id": 1,
            "owner_id": 1,
            "user_id": 1
        }
      }
    ]
}
```

Данный формат называется JSON, с ним мы будем знакомиться позднее. В примере описано, что есть массив `attachments`, в котором лежат объекты (назовем их тип  `Attachment`'ом). В объектах массива есть поле `type`, а второе поле может быть различным (оно определяется на базе значения поля `type`: в первом случае `Photo`, во втором - `Video`). Для организации подобной структуры будет удобно применить наследование.

Возможны два варианта:
1. Сделать `Attachment` интерфейсом.
1. Сделать `Attachment` абстрактным классом.

В обоих вариантах нужно добавить в `Attachment` поле `type`, а после описать наследников Attachment, которые уже будут хранить данные по типу (фото, аудио, видео и т.д.). Данные `Audio`, `Video` (то, что вложено в наследников `Attachment`) лучше оформить в виде отдельных классов. Т.е. для одного типа вложения будет два класса: `AudioAttachment` и `Audio`. Не забывайте, что в Kotlin не обязательно каждый класс описывать в отдельном файле, а можно в одном описать сразу несколько, что будет особенно удобно в этой задаче.

Вам необходимо добавить к классу Post массив из объектов `Attachment` и описать классы `Attachment`, его наследников и классы для хранения данных о вложениях.

Поскольку типов вложений очень много, вам достаточно выбрать для реализации любые 5. Содержимое вложений можно посмотреть в [документации](https://vk.com/dev/objects/attachments_w) или в сохраненных копиях в каталоге [assets](assets).

Вы можете оформить это как Pull Request к задаче №1 (присылайте ссылку в личном кабинете на PR).

**Важно**: после ваших обновлений, функциональность `WallService` должна оставаться работоспособной (т.е. автотесты должны проходить).

## Задача №3 - Sealed классы*

**Важно**: это не обязательная задача. Её выполнение не влияет на получение зачёта по ДЗ.

Одной из возможностей Kotlin для решения предыдущей задачи являются [Sealed ("запечатанные") классы](https://kotlinlang.org/docs/reference/sealed-classes.html).

Что это значит? Это значит, что вы можете определить фиксированную иерархию типов (ведь количество типов вложений у вас фиксировано).

Тогда в выражениях типа `when` вам не придётся писать `else`.

Нужно почитать [документацию](https://kotlinlang.org/docs/reference/sealed-classes.html) и сделать Pull Request с реализацией на базе Sealed классов (вы можете подглядеть подсказку).

<details>
<summary>Подсказка</summary>

Не забывайте, что у всех наследников есть общее поле `type`. Для Sealed классов возможна следующая реализация:
```kotlin
sealed class Attachment(val type: String)

data class VideoAttachment(val video: Video) : Attachment("video")

fun main() {
    val attachment: Attachment = VideoAttachment("stuff")
    println(attachment.type)
}
```
</details>

Вы можете оформить это как Pull Request к задаче №1 (присылайте ссылку в личном кабинете на PR).

**Важно**: после ваших обновлений, функциональность `WallService` должна оставаться работоспособной (т.е. автотесты должны проходить).
