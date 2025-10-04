---
date: 2025-10-04
authors:
    - magus1968
categories:
    - Tools
# draft: true
# tags:
#     - MkDocs
---

# GitHub Actions, первое знакомство

Наконец дошли руки узнать что такое [GitHub Actions](https://github.com/features/actions). Понятно, что есть официальная [документация](https://docs.github.com/ru/actions), но для начала хотелось просто понять – "*что за зверь и с чем его едят*".
<!-- more -->

Поисковик выдал статью из блога 1cloud [GitHub Actions: знакомство и первые шаги](https://1cloud.ru/blog/git_for_begginers_chapter_4) и она вполне удовлетворила моё любопытство.

Стало формироваться понимание содержимого файла `.github/workflows/ci.yml`, который я просто [скопировал](https://jameswillett.dev/getting-started-with-material-for-mkdocs/#publish-site-to-github-pages) у James Willett при исследовании [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/), не имея до этого момента ни малейшего представления не только о назначении yml, а вообще о его существовании.

Я конечно "догадывался" что в ci.yml прописывается последовательность действий для автоматической публикации сайта на [GitHub Pages](https://docs.github.com/ru/pages/getting-started-with-github-pages/what-is-github-pages). Так и оказалось – в yml отражается вся многоуровневая конструкция последовательности выполнения задач (или поток выполнения действий), который называется workflow (ещё один термин в копилку).

Попутно ознакомился с основами синтаксиса yml из статьи [YAML для начинающих](https://1cloud.ru/blog/yaml_for_beginners). А с помощью валидатора [YAML Lint](https://www.yamllint.com/) (бесплатного онлайн-сервиса проверки синтаксиса yml) нашел пару ошибок в примерах исходной [статьи](https://1cloud.ru/blog/git_for_begginers_chapter_4) и заодно проверил скопированный у James Willett `.github/workflows/ci.yml`.

## CheatSheet

Переписывать статью смысла нет. На этапе первичного ознакомления оставлю для себя шпаргалку:

```yaml
# Настройки самого workflow:
name: Print hello and checkout repo workflow # Название workflow
on: push # (1)!

# Настройка джобов:
jobs: # Начало секции джобов
  print_hello: # Название джоба
    runs-on: ubuntu-latest # (2)!
    steps: # Начало секции шагов
      - name: Print hello # Название шага
        run: echo "Hello world!" # (3)!
  
  checkout_repo: # Начало секции второй джобы
    needs: print_hello # (4)!
    runs-on: ubuntu-latest # Среда выполнения джоба
    steps: # Начало секции шагов
      - name: checkout # Название шага
        uses: actions/checkout@v4 # (5)!
```

1.  `on` — условие срабатывания workflow:   
    - `push` — автоматическое выполнение workflow при загрузке файлов в репозиторий;   
    - `workflow_dispatch` — ручной запуск workflow.

2.  `runs-on` — инструкция, указывающая на какой ОС запускать джобу. В данном случае джоба будет выполняться на Ubuntu последней версии.

3.  `run` — действие, которое будет выполнено в терминале Linux. В нашем случае мы вызываем команду echo, которая выводит в терминал «Hello world!».

4.  `needs` — инструкция, если нужно добавить последовательное и связанное выполнение джобов, поскольку по умолчанию джобы выполняются параллельно и независимо друг от друга.

5.  В рамках шагов для выполнения типовых задач можно использовать готовые модули или решения из [GitHub Marketplace](https://github.com/marketplace?type=actions). Такие готовые решения в GitHub называются actions или экшены.  
Вызываются экшены через инструкцию `uses`.

Прим. А вообще в документации GitHub Actions представлено множество [workflow шаблонов](https://docs.github.com/ru/actions/get-started/quickstart#using-workflow-templates) c yml-файлами. Но это уже к пункту 3 следующего раздела :smile:

## Резюме

???+ abstract "Резюме"

    1. Первое представление о GitHub Action получено.
    2. Смысл и структура управляющего (пожалуй точнее – конфигурационного) yml-файла в первом приближении понятны.
        - На [GitHub Marketplace](https://github.com/marketplace?type=actions) много готовых экшенов для выполнения различных типовых задач.
        - В документации GitHub Actions много [workflow шаблонов](https://docs.github.com/ru/actions/get-started/quickstart#using-workflow-templates) c yml-файлами под разные конфигурации.
    3. Основа при необходимости копать глубже заложена.
    4. Пополнил личный глоссарий.

## Глоссарий

???+ info "Глоссарий"

    **GitHub Actions** — сервис GitHub, который позволяет автоматизировать любой процесс связанный с деплоем кода на продакшн сервер. Код проекта выполняется на виртуальных серверах GitHub и далее может быть доставлен туда, куда нужно.

    **Деплой** (или развёртывание) — процесс размещения готового программного продукта (приложения, сайта) на сервере или в облаке, где его смогут использовать другие люди через интернет. Проще говоря, это перенос программы из среды разработки на "боевой" сервер, чтобы пользователи могли с ней работать.

    **Workflow** — последовательность выполнения задач или поток выполнения действий. Задачи внутри workflow называются `jobs` (работы), но обычно их не переводят, а так и называют — джобы. Джобы состоят из шагов (`steps`), которые содержат команды для выполнения workflow — инструкция `run` или экшены — инструкция `uses`.

    **Пайплайн** (от англ. pipeline) — то же самое что в терминологии GitHub означает Workflow — последовательность этапов или шагов, через которые проходит проект, продукт или процесс от начала до конца. Описывается в yml-файле и размещается непосредственно в рабочем репозитории в директории `.github/workflows/workflowname.yml`.

    **YAML** — формат для записи данных (чаще всего конфигурационных файлов), который создан для удобства людей и легко читается благодаря простому синтаксису, основанному на отступах.

## Заметки

???+ note "Заметки"

    1. Есть разночтения в файле `.github/workflows/ci.yml` в параметре path:   
    `path: .cache` - в [гайде](https://jameswillett.dev/getting-started-with-material-for-mkdocs/#publish-site-to-github-pages) James Willett (использую в настоящий момент);   
    `path: ~/.cache` - в [документации](https://squidfunk.github.io/mkdocs-material/publishing-your-site/#with-github-actions) Material for MkDocs.   
    Очевидно, что James Willett использовал код из официальной документации. Пока не понятно чем обусловлена разница.

    2. Есть разница между конфигурационными yml-файлами James Willett [ссылка](https://jameswillett.dev/getting-started-with-material-for-mkdocs/#publish-site-to-github-pages) и Thomas Wilde [ссылка](https://thomaswildetech.com/software-development/github/workflows/deploy-to-github-pages/):   
    По используемому параметру `if: github.event.repository.fork == false` очевидно, что Thomas Wilde имеет доступ к платной версии [Insiders Edition](https://squidfunk.github.io/mkdocs-material/insiders/). Пока не разобрался в других отличиях применительно к бесплатной версии.

    3. Думаю при формировании этого сайта будет логичным: совместно с изучением [документации](https://squidfunk.github.io/mkdocs-material/) Material for MkDocs посматривать в [репозиторий](https://github.com/squidfunk/mkdocs-material) этой документации.

??? success "Тут просто разобрался как вставить скриншот"

    [![Creating your site]][Creating your site]

      [Creating your site]: assets/screenshots/creating-your-site.png