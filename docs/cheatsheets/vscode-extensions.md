## Условные обозначения

!!! note ""

    - [x] — расширение активно (Enable)
    - [ ] — установлено, но отключено (Disable)

## Базовые расширения

- [x] [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) — поддержка языка Python, опционально:
    * [x] [Pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance) — функции IntelliSense: автодополнение, проверка типов, навигация по коду, семантическая раскраска
    * [x] [Python Debugger](https://marketplace.visualstudio.com/items?itemName=ms-python.debugpy) — отладчик
    * [ ] [Python Environments](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-python-envs) — у версии _`Preview`_ ^^конфликт с conda^^
- [x] [Jupyter](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter) — поддержка файлов Jupyter Notebook (.ipynb), опционально:
    * [ ] [Jupyter Cell Tags](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.vscode-jupyter-cell-tags) — _`Preview`_
    * [x] [Jupyter Keymap](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter-keymap) — набор сочетаний горячих клавиш, используемый в среде JN для управления ячейками в выполнения команд
    * [x] [Jupyter Notebook Renderers](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter-renderers) — средства визуализации для выходных данных JN
    * [ ] [Jupyter Slide Show](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.vscode-jupyter-slideshow) — _`Preview`_
- [x] [Rainbow CSV](https://marketplace.visualstudio.com/items?itemName=mechatroner.rainbow-csv) — подсветка столбцов в CSV
- [x] [Ruff](https://marketplace.visualstudio.com/items?itemName=charliermarsh.ruff) — лучший линтер и форматтер кода для Python
!!! quote ""

    * _helpful: [официальный сайт](https://docs.astral.sh/ruff/) и YouTube [tutorial](https://www.youtube.com/watch?v=828S-DMQog8) от Corey Schafer_
    * _поскольку Pylance тоже имеет встроенный линтер, чтобы не дублировать проверки Ruff целесообразно ^^отключить функции линтинга Pylance^^_

- [x] Просмотрщик PDF — [PDF Viewer](https://marketplace.visualstudio.com/items?itemName=mathematic.vscode-pdf) или [vscode-pdf](https://marketplace.visualstudio.com/items?itemName=tomoki1207.pdf)
- [x] [YAML](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml) — поддержка языка YAML
- [ ] [MyPy](https://marketplace.visualstudio.com/items?itemName=matangover.mypy) — проверка типов
!!! quote ""

    * _требуется настройка для совместной работы с Pylance (^^отключить проверку типов^^) и Ruff_

- [x] [Git Graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph) — графическое представление истории коммитов Git (_увидел у [Thomas Wilde](https://thomaswildetech.com/software-development/github/workflows/deploy-to-github-pages/), понравилось_)

---

!!! info "_Продолжение следует ..._"
    
    * _расширения для телеграм-ботов (:emojisense:, Error Lens)_
    * _раширения для ИИ (GitHub Copilot, KiloCode AI Agent с моделью Supernova, JetBrains AI Assistant)_
    * _нюанс в Cursor: вместо Pylance может установиться [Cursor Pyright](https://forum.cursor.com/t/cursor-pyright-python-extension-information/92522) - это норм._
    * _ссылки: полезные плагины в [Stepik](https://stepik.org/lesson/759383/step/4?unit=761399) и [статье](https://habr.com/ru/companies/timeweb/articles/916040/) Habr_