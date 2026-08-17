# Промты на генерацию фото — Глава 1 (технологичный стиль)

Единый визуальный язык для всех картинок (чтобы дека смотрелась одной системой).
Вставляй этот **STYLE-блок** в конец каждого промта.

## STYLE (общий хвост для всех промтов)
```
tech-editorial style, dark background (#07090f), neon magenta (#ff2e6e) and
cyan (#28e0ff) accents, thin isometric line-art + subtle glow, fine grid texture,
high contrast, clean minimal composition, no text, no logos, no watermarks,
16:9, photoreal-meets-diagram hybrid, cinematic rim light. --ar 16:9
```

Соглашение имён: сохраняй файлы как `net-ban.jpg … net-wan.jpg` рядом с
`decks/glava1-networks-test.html`, затем в слоте замени `<div class="ph">…</div>`
на `<img src="net-ban.jpg" alt="BAN">`.

---

## 1. BAN — нательная сеть → `net-ban.jpg`
```
Close-up of a person's wrist and ear wearing a smartwatch and wireless earbuds,
faint glowing signal arcs connecting the devices around the body, ≈1 meter scale,
intimate scale. STYLE
```

## 2. PAN — персональная сеть → `net-pan.jpg`
```
A single desk with a laptop, smartphone, wireless speaker and printer, glowing
short-range links forming a small personal bubble around one user, ≈10 meter
scale. STYLE
```

## 3. LAN — локальная сеть → `net-lan.jpg`
```
Cutaway of a modern apartment / small office, a central Wi-Fi router radiating
glowing links to many devices in several rooms, one building, high-speed local
network. STYLE
```

## 4. CAN — кампусная сеть → `net-can.jpg`
```
Isometric cluster of several adjacent university / corporate buildings connected
by glowing fiber trunks between rooftops, enterprise campus scale. STYLE
```

## 5. MAN — городская сеть → `net-man.jpg`
```
Stylized night city skyline, multiple sites across districts linked by glowing
backbone lines over the streets, metropolitan scale within one city. STYLE
```

## 6. WAN — глобальная сеть → `net-wan.jpg`
```
Dark planet Earth from space, glowing magenta-cyan network arcs spanning between
continents, undersea cable routes, "network of all networks", global scale. STYLE
```

---

## Доп. кадры для деки (по желанию)
- **Титул / hero** → `hero.jpg`:
  `Abstract isometric network of glowing nodes and links forming an upward flow
  from a single dot to a global mesh. STYLE`
- **Пакетная передача** → `packets.jpg`:
  `A message splitting into small glowing packets travelling along parallel
  routes and reassembling at the destination. STYLE`
- **Среды передачи** → `media.jpg`:
  `Three parallel cable cross-sections side by side — coax, twisted pair, optical
  fiber with light inside — as clean line-art specimens. STYLE`

## Заметки
- Никакого текста на картинках (подписи даёт сама дека).
- Держи ракурс и толщину линий одинаковыми у всех 6 сетей — так «зум»
  BAN→WAN читается как единая серия.
- Форматы: экспортируй в `.jpg` (или `.webp`) ~1600×900, затем можно вшить в
  HTML как base64 для полного офлайна (по правилу проекта «один файл»).
