# Duplicate articles detection

Записывает хеши контента статьи в KV базу (LMDB)

Notes:

- Хеш контента игнорирует всю пунктуацию и html теги
- Обычно на каждый файл сохраняется по 5-10 хешей (параграфы 1-2, 2-3 и т.д.)
- Один дополнительный хеш сохраняется для полного текста стать (если она длиннее двух параграфов)
- Параграфы делятся по тегам ```</p>``` и ```</br>```.
- Сохраняется в формате: content_hash -> file_id

## Использование

```python
import dupl_detect.detect as detect
```

указать путь к базе
```python
detect.init('path_to_db')
```
добавить новую статью
```python
result = detect.put('path_to_file')
```
Возвращает словарь с двумя ключами
```python
{'max_intersection': 0.89, 'files': {'file1': 0.33, 'file2': 0.56 }
```
```max_intersection``` - пересечение с имеющимися в базе частями статей  
число от 0 до 1 (для новой статьи = 0, для статьи которая уже есть в базе = 1)  
рассчитывается как отношение количества совпавших хешей (с хешами всех статей имеющихся в базе) к числу хешей добавляемой статьи  
```files``` - словарь, ключами которого являются id файлов в которых найдены пересечания, а значениями показатель пересечения  
рассчитывается как отношение количества совпавших хешей (с этм конкретным файлом) к числу хешей добавляемой статьи

*Если части добавляемой статьи являются подмножеством частей уже добавленных статей, но при этом добавляемая статья не совпадает в точности ни с одной ранее уже добавленной, то ```max_intersection``` будет менее единицы. А точнее n / (n + 1) (где n - количество частей добавляемой статьи).
Аналогично, если добавляемая статья является подможеством ранее добавленной статьи, то пересечение с этой статьей так-же будет менее 1.*

## Запуск тестов
```python
python -m unittest dupl_detect/test/test.py
```

## Структура


```bash
dupl_detect
├── test        # тесты
├── utils       # вспомогательные функции
└── detect.py   # основной код
```