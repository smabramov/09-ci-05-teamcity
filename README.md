# Домашнее задание к занятию 11 «Teamcity»

## Подготовка к выполнению

1. В Yandex Cloud создайте новый инстанс (4CPU4RAM) на основе образа `jetbrains/teamcity-server`.
2. Дождитесь запуска teamcity, выполните первоначальную настройку.
3. Создайте ещё один инстанс (2CPU4RAM) на основе образа `jetbrains/teamcity-agent`. Пропишите к нему переменную окружения `SERVER_URL: "http://<teamcity_url>:8111"`.
4. Авторизуйте агент.
5. Сделайте fork [репозитория](https://github.com/aragastmatb/example-teamcity).
6. Создайте VM (2CPU4RAM) и запустите [playbook](./infrastructure).

![t1](https://github.com/smabramov/09-ci-05-teamcity/blob/7beac47e8acc62c79e912f186c77bf3f0ec53103/jpg/t1.png)

## Основная часть

1. Создайте новый проект в teamcity на основе fork.
2. Сделайте autodetect конфигурации.
3. Сохраните необходимые шаги, запустите первую сборку master.

![t2](https://github.com/smabramov/09-ci-05-teamcity/blob/7beac47e8acc62c79e912f186c77bf3f0ec53103/jpg/t2.png)

![t3](https://github.com/smabramov/09-ci-05-teamcity/blob/7beac47e8acc62c79e912f186c77bf3f0ec53103/jpg/t3.png)

![t4](https://github.com/smabramov/09-ci-05-teamcity/blob/7beac47e8acc62c79e912f186c77bf3f0ec53103/jpg/t4.png)

4. Поменяйте условия сборки: если сборка по ветке `master`, то должен происходит `mvn clean deploy`, иначе `mvn clean test`.
5. Для deploy будет необходимо загрузить [settings.xml](./teamcity/settings.xml) в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus.
6. В pom.xml необходимо поменять ссылки на репозиторий и nexus.
7. Запустите сборку по master, убедитесь, что всё прошло успешно и артефакт появился в nexus.

![t5](https://github.com/smabramov/09-ci-05-teamcity/blob/7beac47e8acc62c79e912f186c77bf3f0ec53103/jpg/t5.png)

![t6](https://github.com/smabramov/09-ci-05-teamcity/blob/7beac47e8acc62c79e912f186c77bf3f0ec53103/jpg/t6.png)

8. Мигрируйте `build configuration` в репозиторий.

![t7](https://github.com/smabramov/09-ci-05-teamcity/blob/7beac47e8acc62c79e912f186c77bf3f0ec53103/jpg/t7.png)

Ссылка на [.teamsity](https://github.com/smabramov/example-teamcity.git)

9. Создайте отдельную ветку `feature/add_reply` в репозитории.
10. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово `hunter`.
11. Дополните тест для нового метода на поиск слова `hunter` в новой реплике.
12. Сделайте push всех изменений в новую ветку репозитория.
13. Убедитесь, что сборка самостоятельно запустилась, тесты прошли успешно.

![t8](https://github.com/smabramov/09-ci-05-teamcity/blob/7beac47e8acc62c79e912f186c77bf3f0ec53103/jpg/t8.png)

14. Внесите изменения из произвольной ветки `feature/add_reply` в `master` через `Merge`.

![t9](https://github.com/smabramov/09-ci-05-teamcity/blob/7beac47e8acc62c79e912f186c77bf3f0ec53103/jpg/t9.png)

15. Убедитесь, что нет собранного артефакта в сборке по ветке `master`
16. Настройте конфигурацию так, чтобы она собирала `.jar` в артефакты сборки.
17. Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны.

![t10](https://github.com/smabramov/09-ci-05-teamcity/blob/7beac47e8acc62c79e912f186c77bf3f0ec53103/jpg/t10.png)

18. Проверьте, что конфигурация в репозитории содержит все настройки конфигурации из teamcity.

![t11](https://github.com/smabramov/09-ci-05-teamcity/blob/7beac47e8acc62c79e912f186c77bf3f0ec53103/jpg/t11.png)

19. В ответе пришлите ссылку на репозиторий.

[.teamsity](https://github.com/smabramov/example-teamcity.git)

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
