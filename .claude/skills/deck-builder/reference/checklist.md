# Чек-лист сборки деки

## Содержание
- [ ] Прочитан весь документ главы; всё содержание — из него (+ идеи из `reference-lectures/`, перефразированные).
- [ ] Палитра взята из картинки в `palettes/`; перекрашены только значения токенов и `PAL`, имена не тронуты.
- [ ] Формулы крупные, с пошаговым выводом; ключевые величины подсвечены (`.c`/`.t`).
- [ ] На всех диаграммах подписаны оси (`t`, `f`, `s(t)`, `|S(f)|`, `|H|`, `U`…).
- [ ] Числовые примеры отдельными слайдами: дано → расчёт → вывод.
- [ ] Мемы только из `assets/memes/`, base64, в смысловых местах. Нет выдуманных/заглушек.
- [ ] Финальный слайд «Вопросики» с интерактивными `.qa`-карточками.
- [ ] Вставлен модуль `draw-edit-module.html` (редактор + рисование), цвета панели из палитры главы.

## Техника (прогнать перед сдачей)
- [ ] `node --check` по последнему `<script>` — без ошибок.
- [ ] `<section class="slide">` count == `</section>` count.
- [ ] Нет дублей `data-label`.
- [ ] Каждый `data-draw="X"` имеет зарегистрированный `drawers.X`.
- [ ] Каждый `cv('id')` имеет `<canvas id="id">`; лишних canvas нет.
- [ ] Ползунки привязаны `bindRange('id', fn)` с гардом `if(el)`.
- [ ] Анимации ставят `raf=requestAnimationFrame(...)`, гасятся через `stopAnim()`.
- [ ] Нет `__PLACEHOLDER__`, нет обрывков SVG-путей (`... ` внутри `d="…"`).
- [ ] Нет `localStorage`/`sessionStorage` в логике слайдов.
- [ ] Внешних зависимостей нет, кроме Google Fonts; картинки/шрифты — base64.
- [ ] Маркер `<!--SLIDES-->` удалён; файл лежит в `decks/`.

## Быстрый скрипт проверки (bash)
```bash
f=decks/glavaN.html
python3 - "$f" <<'PY'
import re,sys
h=open(sys.argv[1],encoding='utf-8').read()
import subprocess,tempfile,os
js=re.findall(r'<script>(.*?)</script>',h,re.S)[-1]
open('/tmp/_e.js','w').write(js); print('node:', subprocess.run(['node','--check','/tmp/_e.js']).returncode)
print('slides', h.count('<section class="slide'), 'sections', h.count('<section'),'/',h.count('</section>'))
draws=re.findall(r'data-draw="([^"]+)"',h); reg=set(re.findall(r'drawers\.([a-zA-Z]+) ?=',h))
print('unreg draws', [d for d in draws if d not in reg] or 'ok')
cvids=set(re.findall(r"cv\('([^']+)'\)",h)); can=set(re.findall(r'<canvas id="([^"]+)"',h))
print('cv missing canvas', sorted(cvids-can) or 'ok')
labels=re.findall(r'data-label="([^"]+)"',h)
print('dup labels', [l for l in set(labels) if labels.count(l)>1] or 'ok')
print('stray', '... ' in h, '__PLACEHOLDER__' in h, 'localStorage' in h)
PY
```
