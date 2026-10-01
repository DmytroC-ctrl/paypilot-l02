# paypilot-l02
Домашнє завдання №1: вхід з L01 і Quality Bar Proposal

## Вміст

| Файл | Що це |
| --- | --- |
| `quality-bar-proposal.md` | Розділ 0 (вхід з L01) і розділи 1–7 |
| `l02-clean-lesson-02-20261001-135517.json` | Сирий звіт прогону, з якого взято всі числа розділів 1–7 |
| `cases.json` | Набір із 13 кейсів |
| `l02_eval.py` | Скрипт прогону (DeepEval + доменна перевірка рушіями стенда) |
| `requirements.txt` | Залежності скрипта |

## Параметри прогону

| Параметр | Значення |
| --- | --- |
| Модель судді | `claude-haiku-4-5` (провайдер Anthropic, `JUDGE_MODEL` за замовчуванням) |
| Профілі | `clean` ×2 (baseline), `lesson-02` ×3 |
| Кейсів | 13 |
| Clock | `2026-09-15T10:00:00Z` |
| Дата прогону | 2026-10-01 |

## Відтворення прогону

Потрібен локальний `paypilot-stand` (скрипт перемикає профілі, ставить годинник і скидає дані, тож лише локальний стенд).

Команда, якою зроблено прогін (зі стенда):

```bash
docker compose run --rm -T eval --runs 3 --baseline-runs 2
```

Те саме напряму:

```bash
pip install -r requirements.txt
export ANTHROPIC_API_KEY=...            # ключ для судді
export STAND_DIR=../paypilot-stand      # звідси імпортуються рушії-оракули
export SERVICE_URL=http://localhost:8000
python l02_eval.py --profiles clean,lesson-02 --runs 3 --baseline-runs 2
```

Звіт запишеться в `reports/l02-clean-lesson-02-<дата>-<час>.json`. Щоб побачити кількість викликів без витрат, додайте `--dry-run`.
