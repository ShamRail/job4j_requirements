## job4j_requirements
Проект содержит описание требований к Web проектам, выполняемых учениками проекта [Job4j.ru](https://job4j.ru/)

### Описание процесса проверки проектов

В процессе проверки Web проектов, менторы обращают внимание на:

1. [README.md](#1-readmemdreadme);
2. Структуру репозитория;
3. Структуру проекта;
4. Скрипты миграции;
5. Слой моделей данных;
6. Конфигурирование проекта;
7. Слой репозиториев;
8. Слой сервисов;
9. Слой контроллеров;
10. Оформление кода;
11. Документирование кода;
12. Тесты;
13. Оформление веб-интерфейса.

Далее описываются требования, на соответствие которым, проверяются проекты.

### [1. README.md](README)

README.md является визитной карточкой проекта. По нему формируется первое впечатление о нем, а также умениях разработчика. Отсутствие этого файла или его
неграмотное заполнение приводит к тому, что мнение портится. 

Чтобы сделать README привлекательным, нужно чтобы он соответствовал требованиям:
1. <u>Наличие README</u>. Он в принципе должен быть. Файл README.md должен располагаться в корне проекта;
2. <u>Четкая структура</u>. README.md должен иметь следующую структуру:
   1. <b>Название проекта</b>. Проекты, выполняемые в рамках курса должны иметь префикс job4j. Например, job4j_dreamjob или job4j_url_shortcut;
   2. <b>Описание проекта</b>. 3-5 предложений. Причем своими словами, а не скопированные из описания заданий курса. Это позволит
      заложить именно ваше понимание и видение проекта. Так проще будет объяснить суть проекта другому человеку. Например, на собеседение;
   3. **Стек технологий**. Это список технологий, которые были использованы при разработке. Для каждой технологии нужно указать версию 
      (например, Hibernate 5), потому что от версии к версии работа с технологиями отличается. Список обязательно должен выключать
      основной ЯП, например, Java 17, а также СУБД, например, PostgreSQL 14;
   4. **Требования к окружению**. Это список ПО, которое должно быть установлено для запуска проекта.
      Например, для большинства проектов нужны: Java 17, Maven 3.8, PostgreSQL 14;
   5. **Запуск проекта**. Эта секция README описывает шаг за шагом как запустить проект. Каждый шаг должен содержать команду, которая
      выделена в тройные кавычки `: Например, команда для создания БД: 
      ```shell
      create database cinema;
      ``` 
   6. **Взаимодействие с приложением**:
      1. Для приложений, имеющих Web интерфейс, нужно добавить скриншоты страниц. Например, страница списка задач, страница регистрации и т.п.;
      2. Для приложений, имеющих REST архитектуру, нужно описать по какому URL доступно запущенное приложение вставить таблицу с endpoint'ами и их описанием. Например,
         приложение доступно по URL `http://localhost:8080`
        <table>
         <thead>
            <tr><th>URI</th><th>Метод</th><th>Описание</th><th>Запрос</th><th>Ответ</th></tr>
         </thead>
         <tbody>
            <tr>
               <td>/site/registration</td>
               <td>POST</td>
               <td>Регистрирует сайт</td>
               <td>
      <pre>{ 
         "site": "job4j.ru" 
      }</pre>
               </td>
               <td>
               <pre>
      {
         "login": "csdzasd",
         "password: "avbcvxvxc",
         "isRegistered": true
      }
      </pre>
      </td>
            </tr>
         <tbody>
        </table>
   7. **Контакты**. Не смотря на то, что проекты являются учебными и их цель освоение технологий, считается хорошей
      практикой предоставление способа обратной связи. Можно оставить в качестве контактов почту или логин в телеграмме.
3. <u>Привлекательность README.md</u>

   Привлекательность README зависит от того применяются ли списки, изображения, таблицы, иконки, способы выделения текстов
   (заголовки, ссылки, код и т.п.) и т.д. По возможности стоит использовать их вместо простого текста. Чем нагляднее
   представлено описание, тем лучше.
   

### 2. Структура репозитория

В репозитории должен быть порядок. Для этого нужно придерживаться следующих правил:
1. <u>Отсутствие файлов локального окружения</u>. Речь о директории `.idea` и файлах `*.iml`. Желательно в самом
начале добавить их в `.gitignore`. Если работа производится в других IDE, то нужно касательно этих IDE добавлять
файлы в исключения;
2. <u>Отсутствие файлов Maven wrapper</u>. Речь о директории `.mvn` и файлах `mvnw` и `mvnw.cmd`. Тема Maven wrapper в 
курсе не освещается, поэтому эти файлы являются лишними;
3. <u>Отсутствие файлов локальных сборок</u>. Речь о директории `target`;
4. <u>Отделение файлов для README</u>. Файлы, используемые в README, должны располагаться в отдельной директории. Например, если при описании добавляются
скриншоты приложения, то они должны лежать в папке `img`;
5. <u>Оформление коммитов</u>. Если коммиты оформлены правильно, то это показывает умение работать с системой контроля версий. 
Сюда можно отнести:
   1) **Количество коммитов**. Коммитов должно быть разумное количество (> 5);
   2) **Названия коммитов**. Название коммита должно описывать, что в нем происходило. Оно должно отвечать на вопрос
   "Что сделано?" или "Что сделал?". Например, "Добавлены зависимости Log4j, Spring-Security", "Созданы скрипт инициализации БД",
   "Реализован сервис TicketService" и т.п.;
   3) **Порядок коммитов**. История коммитов должна быть наглядной, чтобы по ней можно было наблюдать, как происходила разработка проекта.
   Например, если сначала идет коммит "Реализован сервис TicketService", а потом "Реализован репозиторий TicketRepository", то становится непонятно
   как можно было реализовать сервис без репозитория для работы с БД. 

### 3. Структуру проекта
### 4. Скрипты миграции
### 5. Слой моделей данных
### 6. Конфигурирование проекта
### 7. Слой репозиториев
### 8. Слой сервисов
### 9. Слой контроллеров
### 10. Оформление кода
### 11. Документирование кода
### 12. Тесты
### 13. Оформление веб-интерфейса
 