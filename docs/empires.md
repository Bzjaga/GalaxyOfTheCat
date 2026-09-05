# Империи

## Как мод заменяет империи галактики

GOTC полностью вытесняет ванильный набор прескриптованных империй в два шага:

1. **Удаление.** 19 файлов в [prescripted_countries/](../prescripted_countries/) названы
   так же, как ванильные, но имеют **нулевой размер**. Stellaris загружает их вместо
   оригиналов — все ванильные империи (включая контент DLC: Infernals, Shroud, Biogenesis,
   Grand Archive, Cosmic Storms, Machine Age, Astral Planes, First Contact, Toxoids,
   Aquatics, Necroids, Lithoids, MegaCorp, Humanoids, Synthetic Dawn, Utopia, Plantoids)
   исчезают из пула генерации.

2. **Добавление.** [gotc_prescripted_countries.txt](../prescripted_countries/gotc_prescripted_countries.txt)
   определяет 20 собственных империй.

Дополнительно [common/defines/gotc_defines.txt](../common/defines/gotc_defines.txt)
выставляет `FALLEN_CUSTOM_EMPIRE_SPAWN_CHANCE = 0`, чтобы угасшие империи всегда
генерировались логикой мода, а не из шаблонов.

## Прескриптованные империи

20 империй. Ключ — это идентификатор в файле, название — значение из английской локализации.

| # | Ключ | Название | Власть | Правительство | Происхождение | Этики |
|---:|---|---|---|---|---|---|
| 1 | `gotc_zaharova` | Ministry of OutMKADic Affairs | Олигархия | Военная хунта | `origin_imperial_vassal` | Авторитаризм, ксенофобия, милитаризм |
| 2 | `lukashenko_gotc` | Mingsk Dynasy | Диктатура | Миролюбивая диктатура | `origin_imperial_vassal` | Фанат. авторитаризм, пацифизм |
| 3 | `gotc_mao` | Zone of Resistance to Social Imperialism | Олигархия | Миролюбивая бюрократия | `origin_imperial_vassal` | Эгалитаризм, ксенофобия, пацифизм |
| 4 | `gotc_korea` | Chaebolea | Корпорация | Мегакорпорация | `origin_fear_of_the_dark` | Ксенофилия, милитаризм, материализм |
| 5 | `gotc_kadyrov` | Ichkeric Republic Chechenia | Диктатура | Бандитское королевство | `origin_default` | Ксенофобия, милитаризм, спиритуализм |
| 6 | `gotc_solovyov` | Solovyov Live | Корпорация | Мегакорпорация | `origin_shoulders_of_giants` | Авторитаризм, фанат. ксенофобия |
| 7 | `gotc_milov` | Legion of Elves | Демократия | Представительная демократия | `origin_clone_army` | Фанат. эгалитаризм, ксенофобия |
| 8 | `gotc_astrohungary` | Astro-Hungarian Empire | Имперская | Деспотическая империя | `origin_default` | Фанат. авторитаризм, ксенофилия |
| 9 | `gotc_pospolithoid` | Rzeczpospolithoida | Диктатура | Выборная монархия | `origin_galactic_doorstep` | Ксенофобия, милитаризм, спиритуализм |
| 10 | `gotc_netoropyr` | Moderate Progress Within the Bounds of the Law | Демократия | Моральная демократия | `origin_shoulders_of_giants` | Эгалитаризм, пацифизм, материализм |
| 11 | `gotc_reich` | Twenty Third Reich | Диктатура | Военная диктатура | `origin_legendary_leader` | Авторитаризм, ксенофобия, милитаризм |
| 12 | `gotc_roskomnadzor` | RosComNadzor | Диктатура | Орден чистоты | `origin_overtuned` | Фанат. ксенофобия, милитаризм |
| 13 | `gotc_deepseek` | Deep Seek | Машинный разум | Машинные исследования | `origin_ocean_machines` | Гештальт-сознание |
| 14 | `gotc_borrel` | European Garden | Машинный разум | Машина-опекун | `origin_common_ground` | Гештальт-сознание |
| 15 | `gotc_voldemar` | Post-Soviet Wasteland | Олигархия | Теократическая олигархия | `origin_post_apocalyptic` | Авторитаризм, ксенофобия, спиритуализм |
| 16 | `gotc_ussr_citizens` | United Slavic Strength of Rus | Имперская | Теократическая монархия | `origin_scion` | Авторитаризм, ксенофобия, спиритуализм |
| 17 | `gotc_mason` | Masonic lodge | Корпорация | Криминальный синдикат | `origin_scion` | Ксенофилия, фанат. материализм |
| 18 | `gotc_nursultan` | The Senior jüz | Диктатура | Военная диктатура | `origin_hegemon` | Фанат. авторитаризм, милитаризм |
| 19 | `gotc_2ch` | 4chan | Олигархия | Бандитская коммуна | `origin_clone_army` | Ксенофобия, фанат. милитаризм |
| 20 | `gotc_ksir` | Islamic Revolutionary Guard Corps | Диктатура | Оборонительный союз | `origin_toxic_knights` | Милитаризм, фанат. спиритуализм |

### Заметки по составу

- **Имперский вассалитет.** Три империи (`gotc_zaharova`, `lukashenko_gotc`, `gotc_mao`)
  стартуют с `origin_imperial_vassal`. Их сюзерены создаются скриптовыми эффектами
  в [gotc_effects.txt](../common/scripted_effects/gotc_effects.txt) — советский или
  постсоветский оверлорд, выбор зависит от логики эффекта
  `change_empires_if_overlord_soviet` / `change_empires_if_overlord_post_soviet`.
- **Scion.** `gotc_ussr_citizens` и `gotc_mason` используют `origin_scion` — их патрон
  задаётся событиями `origin.*` из [!!!_gotc_origin_events_1.txt](../events/!!!_gotc_origin_events_1.txt).
- **Машинные разумы.** `gotc_deepseek` и `gotc_borrel` — гештальты. `gotc_borrel`
  дополнительно имеет вторичный вид (`origin_common_ground` требует соучредителей).
- **Авторские списки имён** используют 4 империи: `gotc_kadyrov` (`GOTC_TAJICAUCASIAN`),
  `gotc_ussr_citizens` (`GOTC_RUS`), `gotc_mason` (`GOTC_JEW`). Остальные берут ванильные
  списки (`HUMAN1`, `HUMAN2`, `HUM1`, `ART1`, `MAM4`, `MOL4`, `LITHOID1`, `NECROID2`,
  `MACHINE3`, `AQUATIC1`).
- Списки `GOTC_CAT` и `GOTC_BABULKA` не привязаны к прескриптованным империям —
  они используются другими механиками мода.

## Локализованные названия

Файл [gotc_empires_l_english.yml](../localisation/english/gotc_empires_l_english.yml)
содержит 557 ключей и покрывает больше сущностей, чем 20 прескриптованных империй —
часть названий предназначена для стран, создаваемых событиями и скриптовыми эффектами.

Полный список названий империй в локализации (36 записей `*_EMPIRE_NAME`):

| Ключ локализации | Название |
|---|---|
| `GOTC_KOREA_EMPIRE_NAME` | Chaebolea |
| `GOTC_KOREA_EMPIRE_NAME_2` | DPRK |
| `GOTC_ZAHAROVA_EMPIRE_NAME` | Ministry of OutMKADic Affairs |
| `GOTC_LUKASHENKO_EMPIRE_NAME` | Mingsk Dynasy |
| `GOTC_DUGIN_EMPIRE_NAME` | Post-Soviet Russian Empire |
| `GOTC_WAGNER_EMPIRE_NAME` | Wagner Group |
| `GOTC_KADYROV_EMPIRE_NAME` | Ichkeric Republic Chechenia |
| `GOTC_ROSCOSMOS_EMPIRE_NAME` | RosCosmos |
| `GOTC_SOLOVYOV_EMPIRE_NAME` | Solovyov Live |
| `GOTC_RPC_EMPIRE_NAME` | World Russian Orthodox Council |
| `GOTC_MIZULINA_EMPIRE_NAME` | Safe Internet League |
| `GOTC_MAO_EMPIRE_NAME` | Zone of Resistance to Social Imperialism |
| `GOTC_MILOV_EMPIRE_NAME` | Legion of Elves |
| `GOTC_POSPOLITHOID_EMPIRE_NAME` | Rzeczpospolithoida |
| `GOTC_NETOROPYR_EMPIRE_NAME` | Moderate Progress Within the Bounds of the Law |
| `GOTC_REICH_EMPIRE_NAME` | Twenty Third Reich |
| `GOTC_KSIR_EMPIRE_NAME` | Islamic Revolutionary Guard Corps |
| `GOTC_ROSCOMNADZOR_EMPIRE_NAME` | RosComNadzor |
| `GOTC_DEEPSEEK_EMPIRE_NAME` | Deep Seek |
| `GOTC_BORREL_EMPIRE_NAME` | European Garden |
| `GOTC_TSENNOSTI_EMPIRE_NAME` | Western-European Values |
| `GOTC_VYMIRATY_EMPIRE_NAME` | Threebaltic Emortates |
| `GOTC_VOLDEMAR_EMPIRE_NAME` | Post-Soviet Wasteland |
| `GOTC_USSR_CITIZENS_EMPIRE_NAME` | United Slavic Strength of Rus |
| `GOTC_MASON_EMPIRE_NAME` | Masonic lodge |
| `GOTC_NURSULTAN_EMPIRE_NAME` | The Senior jüz |
| `GOTC_2CH_EMPIRE_NAME` | 4chan |
| `GOTC_ASTRAHAN_EMPIRE_NAME` | Astra-Khanate |
| `GOTC_HOPLITHES_EMPIRE_NAME` | Confederation of Goplithses |
| `GOTC_MYRMEKSHATRII_EMPIRE_NAME` | Sumit of Myrmekshatriya |
| `GOTC_MIDII_EMPIRE_NAME` | Musseles Kingdom |
| `GOTC_LIZARD_EMPIRE_NAME` | Reptilian Conspiracy |
| `GOTC_RUS_EMPIRE_NAME` | Rus' |
| `GOTC_HAB_EMPIRE_NAME` | Astro-Hungarian Empire |
| `GOTC_CAREBEAR_EMPIRE_NAME` | Care Bears |
| `GOTC_QIN_EMPIRE_NAME` | Qin Dynasty |
| `GOTC_GATES_EMPIRE_NAME` | Microsoft Corporation |

У части империй есть альтернативные названия с суффиксом `_2` — например, Chaebolea /
DPRK у `gotc_korea`. Они переключаются событиями по ходу игры.

## Набор ключей на одну империю

Для каждой империи локализация определяет типовой набор:

```
GOTC_<KEY>_EMPIRE_NAME          — название империи
GOTC_<KEY>_EMPIRE_ADJECTIVE     — прилагательное
GOTC_<KEY>_SHIP_PREFIX          — префикс кораблей
GOTC_<KEY>_MAIN_SPECIES_NAME    — вид (ед. ч.)
GOTC_<KEY>_MAIN_SPECIES_PLURAL  — вид (мн. ч.)
GOTC_<KEY>_MAIN_SPECIES_ADJECTIVE
GOTC_<KEY>_SYSTEM_NAME          — родная система
GOTC_<KEY>_PLANET_NAME          — родная планета
GOTC_<KEY>_RULER_NAME           — имя правителя
GOTC_<KEY>_RULER_TITLE          — титул правителя
GOTC_<KEY>_RULER_TITLE_FEMALE   — женский титул
GOTC_<KEY>_HEIR_TITLE           — титул наследника
GOTC_<KEY>_HEIR_TITLE_FEMALE
```

Все ключи продублированы в русской локализации
[gotc_empires_l_russian.yml](../localisation/russian/gotc_empires_l_russian.yml)
с тем же числом записей (557).
