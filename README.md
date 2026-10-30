# Backend Basics

Учебный проект для знакомства со структурой Python-проекта.
Проект создаёт задачу, хранит её в словаре в оперативной памяти,
находит по идентификатору и выводит в терминал. Создание записывается в лог.
При завершении программы данные не сохраняются.

## Требования

- Python 3.12.x.
- Git для просмотра истории коммитов.
- VS Code для работы с проектом по условию задания.
- Ruff — единственная сторонняя зависимость, нужна для разработки.

## Подготовка

Проверьте Git командой `git --version`, затем склонируйте репозиторий:

```bash
git clone https://github.com/Sofa9890/PythonX5.git backend-basics
cd backend-basics
```

Git перенесёт исходники вместе с историей коммитов.
Откройте полученную папку `backend-basics` в VS Code через File → Open Folder.
Все дальнейшие команды выполняются из этой папки.

### macOS и Linux

При установленном Python 3.12 команда `python3.12 --version`
должна показывать `Python 3.12.x`. Создайте и активируйте окружение:

```bash
python3.12 -m venv .venv
source .venv/bin/activate
python --version
python -m pip install -r requirements.txt
```

Если интерпретатор 3.12 доступен как `python3`, используйте
`python3 -m venv .venv`, предварительно проверив `python3 --version`.

### Windows PowerShell

```powershell
py -3.12 --version
py -3.12 -m venv .venv
.\.venv\Scripts\Activate.ps1
python --version
python -m pip install -r requirements.txt
```

Если PowerShell блокирует скрипт активации, можно выполнять команды
через интерпретатор окружения без активации:

```powershell
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe main.py
.\.venv\Scripts\python.exe -m ruff check .
.\.venv\Scripts\python.exe -m ruff format .
```

В VS Code выберите `.venv` как интерпретатор Python, если редактор
предлагает выбор интерпретатора.

## Запуск

После активации окружения:

```bash
python main.py
```

Ожидаемый результат:

```text
INFO:tasks:Created task
Task(id=1, title='Подготовить README', description='Добавить инструкцию запуска проекта', due_date=datetime.date(2027, 6, 30))
```

Лог выводится в stderr, а `print` — в stdout, поэтому при объединении
потоков порядок отображения двух строк иногда может отличаться.

## Проверка кода

```bash
ruff check .
ruff format .
python main.py
```

Для проверки форматирования без изменения файлов: `ruff format --check .`.
В новом терминале снова активируйте `.venv` перед командами.

## Структура

```text
backend-basics/
├── .git/             # история Git
├── src/
│   ├── __init__.py   # пустой файл пакета
│   ├── exceptions.py # TaskNotFoundError
│   ├── logger.py     # настройка logging
│   ├── models.py     # dataclass Task
│   └── services.py   # create_task и get_task
├── .gitignore
├── main.py           # сценарий запуска
├── README.md
└── requirements.txt
```

`.venv` и кеши создаются локально и в Git не включаются.
Модули `dataclasses`, `datetime` и `logging` устанавливать не нужно:
это модули стандартной библиотеки Python.

## История Git

Основная ветка — `main`. Подготовка окружения и добавление кода
зафиксированы тремя осмысленными коммитами:

1. `Initialize project environment` — `.gitignore`, зависимости, первый README.
2. `Add task model and service logic` — пакет `src`, модель, сервисы, исключение и логирование.
3. `Add entry point and usage instructions` — `main.py` и полная инструкция запуска.

```bash
git status
git log --oneline
```

После `git clone` репозиторий уже готов: выполнять `git init` не требуется.
