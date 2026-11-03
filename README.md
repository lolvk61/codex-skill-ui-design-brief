# UI Design Brief for Codex

Адаптация [оригинального скилла для Claude Code](https://github.com/lolvk61/claude-skill-ui-design-brief) для Codex.

Перед созданием нового интерфейса Codex собирает короткий бриф, показывает
2–3 разных эскиза, фиксирует выбранный стиль и проверяет отрисовку. Если стиль
уже задан, нужно быстрое решение или пользователь просит работать без вопросов,
процесс сокращается. Мелкие правки не требуют нового брифа.

## Установка

В Codex попросите встроенный `$skill-installer` установить скилл:

```text
$skill-installer Установи https://github.com/lolvk61/codex-skill-ui-design-brief, путь скилла: .
```

Либо скопируйте папку репозитория под именем
`ui-design-brief` в пользовательский каталог скиллов вашей установки Codex.
Для проекта поместите содержимое в `.agents/skills/ui-design-brief/`.

Обязательная структура:

```text
ui-design-brief/
├── SKILL.md
└── agents/
    └── openai.yaml
```

После установки начните новую сессию. Можно вызвать скилл явно:

```text
$ui-design-brief Сделай интерфейс панели мониторинга домашнего сервера.
```

Автоматический выбор скилла оставлен включённым по умолчанию.

## Что адаптировано

- Вместо `AskUserQuestion` — доступные инструменты вопросов Codex с учётом режима или обычный текст.
- Вместо обязательных `preview_start`, `show_widget` и `preview` — HTML, ASCII и реально доступный предпросмотр.
- Добавлены метаданные `agents/openai.yaml`, работа с `AGENTS.md` и существующими токенами проекта.
- Визуальная проверка учитывает настоящий viewport; демонстрационные данные явно отделены от фактов.
- Сохранены исключения для быстрых задач, существующего стиля и работы без вопросов.

Формат: [официальная документация по скиллам](https://learn.chatgpt.com/docs/build-skills).

## Ручная проверка поведения

1. «Сделай сайт кофейни» — контекст, краткий бриф, затем разные эскизы до реализации.
2. «Сделай окно настроек на твой вкус, без вопросов» — выбранное направление и реализация без ожидания.
3. «Быстро набросай простой таймер» — стандартный UI без брифа и эскизов.
4. «Исправь отступ кнопки» — локальная правка в существующем стиле.
5. Новый экран в проекте с `DESIGN.md` — использование заданного стиля без повторного выбора.

Исходные тестовые запросы сохранены в `evals/evals.json`, входной HTML —
в `evals/files/`. Эти сценарии служат для проверки поведения;
автоматический прогон агента не выполнялся.

## English

A Codex adaptation of the original UI design brief skill. It gathers missing
design preferences, offers 2–3 distinct sketches, records the chosen direction,
and checks the rendered result. It supports text-only environments and available
Codex question tools without depending on Claude-specific APIs. Instructions are
in Russian; the skill follows the user's conversation language.

Use `$skill-installer` with this repository URL and path `.` or copy the skill
into `.agents/skills/ui-design-brief/` in a project. Start a new session and invoke
`$ui-design-brief`, or let Codex select it automatically for a matching task.

## License

The original repository declares the MIT license. See `LICENSE` for the original
copyright and license notice.
