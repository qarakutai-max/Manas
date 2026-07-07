# Инструкция: Клод как генератор промтов для Nano Banana 2 (раскадровка)

## 1. Задача

Я (Клод) выступаю в роли **сценографа/художника-раскадровщика**, который переводит твоё описание кадра на русском в готовый промт на английском для генерации эскиза в Nano Banana 2.

Проект — фильм/сериал с постоянными персонажами и локациями, поэтому **консистентность важнее всего остального**. Один и тот же персонаж в кадре 3 и кадре 47 должен выглядеть как один и тот же человек.

## 2. Что ты присылаешь мне (вход)

Для каждого кадра — минимум:
- **Номер кадра / сцены**
- **Что происходит** (действие, 1-2 предложения)
- **Кто в кадре** — если персонаж уже описан в "библии" (см. п.3), просто имя. Если новый — краткое описание.
- **Локация** — если новая, описание; если старая — просто название.
- (по желанию) настроение, время суток, план (крупный/средний/общий)

Если чего-то не хватает — я сам предположу разумный вариант и помечу это, а не буду переспрашивать по каждой мелочи.

## 3. Библия консистентности (Character & Location Bible)

Это ключевой инструмент. Заводим один документ (в этом чате или отдельным файлом), где на каждого персонажа и локацию — **фиксированное текстовое описание**, которое я буду **дословно повторять** в каждом промте.

Пример карточки персонажа:
```
ГЕРОЙ — Максим:
Man in his early 30s, short dark brown hair, light stubble,
angular jawline, wearing a worn olive-green field jacket over
a grey henley, dark jeans, scuffed leather boots. Calm, tired eyes.
```

Пример карточки локации:
```
ЛОКАЦИЯ — Гараж-мастерская:
Cluttered garage workshop, concrete floor stained with oil,
workbench along the back wall covered in tools, single bare
bulb hanging from the ceiling, warm amber light, dusty air.
```

Правило: **описание персонажа/локации копируется в промт слово в слово** каждый раз, когда он появляется в кадре — не переформулируется заново. Это даёт модели строить многопанельные истории с консистентными чертами, одеждой и предметами.

Если у тебя уже есть референсные изображения персонажей — их тоже можно подавать в Nano Banana 2 вместе с текстом (модель поддерживает до нескольких референсных картинок за раз для удержания внешности).

## 4. Визуальный стиль проекта (зафиксировано)

Проект: эпос «Манас». Стиль — **живописная кинематографичная иллюстрация**, matte oil-painting, без глянца цифровой графики. Тон тёмный, приглушённый, атмосферный — не плакатный.

### 4.1 Константа палитры (не меняется никогда)
Базовые оттенки, которые присутствуют в КАЖДОМ кадре независимо от сюжета:
- charcoal (уголь/графит)
- burnt umber (жжёная умбра)
- dusty orange (пыльный оранжевый)

Общий тон всегда тёмный и десатурированный — это держит визуальное единство сериала, даже когда меняется настроение сцены.

### 4.2 Переменная — источник и температура света (меняется по сцене)
- **Боевые/динамичные сцены** — тёплый свет от огня (пожар, факелы)
- **Спокойные сцены** — тёплый низкий свет заката ИЛИ холодный лунный свет ночью *(этот регистр ещё предстоит протестировать отдельно)*
- Правило: свет всегда физически мотивирован одним реальным источником в кадре — никакого "магического" цветного рим-лайта без причины.

### 4.3 Различие "свой / чужой" в батальных сценах
Не через цвет освещения (физически необоснованно), а через **деталь**:
- Союзники — небольшой красный акцент (кушак/шарф/лента)
- Противники — бледный серо-белый акцент (флаг/бунчук)
Оба освещены одним и тем же источником света сцены.

### 4.4 Технические константы боевого стиля
- Плотная фактура холста, видимое зерно (canvas grain + едва заметный film grain)
- Дым, пыль, искры/зола на переднем плане как атмосферный слой
- Лёгкая виньетка по краям кадра
- Кадр без рамки, изображение уходит в край
- Кыргызская орнаментика — конкретно, не общей фразой (например: "chevron-and-diamond ilme-oymo geometric pattern" на снаряжении), формулировка фиксируется в библии, а не придумывается каждый раз заново

### 4.5 Эталонный боевой промт (рабочий, проверенный)
```
Painterly cinematic illustration, dense matte oil-painting texture
with heavy visible canvas grain and subtle film noise — dark,
moody value range, avoid bright or glossy digital rendering.
Single warm firelight source illuminating the entire scene, no
unmotivated colored rim lighting. Fixed core palette: charcoal,
burnt umber, dusty orange, kept dark and desaturated overall.
Allied figures identified by a small red fabric sash or scarf
accent; opposing figures identified by a small pale grey-white
flag or banner, both lit only by the same warm firelight — no
artificial glow separating them. Heavy atmospheric haze with
drifting embers and dust in the foreground, distant riders
partially obscured by smoke. No frame border, image bleeds to
the edge. No letterboxing, no black bars at any edge — image
fills the entire canvas. Dynamic action pose captured mid-motion.
```

### 4.6 Ещё не решено
- [ ] Спокойный регистр (закат/луна) — протестировать отдельно на нейтральной сцене
- [ ] Финально свести оба регистра под одну формулировку константы, чтобы переключение между ними было просто заменой 1-2 фраз, а не полной переписью промта

### 4.7 Спокойный регистр (зафиксировано)

Та же константа палитры и живописная фактура, что и в боевом регистре, но источник света — **закат**, без огня/дыма/искр. Насыщенность — небольшое яркое пятно строго вокруг солнца, остальная сцена держится в приглушённой гамме (не заливать всё небо цветом — модель легко срывается в плоский цифровой градиент, если не указать явно "brushwork throughout, including the sky").

Рабочий промт (общий план, крупный масштаб пейзажа):
```
Painterly cinematic illustration, dense matte oil-painting texture
with visible canvas grain and brushwork throughout, including the
sky — sunset clouds rendered as loose, textured brushstrokes, not
a smooth digital gradient. Subtle, restrained film grain, barely
noticeable. Dark, moody value range for foreground and figures,
avoid bright or glossy digital rendering. Warm saturated orange-red
glow concentrated tightly around the sun itself, fading quickly
into the muted dusty core palette (charcoal, burnt umber, dusty
orange) across the rest of the sky and landscape — the saturation
should feel like a small warm ember in a mostly muted scene, not
an even gradient wash. Calm and quiet mood, no fire, no smoke.
Thin natural haze softening the distant mountains, visible painterly
texture in the grass and rocky ground in the foreground. No frame
border or letterboxing, no black bars at any edge, image fills the
entire canvas edge to edge.
```

Этот же световой/палитровый блок работает и для более крупного плана (тот же герой ближе к камере) — меняется только Composition (план/ракурс), сам блок стиля и света остаётся неизменным. Оба масштаба (дальний общий и более крупный) держим как варианты кадровки одного регистра — выбор между ними чисто по монтажной надобности кадра, не по стилю.

Ещё не протестировано: ночной/лунный вариант спокойного регистра.

### 4.8 Дневной спокойный регистр (зафиксировано)

Дневной свет — самый рискованный регистр: естественно тяготеет к холодному/зелёному и к светлому небу, что рвёт тональное единство с боевым и закатным регистрами. Решение — **не ясный день, а грозовой пасмурный**: тёмное тяжёлое небо, рассеянный тусклый свет, без прямого солнца. Это держит нужную тональную темноту и настроение "тревожного ожидания".

Ключевые ограничения, без которых модель уводит в светлое/зелёное:
- явно требовать "storm-heavy", "dark grey clouds", "low overall brightness"
- явно запрещать зелень: "no greens, no cool blue-grey tones... vegetation rendered in dry dusty ochre and umber"
- явно указывать "matching the same tonal darkness as firelit and sunset scenes" — чтобы модель сверялась с общим тоном проекта, а не с обычным "пасмурным днём"

Рабочий промт:
```
Painterly cinematic illustration, dense matte oil-painting texture
with visible canvas grain and brushwork throughout, including the
sky — clouds rendered as loose, textured brushstrokes, not a
smooth digital gradient. Subtle, restrained film grain, barely
noticeable. Overcast, storm-heavy daylight — thick dark grey
clouds filling most of the sky, diffused dim light with no direct
sun, low overall brightness, closer to dusk than a bright midday.
No harsh shadows. Strictly keep the core palette: charcoal, burnt
umber, dusty orange — no greens, no cool blue-grey tones anywhere
in the grass, clothing, or ground; vegetation rendered in dry
dusty ochre and umber, not green. Dark, moody overall value range,
matching the same tonal darkness as firelit and sunset scenes.
Thin natural haze softening the distant mountains, visible
painterly texture in the grass and rocky ground in the foreground.
No frame border or letterboxing, no black bars at any edge, image
fills the entire canvas edge to edge.
```

Как и в закатном регистре — Composition (план/масштаб) меняется свободно под конкретный кадр, а сам блок света/палитры остаётся неизменным.

Ещё не протестировано: ночной/лунный вариант.

### 4.9 Мирный регистр (зафиксировано)

Отдельный, третий тип настроения — не драма/ожидание (закат, гроза), а спокойная бытовая жизнь: стойбище, семья, повседневность. Задача: сделать сцену **светлее и теплее**, не покидая цветовую семью проекта.

Главный риск — модель по умолчанию тянет "мирная сцена" в сторону синего неба и сочной зелёной травы (обычная книжная иллюстрация). Это нужно явно запрещать, а не полагаться на общее "в том же стиле":
- небо — тёплое кремовое/охристое, не насыщенно-синее
- трава/растительность — сухая золотисто-коричневая, не яркая зелень
- палитра остаётся той же семьи (charcoal, burnt umber, dusty orange, warm ochre), просто выше по светлоте

Рабочий промт:
```
Painterly cinematic illustration, dense matte oil-painting texture
with visible canvas grain and brushwork throughout, including the
sky — clouds rendered as loose, textured brushstrokes, not a
smooth digital gradient. Subtle, restrained film grain, barely
noticeable. Warm hazy morning sunlight, soft golden-white sky with
minimal blue — sky rendered in warm cream and pale ochre tones
rather than saturated blue. Strictly keep the core palette family:
charcoal, burnt umber, dusty orange, warm ochre — dry grassland
rendered in golden-brown and dusty tan, NOT vivid green; only
muted sage-brown undertones in vegetation. Peaceful and lively
mood, brighter and warmer than the dramatic registers, but from
the same tonal family — never a clean bright-blue-sky, saturated-
green-grass look. Thin natural haze softening the distant
mountains, visible painterly texture throughout. No frame border
or letterboxing, no black bars at any edge, image fills the entire
canvas edge to edge.
```

### 4.10 Общее правило против анахронизмов

В мирных/бытовых сценах модель иногда добавляет случайные современные предметы (в тесте проскочила игрушечная машинка на фоне). Чтобы это не повторялось — в КАЖДЫЙ промт (не только мирный регистр) добавляется финальная строка-ограничитель:

```
No anachronistic objects, strictly traditional nomadic setting only.
```

### 4.11 Нейтральный / переходный регистр (зафиксировано)

Пятый регистр — не драма и не радость, а состояние "между событиями": дорога, ожидание, разведка, неопределённость. Светлее и спокойнее грозового, но без тепла и жизни мирного регистра — тихий, задумчивый, приглушённо-нейтральный.

Рабочий промт:
```
Painterly cinematic illustration, dense matte oil-painting texture
with visible canvas grain and brushwork throughout, including the
sky — clouds rendered as loose, textured brushstrokes, not a
smooth digital gradient. Subtle, restrained film grain, barely
noticeable. Overcast daylight, thick pale clouds filling most of
the sky with soft warm light breaking faintly at the horizon,
diffused dim light, no direct sun visible. No harsh shadows. Keep
within the core palette family: charcoal, burnt umber, dusty
orange, muted olive-brown vegetation — avoid vivid green or clean
blue sky. Quiet, contemplative, uncertain mood — neither dramatic
nor cheerful, a sense of travel, waiting, or in-between moments.
Thin natural haze softening the distant mountains, visible
painterly texture in the grass and rocky ground in the foreground.
No frame border or letterboxing, no black bars at any edge, image
fills the entire canvas edge to edge. No anachronistic objects,
strictly traditional nomadic setting only.
```

### 4.12 Сводка регистров настроения проекта

| Регистр | Источник света | Настроение |
|---|---|---|
| Боевой | огонь | экшен, угроза |
| Закатный | закат, локальная насыщенность у солнца | драма, созерцание |
| Грозовой | тяжёлые тучи, рассеянный тусклый свет | тревожное ожидание |
| Мирный | тёплый рассеянный дневной свет | быт, радость |
| Нейтральный/переходный | бледный пасмурный, лёгкий тёплый край | дорога, неопределённость |
| Ночной/лунный | луна (холод локально), тёплая тень вокруг | тишина, ожидание, ночная стража |
| Рассветный | тонкая полоса тепла на горизонте, ночь ещё в небе | начало, предвкушение |
| Мистический/обрядовый | бесплотное холодное свечение духа, реальный фон тёплый | видение, потустороннее |
| Скорбь / последствия боя | тлеющие угли, пасмурное холодное небо | горе, опустошение |

Все шесть держатся на одной палитровой семье (charcoal / burnt umber / dusty orange / warm ochre) и одной технике (matte oil-painting, зерно холста, мазок в небе) — различается только источник света и степень насыщенности/светлоты.

### 4.13 Ночной/лунный регистр (зафиксировано)

Как и закат — холод локализован строго вокруг источника (луны), остальная сцена остаётся в тёплой тёмной гамме проекта. Явный запрет на общий синий тон сцены обязателен, иначе модель тонирует всю ночь в холодный.

Рабочий промт:
```
Painterly cinematic illustration, dense matte oil-painting texture
with visible canvas grain and brushwork throughout, including the
sky — clouds and stars rendered as loose, textured brushstrokes,
not a smooth digital gradient. Subtle, restrained film grain,
barely noticeable. Night scene lit primarily by a bright full moon
— cool pale blue-white moonlight concentrated tightly around the
moon itself and as soft highlights on edges and metal surfaces
only, while the bulk of the scene (ground, clothing, vegetation,
shadow areas) remains within the warm dark core palette: charcoal,
burnt umber, dusty orange — do not tint the overall scene blue,
the coolness stays confined to direct moonlight highlights. Deep
dark shadows dominate the frame. Thin drifting night haze around
distant mountains. No frame border or letterboxing, no black bars
at any edge, image fills the entire canvas edge to edge. No
anachronistic objects, strictly traditional nomadic setting only.
```

### 4.14 Боевой регистр — дневной вариант (зафиксировано)

Тот же боевой регистр, но источник света — рассеянное дневное солнце сквозь пыль/дым, а не огонь. Палитра и тональная тёмность держатся такими же, как в огненном варианте — деталь "свой/чужой" работает так же (красный акцент/бледный акцент).

Рабочий промт:
```
Painterly cinematic illustration, dense matte oil-painting texture
with visible canvas grain and brushwork throughout, including the
sky — subtle, restrained film grain, barely noticeable. Dark,
moody value range, avoid bright or glossy digital rendering.
Overcast daylight battle scene — diffused grey-white sun filtered
through thick dust and smoke kicked up by the clash, no direct
sun visible, no fire as the primary light source. Fixed core
palette: charcoal, burnt umber, dusty orange, kept dark and
desaturated overall — no clean blue sky, no bright daylight.
Allied figures identified by a small red fabric sash or scarf
accent; opposing figures identified by a small pale grey-white
flag or banner, both lit only by the same diffused daylight — no
artificial colored glow separating them. Heavy dust and drifting
debris in the foreground, distant riders partially obscured by
haze. No frame border or letterboxing, no black bars at any edge,
image fills the entire canvas edge to edge. Dynamic action pose
captured mid-motion. No anachronistic objects, strictly
traditional nomadic setting only.
```

**Известная проблема, требует решения:** в тесте на заднем плане одновременно оказались синие и красные флаги у разных групп статистов — приём "красный акцент = свои, бледный/серый = чужие" размылся, когда фон сам добавил случайные яркие цвета. Нужно явно ограничивать цвет фоновых/массовых персонажей в промте (например, прямо прописывать цвет флагов для каждой группы массовки, не полагаясь на то, что модель сама будет последовательна) — доработать при следующем тесте с массовкой.

### 4.15 Рассветный регистр (зафиксировано)

Отличается от заката по смыслу, не только по свету: тонкая полоса тёплого света у самого горизонта, а небо над головой ещё держит остатки ночи — свет "наступает", а не "гаснет". Плюс предутренние детали (роса, пар от дыхания, низкий туман), которых нет в закате — они и создают ощущение "начала".

Рабочий промт:
```
Painterly cinematic illustration, dense matte oil-painting texture
with visible canvas grain and brushwork throughout, including the
sky — sunrise clouds rendered as loose, textured brushstrokes, not
a smooth digital gradient. Subtle, restrained film grain, barely
noticeable. Dark, moody value range overall, avoid bright or
glossy digital rendering. Early dawn light — a thin band of warm
orange-gold breaking low on the horizon where the sun is about to
rise, while the rest of the sky above still holds the last dim
tones of night, gradually softening rather than fully dark. Warm
saturated glow concentrated tightly at the horizon line itself,
fading into the muted dusty core palette (charcoal, burnt umber,
dusty orange) across the rest of the sky and landscape — same
principle as sunset, but the light feels like it is beginning
rather than fading. Cool morning mist clinging low to the ground,
dew visible on grass and stone in the foreground. Mood: quiet
anticipation, a sense of beginning rather than closure — alert
and still, not melancholic. Thin natural haze softening the
distant mountains. No frame border or letterboxing, no black bars
at any edge, image fills the entire canvas edge to edge. No
anachronistic objects, strictly traditional nomadic setting only.
```

### 4.16 Мистический/обрядовый регистр (зафиксировано)

Единственный регистр, где сознательно **нарушается** правило "свет всегда физически мотивирован" — цель показать нереальное. Приём: бесплотный холодный призрачный свет без физического источника у духа/видения, при этом окружающая "реальная" часть кадра остаётся в обычной тёмной тёплой палитре проекта — так граница между реальным и потусторонним читается чётко, не смешиваясь в общую кашу.

Рабочий промт:
```
Painterly cinematic illustration, dense matte oil-painting texture
with visible canvas grain and brushwork throughout — subtle,
restrained film grain, barely noticeable. Dark, moody value range,
avoid bright or glossy digital rendering. Supernatural, dreamlike
atmosphere — an unnatural pale spectral glow with no physical light
source, cool and colorless-white rather than warm, emanating from
a translucent ancestor-spirit figure that seems to be made of mist
and faint light rather than solid form, semi-transparent, edges
dissolving into smoke. The rest of the scene remains within the
core palette (charcoal, burnt umber, dusty orange), kept dark and
desaturated, grounding the vision in the real world around it.
Swirling mist moves in unnatural spiral patterns, not following
wind logic. Mood: reverent, eerie, otherworldly — a vision or
prophetic dream, not a physical event. Thin haze blurring the
boundary between the real figure and the spectral one, slight
dreamlike softness to the entire image as if seen in sleep. No
frame border or letterboxing, no black bars at any edge, image
fills the entire canvas edge to edge. No anachronistic objects,
strictly traditional nomadic setting only.
```

Побочная находка: тест заодно дал хороший визуальный ориентир для **интерьера юрты** (орнамент на кереге/решётчатых стенах, ковры, развешанное оружие) — но отдельно интерьер как регистр (с обычным дневным/огненным светом, без мистики) ещё предстоит протестировать самостоятельно.

### 4.17 Интерьер юрты (зафиксировано)

Отдельный регистр пространства (не света) — внутри юрты, огонь очага как единственный источник, свет и дым уходят вверх через тюндюк. Подтверждён на двух разных типах сцен (совет и семья) — базовый блок стабилен, меняется только состав персонажей и Subject.

**Базовый блок (не меняется):**
```
Painterly cinematic illustration, dense matte oil-painting texture
with visible canvas grain and brushwork throughout, subtle
restrained film grain, barely noticeable. Dark, moody value range,
avoid bright or glossy digital rendering. Interior of a yurt at
night — the only light source is a central hearth fire, warm
firelight illuminating faces and objects nearest to it while the
edges of the round tent dissolve into deep shadow, smoke rising
toward the tunduk opening at the apex of the roof, a shaft of pale
light and smoke visible through the opening. Fixed core palette:
charcoal, burnt umber, dusty orange, kept dark and desaturated
overall. Rich interior detail: carved and painted wooden lattice
walls (kerege) with scrolling ornamental patterns, layered
patterned carpets on the floor, felt wall hangings with geometric
ilme-oymo ornament. Thin haze of smoke softening the upper frame
near the tunduk. No frame border or letterboxing, no black bars
at any edge, image fills the entire canvas edge to edge. No
anachronistic objects, strictly traditional nomadic setting only.
```

**Проверенные варианты Subject/Composition:**

1. **Совет** (протестировано, эталон): «A council of several Kyrgyz men seated in a circle around the central hearth fire, deep in serious discussion, firelight catching their faces and the weapons hung on the wall behind them. Medium-wide shot, eye-level, camera positioned just inside the yurt entrance looking toward the hearth, figures arranged in a loose circle around the fire.»

2. **Семья** (протестировано, эталон): небольшая группа (2-3 человека) у очага в спокойной бытовой сцене, посуда и утварь на полу, более тихая и тёплая интонация, чем в совете — тот же свет и пространство.

**Шаблоны на будущее (ещё не тестировались, менять только Subject):**
3. Уединение героя — один персонаж сидит в тишине у огня, задумчив
4. Пир/праздник — много людей, дастархан, чаши, оживлённая композиция
5. Отдых/сон — спящий персонаж у гаснущего огня (без мистического элемента — просто сцена отдыха)

### 4.18 Скорбь / последствия боя (зафиксировано)

Противоположность боевому регистру: статика вместо движения, тлеющие угли и зола вместо активного пламени, пасмурное холодное небо без прямого света. Палитра сдвинута к холодным пепельным тонам внутри той же семьи (умбра/уголь остаются, но огонь — умирающий, не активный).

Рабочий промт:
```
Painterly cinematic illustration, dense matte oil-painting texture
with visible canvas grain and brushwork throughout, subtle
restrained film grain, barely noticeable. Dark, moody value range,
avoid bright or glossy digital rendering. Aftermath of battle —
smoldering embers and thin wisps of smoke rising from burned-out
yurts and scorched ground, pale grey overcast sky with no visible
sun, dim diffused light. Fixed core palette: charcoal, burnt umber,
dusty orange, but shifted toward cold grey ash tones rather than
vivid fire — the orange here is dying embers, not active flame.
Fine ash drifting slowly through the air like snow, settling on the
ground and on still objects. Complete stillness — no motion, no
dynamic poses, a static and heavy silence. Mood: grief, desolation,
quiet mourning rather than action. Thin haze softening the distant
mountains. No frame border or letterboxing, no black bars at any
edge, image fills the entire canvas edge to edge. No anachronistic
objects, strictly traditional nomadic setting only.
```

## 5. Структура промта, который я буду выдавать (общий шаблон)

Каждый промт строится по формуле (это то, на что реально реагирует модель):

1. **Subject / Action** — кто и что делает (из библии + действие в кадре)
2. **Environment** — локация (из библии)
3. **Composition & Camera** — план (крупный/средний/общий), угол камеры, объектив
4. **Lighting & Mood** — свет, атмосфера, время суток
5. **Style** — стиль эскиза (это нужно зафиксировать один раз для всего проекта — чёрно-белый скетч / цветной концепт-арт / кинематографичный реализм и т.д.)
6. **Aspect ratio** — соотношение сторон кадра (16:9 для кино, 2.39:1 для широкого кадра и т.п.)
7. **Exclusions** — чего не должно быть в кадре (если важно)

Промт пишется как бриф для художника-постановщика, не как список тегов — лучше писать как будто инструктируешь человека-арт-директора, но при этом плотно упаковывая детали.

## 6. Формат моего ответа

На каждый кадр я даю:

```
КАДР №[X]

PROMPT (EN):
[готовый промт на английском, копируешь прямо в Nano Banana 2]

Пояснение (RU):
[коротко: что учтено, какие допущения я сделал, на что обратить внимание при генерации]
```

## 7. Пример

**Твой ввод:** «Кадр 12: Максим заходит в мастерскую, включает свет, средний план»

**Мой ответ:**
```
КАДР №12

PROMPT (EN):
Man in his early 30s, short dark brown hair, light stubble,
angular jawline, wearing a worn olive-green field jacket over
a grey henley, dark jeans, scuffed leather boots, calm tired eyes —
entering a cluttered garage workshop, concrete floor stained with
oil, workbench along the back wall covered in tools, reaching to
flip a light switch by the door. Medium shot, eye-level angle,
50mm lens. Single bare bulb flickering on, warm amber light
spreading across the room, dusty air catching the light. Black
and white pencil-sketch storyboard style, loose expressive linework.
16:9 aspect ratio.

Пояснение (RU):
Взял описание Максима и мастерской из библии без изменений.
Добавил момент включения света как основное действие кадра.
Стиль и формат кадра — по умолчанию проекта (Ч/б скетч, 16:9).
Если план должен быть ближе — скажи, поправлю на крупный.
```

## 8. Правила консистентности между кадрами

- Не переформулирую описания персонажей/локаций — только копирую из библии.
- Если персонаж меняет одежду/состояние по сюжету (например, ранен, промок) — это фиксируется как **новая версия карточки** с пометкой, с какого кадра действует.
- При добавлении нового персонажа/локации — сначала предлагаю карточку для библии, потом уже промт.
- Если нужно отредактировать уже сгенерированный кадр (а не сгенерировать новый) — говори "правка", тогда промт строится иначе: явно указываю, **что меняется**, а что **остаётся без изменений** — так работает semantic editing в Nano Banana 2.

## 9. Статус проекта

- [x] Визуальный стиль — живописная кинематографичная иллюстрация
- [x] Aspect ratio — 16:9
- [x] Боевой регистр (огонь) — зафиксирован
- [x] Спокойный регистр (закат) — зафиксирован, два масштаба кадровки
- [x] Спокойный регистр (день, грозовая облачность) — зафиксирован
- [x] Мирный регистр (быт, светлый день) — зафиксирован
- [x] Нейтральный/переходный регистр (дорога, ожидание) — зафиксирован
- [x] Ночной/лунный регистр — зафиксирован
- [x] Боевой регистр — дневной вариант — зафиксирован
- [x] Рассветный регистр — зафиксирован
- [x] Мистический/обрядовый регистр — зафиксирован
- [x] Интерьер юрты (совет + семья, ещё 3 варианта шаблоном) — зафиксирован
- [x] Скорбь / последствия боя — зафиксирован
- [x] Правило против анахронизмов — добавлено во все промты
- [ ] Доработать промт массовки в боевых сценах — цвет флагов "свой/чужой" иногда путается на заднем плане
- [ ] Открытый вопрос: способ синхронизации с GitHub/Obsidian для памяти между сессиями — пока работаем через ручную загрузку файлов
- [ ] Библия персонажей и локаций — следующий шаг
- [ ] Конкретная формулировка кыргызского орнамента и породы коня — зафиксировать в библии, чтобы не "плавала" от кадра к кадру.
