# Состав репозитория

Полная карта репозитория Galaxy of the Cat. Файлы сгруппированы по каталогам,
для каждого указано назначение и объём.

## Корень

| Файл | Строк | Назначение |
|---|---:|---|
| [descriptor.mod](../descriptor.mod) | 9 | Манифест мода: версия 0.25, поддержка Stellaris 4.4.1, Workshop ID 3118932220, теги Events / Galaxy Generation |
| [README.md](../README.md) | 11 | Описание мода на английском и русском |
| `thumbnail.png` | — | Обложка мода в Steam Workshop (413 КБ) |

---

## `common/` — игровая логика

20 подкаталогов, самая объёмная часть мода.

### `common/scripted_effects/` — переиспользуемые эффекты

Ядро мода: почти все сложные операции по созданию стран, флотов и станций вынесены сюда.

| Файл | Строк | Эффектов | Назначение |
|---|---:|---:|---|
| [gotc_effects.txt](../common/scripted_effects/gotc_effects.txt) | 8175 | 67 | Крупнейший файл репозитория. Создание анклавов Шроудходцев, имперских оверлордов и вассалов (International, Mraxist, Pamyatnik, RKKA, Tuva, Stakhanov), советских и постсоветских сюзеренов |
| [zzz_gotc_first_contact_dlc_effects.txt](../common/scripted_effects/zzz_gotc_first_contact_dlc_effects.txt) | 1369 | 11 | Контент First Contact: работорговцы, MSI, сборщики долгов, Payback, «Страх темноты» |
| [zzz_gotc_pre_ftl_scripted_effects.txt](../common/scripted_effects/zzz_gotc_pre_ftl_scripted_effects.txt) | 2547 | 2 | Рандомизаторы преразумных видов и их родных миров |
| [zzz_gotc_start_of_game_effects.txt](../common/scripted_effects/zzz_gotc_start_of_game_effects.txt) | 269 | 1 | `imperial_origin_start_effect` — стартовая настройка имперского происхождения |
| [zzz_gotc_scripted_effects.txt](../common/scripted_effects/zzz_gotc_scripted_effects.txt) | 44 | 1 | `create_zombie_pop_group` |

### `common/solar_system_initializers/` — генерация систем

| Файл | Строк | Инициализаторов | Назначение |
|---|---:|---:|---|
| [gotc_fallen_empire_initializers.txt](../common/solar_system_initializers/gotc_fallen_empire_initializers.txt) | 4418 | 25 | Системы угасших империй и их колоний |
| [marauder_initializers.txt](../common/solar_system_initializers/marauder_initializers.txt) | 3035 | 9 | Три анклава мародёров по три системы |
| [overlord_initializers.txt](../common/solar_system_initializers/overlord_initializers.txt) | 2944 | 18 | Анклавы сборщиков, Шроудходцев, квантовые катапульты (DLC Overlord) |
| [gotc_starting_initializers.txt](../common/solar_system_initializers/gotc_starting_initializers.txt) | 2489 | 18 | Стартовые системы, включая систему Киры и системы вассалов |
| [gotc_pre_ftl_initializers.txt](../common/solar_system_initializers/gotc_pre_ftl_initializers.txt) | 878 | 10 | Префтл-цивилизации: Египет, Сирия, Антиохия, Франция, Аравия, Уганда, Филистия, Иордания и др. |
| [!!!_gotc_first_contact_initializers.txt](../common/solar_system_initializers/!!!_gotc_first_contact_initializers.txt) | 764 | 5 | Системы MSI, работорговцев и Broken Shackles |
| [gotc_special_system_initializers.txt](../common/solar_system_initializers/gotc_special_system_initializers.txt) | 380 | 1 | `gotc_the_chosen_home_initializer` — дом Избранных |

### `common/prescripted_flags/`, `governments/`, `personalities/`, `traits/`

| Файл | Строк | Назначение |
|---|---:|---|
| [gotc_empire_flags.txt](../common/prescripted_flags/gotc_empire_flags.txt) | 59 | Флаги стран, помечающие прескриптованные империи для событий |
| [zzz_gotc_governments.txt](../common/governments/zzz_gotc_governments.txt) | 22 | Переопределение `gov_feudal_empire` |
| [zzz_gotc_personalities.txt](../common/personalities/zzz_gotc_personalities.txt) | 119 | ИИ-личности: `gotc_dimon_behaviour`, переопределение `machine_intelligence` |
| [gotc_traits.txt](../common/traits/gotc_traits.txt) | 149 | Черта лидера `leader_trait_tomcat_insight`, черта вида `trait_mudozvon` |
| [02_species_traits_basic_characteristics.txt](../common/traits/02_species_traits_basic_characteristics.txt) | 1072 | Перезапись ванильного файла базовых черт видов |

### `common/scripted_triggers/`

| Файл | Строк | Назначение |
|---|---:|---|
| [gotc_scripted_triggers.txt](../common/scripted_triggers/gotc_scripted_triggers.txt) | 12 | `is_feline_species` — проверка на кошачий вид |

### `common/federation_*` — федерации

Мод добавляет собственный тип федерации — «Европейский союз».

| Файл | Строк | Назначение |
|---|---:|---|
| [federation_types/gotc_federation_types.txt](../common/federation_types/gotc_federation_types.txt) | 317 | Тип федерации `eu_federation` |
| [federation_perks/gotc_perks.txt](../common/federation_perks/gotc_perks.txt) | 71 | 5 перков: passive, bureaucratic_hell, green_transition_and_sanctions, extra_envoy, extra_influence |
| [federation_laws/02_fleet_contribution.txt](../common/federation_laws/02_fleet_contribution.txt) | 1982 | Перезапись законов о вкладе во флот |
| [federation_laws/06_allow_subjects_to_join.txt](../common/federation_laws/06_allow_subjects_to_join.txt) | 113 | Допуск вассалов в федерацию |
| [federation_laws/11_free_migration.txt](../common/federation_laws/11_free_migration.txt) | 102 | Свободная миграция |
| [federation_laws/12_separate_treaties.txt](../common/federation_laws/12_separate_treaties.txt) | 119 | Раздельные договоры |

Все четыре файла законов — перезаписи ванильных: они добавляют условия для `eu_federation`.

### `common/fallen_empires/`, `pop_jobs/`

| Файл | Строк | Назначение |
|---|---:|---|
| [gotc_fallen_empire.txt](../common/fallen_empires/gotc_fallen_empire.txt) | 687 | 5 угасших империй: `fallen_empire_1`…`_4` и `fallen_machine_empire` |
| [gotc_fallen_empire_jobs.txt](../common/pop_jobs/gotc_fallen_empire_jobs.txt) | 66 | Работа `fe_hedonist` для угасших империй |

### `common/pop_faction_types/`, `random_names/`

| Файл | Строк | Назначение |
|---|---:|---|
| [gotc_catist_xenophile.txt](../common/pop_faction_types/gotc_catist_xenophile.txt) | 1007 | Фракция «котисты-ксенофилы» |
| [gotc_catist_xenophobe.txt](../common/pop_faction_types/gotc_catist_xenophobe.txt) | 953 | Фракция «котисты-ксенофобы» |
| [gotc_pop_faction_names.txt](../common/random_names/gotc_pop_faction_names.txt) | 65 | Случайные имена для фракций |

### `common/static_modifiers/`, `agreement_presets/`, `defines/`

| Файл | Строк | Назначение |
|---|---:|---|
| [gotc_static_modifiers.txt](../common/static_modifiers/gotc_static_modifiers.txt) | 12 | `gotc_eu_federation_subsidies_bonus` — субсидии ЕС |
| [zzz_gotc_static_modifiers_overlord.txt](../common/static_modifiers/zzz_gotc_static_modifiers_overlord.txt) | 8 | `imperial_vassal_ai_modifier` |
| [gotc_agreement_presets.txt](../common/agreement_presets/gotc_agreement_presets.txt) | 80 | Пресет вассалитета `preset_bulwark_kadyrov` |
| [gotc_defines.txt](../common/defines/gotc_defines.txt) | 5 | `FALLEN_CUSTOM_EMPIRE_SPAWN_CHANCE = 0` — угасшие империи всегда генерируются модом, а не из шаблонов |

### `common/on_actions/`

| Файл | Строк | Назначение |
|---|---:|---|
| [gotc_on_actions.txt](../common/on_actions/gotc_on_actions.txt) | 51 | Привязка событий мода к игровым хукам |

Подключённые хуки:

| Хук | События | Когда срабатывает |
|---|---|---|
| `on_game_start` | `gotc.1` | Старт игры — система Киры |
| `on_five_year_pulse_country` | `gotc.41234`, `gotc.40000` | Раз в 5 лет — известные лидеры, найм лидеров (Galactic Paragons) |
| `on_colonized` | `gotc.10` | Колонизация планеты |
| `on_colony_transfer` | `gotc.11` | Смена владельца планеты |
| `on_colony_conquer` | `gotc.11` | Захват планеты (дополнительно к transfer) |
| `on_system_gained` | `gotc.12` | Переход системы к новому владельцу |

### `common/name_lists/` — списки имён

5 авторских списков имён. Каждый содержит имена кораблей по классам, названия классов
кораблей, флотов, армий и имена персонажей.

| Файл | Строк | Тематика |
|---|---:|---|
| [GOTC_CAT.txt](../common/name_lists/GOTC_CAT.txt) | 297 | Кошачья |
| [GOTC_JEW.txt](../common/name_lists/GOTC_JEW.txt) | 273 | Еврейская |
| [GOTC_TAJICAUCASIAN.txt](../common/name_lists/GOTC_TAJICAUCASIAN.txt) | 261 | Таджикско-кавказская |
| [GOTC_RUS.txt](../common/name_lists/GOTC_RUS.txt) | 261 | Русская |
| [GOTC_BABULKA.txt](../common/name_lists/GOTC_BABULKA.txt) | 261 | «Бабулькина» |

---

## `events/` — события

6 файлов, 60 событий. Файлы с префиксом `!!!_` загружаются первыми.

| Файл | Строк | Событий | Namespace | Назначение |
|---|---:|---:|---|---|
| [!!!_gotc_marauder_events.txt](../events/!!!_gotc_marauder_events.txt) | 4957 | 22 | `marauder` | Дипломатия и поведение мародёров |
| [!!!_gotc_origin_events_1.txt](../events/!!!_gotc_origin_events_1.txt) | 2353 | 7 | `origin` | События происхождений, в т.ч. Scion |
| [!!!_gotc_events.txt](../events/!!!_gotc_events.txt) | 1911 | 25 | `gotc` | Основные события мода, привязанные к `on_actions` |
| [!!!_gotc_origin_events_3.txt](../events/!!!_gotc_origin_events_3.txt) | 305 | 4 | `origin` | События происхождений, ветка сюзерена |
| [!!!_gotc_fallen_empire_awakening_events.txt](../events/!!!_gotc_fallen_empire_awakening_events.txt) | 222 | 1 | `fallen_empires_awakening` | Пробуждение угасших империй |
| [!!!_gotc_ancient_relics_arcsite_events_2.txt](../events/!!!_gotc_ancient_relics_arcsite_events_2.txt) | 54 | 1 | `ancrel` | Раскопки Ancient Relics |

---

## `prescripted_countries/` — прескриптованные империи

Ключевой каталог мода. Работает в два шага.

**Шаг 1 — удаление ванильных империй.** 19 файлов с ванильными именами имеют нулевой
размер. Stellaris загружает их вместо оригиналов, и все ванильные прескриптованные
империи исчезают из галактики:

```
00_top_countries.txt              86_cosmic_storms_prescripted_countries.txt
82_infernals_prescripted_empires  87_machine_age_prescripted_countries.txt
83_shroud_prescripted_countries   88_astral_planes_prescripted_countries.txt
84_biogenesis_prescripted_...     89_first_contact_prescripted_countries.txt
85_grand_archive_prescripted_...  90_toxoids … 99_prescripted_countries.txt
```

**Шаг 2 — добавление своих.** [gotc_prescripted_countries.txt](../prescripted_countries/gotc_prescripted_countries.txt)
(2841 строка) определяет 20 империй. Подробности — в [empires.md](empires.md).

---

## `localisation/` — тексты

Полная двуязычная локализация: english и russian. Структура каталогов зеркальна,
файлы и число ключей совпадают один в один.

| Файл (в каждом языке) | Ключей | Содержание |
|---|---:|---|
| `gotc_empires_l_<lang>.yml` | 557 | Названия империй, видов, планет, систем, титулы правителей |
| `gotc_l_<lang>.yml` | 204 / 210 | Общие тексты: события, черты, фракции, федерация |
| `gotc_marauder_l_<lang>.yml` | 54 | Тексты событий мародёров |
| `name_lists/name_list_GOTC_JEW_l_<lang>.yml` | 424 | Имена еврейского списка |
| `name_lists/name_list_GOTC_RUS_l_<lang>.yml` | 388 | Имена русского списка |
| `name_lists/name_list_GOTC_TAJICAUCASIAN_l_<lang>.yml` | 373 | Имена таджикско-кавказского списка |
| `name_lists/name_list_GOTC_CAT_l_<lang>.yml` | 350 | Имена кошачьего списка |
| `name_lists/name_list_GOTC_BABULKA_l_<lang>.yml` | 312 | Имена «бабулькиного» списка |

Русский `gotc_l_russian.yml` содержит на 6 ключей больше английского — расхождение
стоит проверить при следующей правке локализации.

---

## `gfx/` и `interface/` — графика

### Иконки (`gfx/interface/`)

| Файл | Назначение |
|---|---|
| `federation/eu_federation_bg.dds` | Фон федерации ЕС |
| `icons/faction_icons/faction_icons_catists.dds` | Иконка фракций котистов |
| `icons/traits/leader_trait_icons/tomcat_insight.dds` | Иконка черты лидера |
| `icons/message/message_leader_recruitment_mad_vacuum_cleaner.dds` | Иконка сообщения о найме лидера |
| `icons/federation/federation_perks/eu_federation_*.dds` | 6 иконок перков федерации ЕС |

### Портреты (`gfx/portraits/`)

| Файл | Строк | Назначение |
|---|---:|---|
| [asset_selectors/new_human_male_01_hair.txt](../gfx/portraits/asset_selectors/new_human_male_01_hair.txt) | 928 | Перезапись селектора причёсок |
| [asset_selectors/new_human_male_clothes_01.txt](../gfx/portraits/asset_selectors/new_human_male_clothes_01.txt) | 58 | Перезапись селектора одежды |
| [portraits/07_portraits_human.txt](../gfx/portraits/portraits/07_portraits_human.txt) | 534 | Перезапись человеческих портретов |

### `interface/`

| Файл | Назначение |
|---|---|
| [gotc_links_to_texture_files.gfx](../interface/gotc_links_to_texture_files.gfx) | Объявление 4 спрайтов: черта лидера, сообщение о найме, две иконки фракций котистов |

---

## Сводка по объёму

| Раздел | Файлов | Строк |
|---|---:|---:|
| `common/` | 38 | ~40 800 |
| `events/` | 6 | 9 802 |
| `prescripted_countries/` | 20 | 2 841 |
| `localisation/` | 16 | ~5 900 |
| `gfx/` + `interface/` | 15 | ~1 540 |
| Корень | 3 | 20 |
| **Итого** | **98** | **~55 500** |
