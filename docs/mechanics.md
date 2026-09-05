# Механики

Как устроена игровая логика мода: от старта игры до пробуждения угасших империй.

## Точки входа

Всё, что мод делает по ходу игры, начинается с
[common/on_actions/gotc_on_actions.txt](../common/on_actions/gotc_on_actions.txt) —
там события мода подвешиваются к игровым хукам.

| Хук | Событие | Область | Что происходит |
|---|---|---|---|
| `on_game_start` | `gotc.1` | — | Настройка системы Киры при старте игры |
| `on_five_year_pulse_country` | `gotc.41234` | country | Проверка известных лидеров |
| `on_five_year_pulse_country` | `gotc.40000` | country | Проверка возможности найма лидера (Galactic Paragons) |
| `on_colonized` | `gotc.10` | planet | Реакция на колонизацию |
| `on_colony_transfer` | `gotc.11` | planet | Смена владельца планеты |
| `on_colony_conquer` | `gotc.11` | planet | Захват планеты (срабатывает дополнительно к transfer) |
| `on_system_gained` | `gotc.12` | country | Переход системы к новому владельцу |

## События

6 файлов, 60 событий, 4 пространства имён. Префикс `!!!_` в именах файлов обеспечивает
загрузку раньше ванильных.

| Namespace | Файл | Событий | Что покрывает |
|---|---|---:|---|
| `gotc` | [!!!_gotc_events.txt](../events/!!!_gotc_events.txt) | 25 | Собственные события мода, привязанные к `on_actions`. Часть событий — системные (`system_event`), с цепочками отложенных вызовов |
| `marauder` | [!!!_gotc_marauder_events.txt](../events/!!!_gotc_marauder_events.txt) | 22 | Дипломатия мародёров: переписаны диалоги, требования дани, наём. Крупнейший событийный файл (4957 строк) |
| `origin` | [!!!_gotc_origin_events_1.txt](../events/!!!_gotc_origin_events_1.txt) | 7 | События происхождений; ветка Scion с наградами от патрона (`@scionRewardTimer`) |
| `origin` | [!!!_gotc_origin_events_3.txt](../events/!!!_gotc_origin_events_3.txt) | 4 | Ветка сюзерена для имперских происхождений |
| `fallen_empires_awakening` | [!!!_gotc_fallen_empire_awakening_events.txt](../events/!!!_gotc_fallen_empire_awakening_events.txt) | 1 | Пробуждение угасших империй; связано с `planet_destruction.611` |
| `ancrel` | [!!!_gotc_ancient_relics_arcsite_events_2.txt](../events/!!!_gotc_ancient_relics_arcsite_events_2.txt) | 1 | Раскопки Ancient Relics (`ancrel.12055`) |

## Скриптовые эффекты

Основной инструмент мода — создание стран, флотов и станций «на лету».
Всего 82 эффекта в 5 файлах.

### `gotc_effects.txt` — 67 эффектов, 8175 строк

Самый большой файл репозитория. Основные группы:

**Анклавы Шроудходцев**
```
choose_shroudwalker_enclave_country
create_shroudwalker_enclave_country_default
create_shroudwalker_enclave_country_dialectics
create_shroudwalker_enclave_starbase_dialectics_1 / _2 / _3
```

**Имперские сюзерены и вассалы**
```
choose_imperial_overlord_country
create_overlord_soviet
create_overlord_post_soviet
change_empires_if_overlord_soviet
change_empires_if_overlord_post_soviet
find_or_create_a_way_out_for_vassal
create_imperial_vassal_international
create_imperial_vassal_mraxist
create_imperial_vassal_pamyatnik
create_imperial_vassal_rkka
create_imperial_vassal_tuva
create_imperial_vassal_stakhanov
```

Логика двухступенчатая: сначала `choose_imperial_overlord_country` определяет, какой
сюзерен появится (советский или постсоветский), затем `change_empires_if_overlord_*`
подстраивает состав вассалов под этот выбор.

**Прочее**
```
choose_fear_of_the_dark_country_korea   — привязка Кореи к происхождению Fear of the Dark
create_MSI_zion                          — вариант MSI
```

### `zzz_gotc_first_contact_dlc_effects.txt` — 11 эффектов

Контент DLC First Contact:

| Эффект | Назначение |
|---|---|
| `create_slavers_dummy_country` | Страна-работорговцы |
| `generate_slaver_bonus` | Бонусы работорговцам |
| `create_MSI_effect` | Создание MSI |
| `create_debt_collectors_country` | Сборщики долгов |
| `create_payback_digsite_fleet` | Флот раскопок Payback |
| `create_payback_debt_collectors_fleet` | Флот сборщиков долгов |
| `create_payback_warship_effect` | Военный корабль Payback |
| `spawn_payback_site_habitat` | Хабитат на месте Payback |
| `create_fear_of_the_dark_country` | Страна происхождения Fear of the Dark |
| `setup_fear_of_the_dark_pre_ftl` | Префтл для Fear of the Dark |
| `uplift_pre_ftl_with_origin_effect` | Возвышение префтл-цивилизации |

### Остальные файлы эффектов

| Файл | Эффекты |
|---|---|
| [zzz_gotc_pre_ftl_scripted_effects.txt](../common/scripted_effects/zzz_gotc_pre_ftl_scripted_effects.txt) | `spawn_presapient_species_randomizer_effect`, `spawn_presapient_species_randomizer_homeworld_effect` — рандомизация преразумных видов (2547 строк на два эффекта: почти всё — таблицы вариантов) |
| [zzz_gotc_start_of_game_effects.txt](../common/scripted_effects/zzz_gotc_start_of_game_effects.txt) | `imperial_origin_start_effect` |
| [zzz_gotc_scripted_effects.txt](../common/scripted_effects/zzz_gotc_scripted_effects.txt) | `create_zombie_pop_group` |

## Скриптовые триггеры

| Триггер | Файл | Назначение |
|---|---|---|
| `is_feline_species` | [gotc_scripted_triggers.txt](../common/scripted_triggers/gotc_scripted_triggers.txt) | Проверка, относится ли вид к кошачьим — используется фракциями котистов |

## Генерация галактики

86 инициализаторов систем в 7 файлах.

| Группа | Файл | Кол-во | Содержание |
|---|---|---:|---|
| Угасшие империи | [gotc_fallen_empire_initializers.txt](../common/solar_system_initializers/gotc_fallen_empire_initializers.txt) | 25 | `gotc_fallen_1`…`gotc_fallen_4` и системы их колоний (`gotc_fallen_col_*`) |
| Overlord DLC | [overlord_initializers.txt](../common/solar_system_initializers/overlord_initializers.txt) | 18 | Анклавы сборщиков (`salvager_enclave_init_01–03`), Шроудходцев (`shroudwalker_enclave_init_01–03`), сломанный анклав, квантовые катапульты |
| Стартовые системы | [gotc_starting_initializers.txt](../common/solar_system_initializers/gotc_starting_initializers.txt) | 18 | См. разбор ниже |
| Префтл | [gotc_pre_ftl_initializers.txt](../common/solar_system_initializers/gotc_pre_ftl_initializers.txt) | 10 | Египет, Сирия, Антиохия, Франция, Аравия, Уганда, Филистия, Иордания и др. |
| Мародёры | [marauder_initializers.txt](../common/solar_system_initializers/marauder_initializers.txt) | 9 | 3 анклава × 3 системы (`marauder_1_1`…`marauder_3_3`) |
| First Contact | [!!!_gotc_first_contact_initializers.txt](../common/solar_system_initializers/!!!_gotc_first_contact_initializers.txt) | 5 | Дом MSI, соседи работорговцев, родительская система Broken Shackles |
| Особые | [gotc_special_system_initializers.txt](../common/solar_system_initializers/gotc_special_system_initializers.txt) | 1 | `gotc_the_chosen_home_initializer` — дом Избранных |

### Разбор стартовых инициализаторов

18 инициализаторов делятся на четыре группы:

| Группа | Инициализаторы | Назначение |
|---|---|---|
| Особые старты | `kira_starting_system`, `neighbor_colliding_planet_first_colony` | Система Киры (настраивается событием `gotc.1` на старте игры) и соседняя колония |
| Сюзерены | `overlord_soviet_test`, `overlord_post_soviet_test` | Системы советского и постсоветского сюзерена |
| Исключения `do_not_choose_*` | `international`, `mraxist`, `pamyatnik`, `kgb`, `dumatel`, `korea`, `kadyrov`, `solovyov`, `reich`, `palestina` (10 шт.) | Системы, зарезервированные под конкретные империи и не выдаваемые случайным игрокам |
| Многосторонние происхождения | `common_ground_init_tsennosti`, `common_ground_init_vymiraty`, `hegemon_init_middle_juz`, `hegemon_init_junior_juz` | Соучредители для `origin_common_ground` (Western-European Values, Threebaltic Emortates) и вассалы для `origin_hegemon` (Средний и Младший жузы при `gotc_nursultan`) |

Группа `hegemon_init_*` напрямую связана с `gotc_nursultan` («Старший жуз»,
`origin_hegemon`): Средний и Младший жузы становятся его вассалами по происхождению.
Аналогично `common_ground_init_*` обслуживает `gotc_borrel` (`origin_common_ground`).

### Угасшие империи

[gotc_fallen_empire.txt](../common/fallen_empires/gotc_fallen_empire.txt) переопределяет
5 угасших империй: `fallen_empire_1` … `fallen_empire_4` и `fallen_machine_empire`.
Для них добавлена работа `fe_hedonist`
([gotc_fallen_empire_jobs.txt](../common/pop_jobs/gotc_fallen_empire_jobs.txt)).

Пробуждение обрабатывает namespace `fallen_empires_awakening`.

## Федерация «Европейский союз»

Мод добавляет собственный тип федерации `eu_federation`
([gotc_federation_types.txt](../common/federation_types/gotc_federation_types.txt))
с пятью перками:

| Перк | Иконка |
|---|---|
| `eu_federation_passive` | `eu_federation_passive.dds` |
| `eu_federation_bureaucratic_hell` | `eu_federation_bureaucratic_hell.dds` |
| `eu_federation_green_transition_and_sanctions` | `eu_federation_green_transition_and_sanctions.dds` |
| `eu_federation_extra_envoy` | `eu_federation_extra_envoy.dds` |
| `eu_federation_extra_influence` | `eu_federation_extra_influence.dds` |

Четыре ванильных файла законов федерации перезаписаны, чтобы учитывать новый тип:
вклад во флот, допуск вассалов, свободная миграция, раздельные договоры.
Статический модификатор `gotc_eu_federation_subsidies_bonus` даёт субсидии членам.

## Фракции котистов

Две фракции населения:

| Фракция | Файл | Строк |
|---|---|---:|
| `catist_xenophile` | [gotc_catist_xenophile.txt](../common/pop_faction_types/gotc_catist_xenophile.txt) | 1007 |
| `catist_xenophobe` | [gotc_catist_xenophobe.txt](../common/pop_faction_types/gotc_catist_xenophobe.txt) | 953 |

Обе используют триггер `is_feline_species` и общую иконку
`faction_icons_catists.dds`, объявленную в
[gotc_links_to_texture_files.gfx](../interface/gotc_links_to_texture_files.gfx)
как два спрайта: `GFX_faction_icon_catist_xenophile` и `GFX_faction_icon_catist_xenophobe`.

Случайные имена фракций — в
[gotc_pop_faction_names.txt](../common/random_names/gotc_pop_faction_names.txt).

## Черты и личности

| Объект | Тип | Файл |
|---|---|---|
| `leader_trait_tomcat_insight` | Черта лидера | [gotc_traits.txt](../common/traits/gotc_traits.txt) |
| `trait_mudozvon` | Черта вида | [gotc_traits.txt](../common/traits/gotc_traits.txt) |
| `gotc_dimon_behaviour` | ИИ-личность | [zzz_gotc_personalities.txt](../common/personalities/zzz_gotc_personalities.txt) |
| `machine_intelligence` | ИИ-личность (перезапись) | [zzz_gotc_personalities.txt](../common/personalities/zzz_gotc_personalities.txt) |
| `gov_feudal_empire` | Правительство (перезапись) | [zzz_gotc_governments.txt](../common/governments/zzz_gotc_governments.txt) |
| `preset_bulwark_kadyrov` | Пресет вассалитета | [gotc_agreement_presets.txt](../common/agreement_presets/gotc_agreement_presets.txt) |
| `imperial_vassal_ai_modifier` | Статический модификатор | [zzz_gotc_static_modifiers_overlord.txt](../common/static_modifiers/zzz_gotc_static_modifiers_overlord.txt) |

## Перезаписанные ванильные файлы

Мод несовместим с другими модами, трогающими те же файлы:

| Файл мода | Перезаписывает |
|---|---|
| `common/traits/02_species_traits_basic_characteristics.txt` | Базовые черты видов |
| `common/governments/zzz_gotc_governments.txt` | `gov_feudal_empire` |
| `common/personalities/zzz_gotc_personalities.txt` | `machine_intelligence` |
| `common/federation_laws/02, 06, 11, 12` | Законы федераций |
| `gfx/portraits/portraits/07_portraits_human.txt` | Человеческие портреты |
| `gfx/portraits/asset_selectors/new_human_male_01_hair.txt` | Причёски |
| `gfx/portraits/asset_selectors/new_human_male_clothes_01.txt` | Одежда |
| `prescripted_countries/*` (19 пустых файлов) | Все ванильные прескриптованные империи |
| `common/solar_system_initializers/marauder_initializers.txt` | Системы мародёров |
| `common/solar_system_initializers/overlord_initializers.txt` | Системы анклавов Overlord |
| `common/fallen_empires/gotc_fallen_empire.txt` | Угасшие империи |

## Требования к DLC

По содержимому мод затрагивает механики следующих DLC. Явной проверки наличия DLC
в `descriptor.mod` нет, но контент рассчитан на:

| DLC | Что задействовано |
|---|---|
| First Contact | Работорговцы, MSI, Payback, сборщики долгов, Fear of the Dark, Broken Shackles |
| Overlord | Анклавы сборщиков и Шроудходцев, квантовые катапульты, имперский вассалитет, пресеты соглашений |
| Galactic Paragons | Событие найма лидера `gotc.40000`, черта `leader_trait_tomcat_insight` |
| Ancient Relics | Раскопки `ancrel.12055` |
| Federations | Тип федерации `eu_federation`, перки, законы |
| MegaCorp | Корпоративные империи (`gotc_korea`, `gotc_solovyov`, `gotc_mason`) |
| Toxoids | `origin_toxic_knights` у `gotc_ksir` |
| Necroids | Список имён `NECROID2` у `gotc_nursultan` |
| Lithoids | Список имён `LITHOID1` у `gotc_pospolithoid` |
| Aquatics | Вторичный вид `AQUATIC1` у `gotc_borrel` |
| Machine Age | `origin_ocean_machines` у `gotc_deepseek` |
| Synthetic Dawn | Машинные разумы |
| Biogenesis | `origin_overtuned` у `gotc_roskomnadzor` |
