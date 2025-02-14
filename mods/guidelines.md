# Правила для модов

Это правила для модов, публикуемых в [индексе модов](https://geode-sdk.org/mods). **Все моды в индексе обязаны соблюдать эти правила.**

Ответственность за соблюдение модом этих правил лежит как на разработчике мода, так и на [человеке, который проверяет мод](/mods/publishing#who-can-approve-mods), чтобы убедиться, что мод соблюдает правила. Если мод был ошибочно одобрен, или он получил обновление, нарушающее правила, **он может быть изменён или одобрен в другое время**.

## Правила, влекущие бан

Мод, нарушивший любое из этих правил, будет безоговорочно отклонен из индекса, а также, весьма вероятно, приведет к полному и бессрочному запрету на публикацию в индексе и удалению всех существующих модов из индекса:

 * Мод содержит **вредоносное ПО**. Это означает любой код, целью которого является причинение вреда кому-либо или чему-либо;
 * Мод **собирает данные пользователя без согласия**. Сбор данных локально для целей статистики допустим, но любой вид сбора данных онлайн должен быть однозначно явным и давать возможность отказаться от него;
 * Мод **украден**. Это означает, что он полностью или почти полностью состоит из оригинального кода другого человека, при этом авторство явно удалено.

Пожалуйста, обратите внимание, что мод, намеренно изменяющий игровой опыт конкретных пользователей (например, делающий игровой процесс неиграбельным) и моды, преследующие конкретных людей и/или их работу, **считаются вредоносным ПО**, независимо от пользователей, если только эти пользователи лично не дали на это согласия. Эта конкретная форма вредоносного ПО вряд ли приведет к бану в рамках всего индекса и просто приведет к исключению мода из списка, хотя это зависит от серьезности ситуации.

## Другие правила

> :information_source: Вкратце: правилом для определения того, разрешено ли что-то в индексе, является **совместимость**. Если мод несовместим или может быть несовместим с другими модами, с которыми *должен* быть совместим, это обычно является основанием для отклонения.

Повторные попытки нарушить эти правила могут привести к **бану в рамках всего индекса**. Постарайтесь убедиться, что ваш мод соответствует правилам. Вы можете связаться с админами индекса, если у вас есть какие-либо вопросы относительно вашего конкретного случая.

Мод, нарушивший любое из этих правил, будет **безоговорочно отклонен** из индекса:

 * Мод содержит **ложную информацию** о том, что он делает;
 * Мод не использует предоставляемые Geode системы хуков и патчей, что почти гарантированно приводит к **несовместимости с другими модами**;
 * Мод вводит **серьезные уязвимости безопасности**, такие как RCE (удаленное выполнение кода);
 * Мод содержит **откровенный контент и/или нецензурную лексику**. Обратите внимание, что наличие нецензурной лексики в исходном коде, комментариях, именах переменных и т. д., допустимо, если она не видна конечному пользователю;
 * У мода **отсутствуют соответствующие метаданные**. Все моды в индексе должны иметь правильное название, описание, значок и теги, [включая моды-шутки](#Моды-шутки)
 * Мод **удаляет оригинальные функции** без веской причины;
 * Мод **устанавливает другие моды вне индекса Geode.**. Вам не разрешается запускать произвольный код, загруженный из Интернета. Есть два исключения из этого правила: моды, которые вводят своего рода систему скриптов, запускающую *изолированный* произвольный код, и моды, устанавливающие дополнительные платные функции в качестве библиотеки времени выполнения. Обратите внимание, что в целях проверки должен быть включен код для всех этих платных функций, включая код, используемый для их загрузки.

Мод, нарушивший любое из этих правил, скорее всего, будет отклонен, хотя в зависимости от ситуации он все еще может быть одобрен:

 * Мод без веской причины **ломает другие моды**;
 * Мод имеет несколько распространенных **ошибок, приводящих к сбоям игры** которые не были исправлены, несмотря на сообщения;
 * Мод **не делает ничего значимого**. Обратите внимание, что моды-шутки могут считаться значимыми; см. [нашу политику по ним](#joke-mods).

Мод, нарушивший любое из этих правил, скорее всего, все еще будет одобрен, хотя постоянное и/или частое нарушение может привести к отклонению:

 * Мод имеет **несколько распространенных ошибок**;
 * Мод не может нормально **сохранять состояние** между запусками (сохранение данных, загрузка данных);
 * **Кодовая база мода очень трудна для чтения**. Причина, по которой это может привести к отклонению, заключается в том, что люди, проверяющие мод для индекса, не могут должным образом установить, нарушает ли мод какие-либо другие правила из-за (надеемся, непреднамеренной) обфускации

## Что не является правилом

Это некоторые вещи, которые, как можно было бы ожидать, приведут к отклонению, но на самом деле, скорее всего, не приведут:

 * Мод **логически несовместим** с другим модом в индексе (например, два мода, которые полностью переделывают `MenuLayer` по-разному, никогда не будут совместимы);
 * Мод **выглядит плохо**.  Мы не будем вас стыдить за отсутствие навыков UI как у HJfod! Однако, если UI/UX мода не просто плох, а активно вреден, это, вероятно, нарушает правило "отсутствие ложной информации";
 * Мод **не на английском языке**. Это просто круто! Однако, нам может потребоваться некоторое время, чтобы проверить мод, исходный код которого написан на другом языке.

Также есть некоторые **шаблоны кода**, которые, как можно было бы предположить, будут отклонены, но на самом деле разрешены:

```cpp
#ifdef GEODE_IS_WINDOWS
auto editorUIGridSize = reinterpret_cast<float*>(reinterpret_cast<uintptr_t>(EditorUI::get()) + 0x1d0);
#endif
```
Доступ и изменение членов по их необработанному смещению на платформе это совершенно нормально, поскольку это не вызывает проблем совместимости с другими модами, а просто усложняет портирование вашего мода.

```cpp
if (this->querySelector("hjfod.gdshare/export-button")) {
    // GDShare загружен, режим совместимости
}
```
Проверка того, загружен ли другой мод путем поиска идентифицирующих эффектов от него в игре - это совершенно нормально, если проверки безопасны и не делают предположений о вещах, которые не были проверены. Например, просто вызова `Loader::get()->isModLoaded("hjfod.gdshare")` НЕДОСТАТОЧНО, чтобы гарантировать существование всех кнопок GDShare, поэтому всегда проверяйте сами кнопки!

## Моды, изменяющие интерфейс Geode

Некоторые моды могут захотеть **расширить интерфейс Geode**, например, чтобы добавить пользовательские функции на страницу своего мода. Это разрешено, но с некоторыми оговорками. Смотрите [страницу руководства](/tutorials/modify-geode) для получения дополнительной информации.

## Моды-шутки

Моды-шутки, то есть моды, вся функция которых заключается в том, чтобы быть смешной небольшой выходкой и ничем более, **разрешены**, при условии, что у них есть правильное название, описание, значок и теги, особенно тег `Joke`.

Однако, обратите внимание, что для того, чтобы мод был включен в Индекс, он должен быть **значимым**. То есть, это должно быть что-то, что люди могут захотеть иметь и использовать. Точное определение остается за тем, кто утверждает мод, но в целом, **если мод - это то, что вы установите один раз на пять минут, а затем удалите и никогда больше не будете использовать, это, вероятно, не значимо**. Это в основном включает моды, которые активно ухудшают игровой процесс, не добавляя новых видов удовольствия, но также могут включать визуальные изменения, настолько маленькие и ненавязчивые, что вы забываете, что они у вас установлены.

Например:

 - Мод, который просто меняет название игры на Geometry Fart и больше ничего, вероятно, недостаточно для принятия;
 - Мод, который намеренно вызывает сбой игры при каждой смерти, крайне маловероятно, что будет принят, поскольку это забавно для одного видео на YouTube, но настолько активно вредно, что никто не будет использовать его нормально;
 - Мод, который изменяет физику на супер странную, может быть пригоден для принятия, поскольку, хотя большинство пользователей не будут использовать его постоянно, они могут включать его время от времени для использования вместе с другими модами, такими как Globed;
 - Мод, который превращает значок игрока в плохо нарисованного Соника Ежа, вероятно, пригоден для принятия;
 - Мод, который представляет собой компиляцию нескольких различных переключаемых мелких шуток, абсолютно пригоден для принятия, при условии, что он не нарушает никаких других правил.

## Платные моды

Платные моды, то есть моды, для использования которых требуется оплата, **разрешены в индексе, если они имеют тег `Paid`**. Однако обратите внимание, что Geode не обрабатывает никакие платежи — вам нужно будет самостоятельно настроить всю платежную инфраструктуру, DRM и т. д.

Моды, которые можно использовать бесплатно, но которые имеют дополнительные встроенные платные функции, такие как Pro-версия или уровень поддержки, не нуждаются в теге `Paid`, если платные функции не являются необходимыми для работы мода. Например, многопользовательский мод, в котором есть платный уровень для приватных комнат, но при этом бесплатные общедоступные комнаты для всех, скорее всего, не будет нуждаться в теге.

Также разрешено публиковать **мод-установщик** для платного мода в индексе, то есть что-то, что просто просит пользователя аутентифицироваться, а затем устанавливает платный контент. Эти моды также должны иметь тег `Paid`.

## Моды, использующие генеративный ИИ

Из-за споров среди разработчиков по этому вопросу, моды, использующие **генеративный ИИ**, должны следовать этим дополнительным правилам в отношении использования ИИ:

> :information_source: Все моды, использующие ИИ, должны быть обучены на данных, полученных с согласия, и не могут использоваться для создания уровней.

 * Мод **не должен предоставлять несправедливое преимущество** в игровом процессе или чем-либо другом людям посредством использования ИИ;
 * Мод **не должен ставить под угрозу целостность создаваемого пользователем контента**. По сути, это означает, что **ни одному моду не разрешается использовать ИИ для размещения, изменения или удаления объектов**, хотя это не ограничивается только этим;
 * Модель ИИ обучена исключительно, и насколько это можно разумно ожидать, **на данных, полученных с согласия и прозрачно**. Любой мод, нарушивший это правило, будет признан нарушителем правила жесткого бана «сбора данных пользователя без согласия» и, как следствие, приведет к немедленному и постоянному бану разработчика в индексе;
 * Мод **должен явно и недвусмысленно сообщать пользователю об использовании ИИ** до того, как он нажмет на него. Это может быть так же просто, как добавление "AI" или "GPT" в название мода.

Кроме того, все моды, использующие ИИ, **должны быть проверены вручную** в индексе и **одобрены единолично ведущими разработчиками Geode**, независимо от того, подтвержден ли разработчик в индексе или нет.

## Ненавистническое поведение

Разработчики могут быть забанены в индексе модов и других связанных с Geode онлайн-пространствах, таких как сервер Discord и организация GitHub, если они совершили действия внутри *или за пределами* сообщества Geode, которые считаются ненавистными, вредными или иным образом отвратительными. **К ним относятся, но не ограничиваются:**

 * Кража или порча работ других людей;
 * Участие в непристойной деятельности с несовершеннолетними;
 * Расизм, гомофобия, трансфобия или любая другая форма нетерпимости;
 * Любая форма публичного преследования.

Это правило введено для того, чтобы Geode оставался **безопасным и гостеприимным местом для всех**. Это загрузчик модов для детской видеоигры — мы не хотим косвенно рекламировать плохих людей или их действия с его помощью!

Обратите внимание, что **приведенный выше список не является исчерпывающим или незыблемым**, и то, что квалифицируется как ненавистническое поведение, может и будет меняться со временем, при этом последнее слово всегда остается за командой Geode того времени.

Также обратите внимание, что эти правила вполне могут применяться задним числом. Хотя мы верим в то, что люди могут становиться лучше, и надеемся на это, любой человек, которого признали совершившим ненавистнические действия в прошлом, должен предоставить команде Geode основания полагать, что он действительно изменился, чтобы отменить приговор.

## Правило "Слишком большой, чтобы игнорировать"

Как и все остальное в этом мире, индекс Geode также имеет один набор правил для сверхбогатых и другой для всех остальных. Хотя это нежелательно, и мы изо всех сил стараемся быть справедливыми и равноправными, некоторые моды официально считаются "слишком большими, чтобы игнорировать", и им могут быть предоставлены небольшие исключения из правил индекса, которым должны следовать другие моды. Обратите внимание, что у нас, конечно, все еще есть жесткие ограничения; даже мод, который слишком велик, чтобы его игнорировать, не может красть данные пользователя. Кроме того, статус "слишком большой, чтобы игнорировать" обычно сам по себе подразумевает ответственность разработчика мода делать добро; поимка крупного мода на краже данных пользователя немедленно вызовет массовое возмущение. Итак, по этой причине модам, которые слишком велики, чтобы их игнорировать, могут быть предоставлены исключения в некоторых правилах, таких как отсутствие необходимости предоставлять исходный код.
