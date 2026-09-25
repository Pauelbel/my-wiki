# Шпаргалка по uv

Инструмент `uv` — это современный и быстрый менеджер пакетов и инструментов для Python, написанный на Rust. Он заменяет собой `pip`, `venv`, `pip-tools` и `pipx`.

## Установка

### Windows (PowerShell)
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

### Mac / Linux
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### Через pip
```bash
pip install uv
```

**Команды обновления и проверки:**
- `uv --version` — проверить версию.
- `uv self update` — обновить сам `uv`.

## Работа с проектами

### Рекомендуемый способ (современный)
Используйте эти команды для управления зависимостями в рамках проекта:
- `uv init myproject` — создать проект с файлом `pyproject.toml`.
- `uv add requests` — добавить библиотеку (автоматически создаст `.venv`).
- `uv add --dev pytest` — добавить зависимость для разработки.
- `uv remove requests` — удалить библиотеку.
- `uv run main.py` — запустить скрипт в изолированном окружении проекта.
- `uv sync` — восстановить окружение на основе `pyproject.toml`.
- `uv lock` — обновить файл блокировки (`uv.lock`).
- `uv tree` — отобразить дерево зависимостей.

### Классическая схема (аналог pip)
Если нужно работать в стиле привычного `pip`:
- `uv venv` — создать `.venv` в текущей папке.
- `uv venv --python 3.12` — создать окружение с конкретной версией Python.
- `uv pip install requests` — установить пакет.
- `uv pip install -r requirements.txt` — установка из файла.
- `uv pip freeze > requirements.txt` — экспорт зависимостей.
- `uv pip list` — список установленных пакетов.
- `uv pip uninstall requests` — удаление пакета.

**Активация окружения:**
- Windows: `.venv\Scripts\activate`
- Mac/Linux: `source .venv/bin/activate`

## Инструменты и глобальные пакеты (аналог pipx)

Для запуска инструментов без установки в текущее окружение или их глобальной установки:
- `uvx ruff check .` — запустить инструмент без предварительной установки.
- `uv tool install ruff` — установить инструмент глобально в отдельное изолированное окружение.
- `uv tool list` — список установленных инструментов.
- `uv tool upgrade ruff` — обновить инструмент.
- `uv tool uninstall ruff` — удалить инструмент.

## Управление версиями Python

- `uv python list` — показать доступные и установленные версии.
- `uv python install 3.12` — установить конкретную версию.
- `uv python pin 3.12` — закрепить версию для текущего проекта.


## Сводная таблица соответствия pip и uv

| Действие | Pip (старый способ) | UV (новый способ) |
| --- | --- | --- |
| Создание окружения | `python -m venv .venv` | `uv venv` |
| Установка пакета | `pip install X` | `uv pip install X` или `uv add X` |
| Установка из файла | `pip install -r requirements.txt` | `uv pip install -r requirements.txt` или `uv sync` |
| Запуск скрипта | `python main.py` | `uv run main.py` |
| Глобальная установка | `pipx install X` | `uv tool install X` |
| Запуск инструмента | `pipx run X` | `uvx X` |

## Источники

- [[Архив/2026/09/2026-09-23 - Шпаргалка по uv]]
