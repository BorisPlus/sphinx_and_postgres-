# PostgreSQL и Sphinx

Согласно

* https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-sphinx-on-ubuntu-16-04
* http://sphinxsearch.com/docs/sphinx3.html
* https://blog-programmista.ru/post/19-sphinx-ustanovka-i-nastrojka.html

## 

```shell
sudo apt-get install sphinxsearch

psql -h 192.168.102.99 -p 11111 --user root
Пароль пользователя root: 
psql (11.11 (Debian 11.11-0+deb10u1), сервер 13.2 (Debian 13.2-1.pgdg100+1))
ПРЕДУПРЕЖДЕНИЕ: psql имеет базовую версию 11, а сервер - 13.
                Часть функций psql может не работать.
Введите "help", чтобы получить справку.

root=# 
```

```postgres-psql

-- DROP SCHEMA library CASCADE;

CREATE SCHEMA library
    AUTHORIZATION root;

-- DROP TABLE library.documents;

CREATE TABLE library.documents
(
    id bigserial NOT NULL,
    income_datetime timestamp with time zone NOT NULL DEFAULT now(),
    content text COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT documents_pkey PRIMARY KEY (id)
)
TABLESPACE pg_default;

ALTER TABLE library.documents
    OWNER TO root;
```

```postgres-sql

SET search_path TO collection;
INSERT INTO library.documents(content)
VALUES
    ('Путь к сердцу мужчины лежит через путь к желудку женщины.'),
    ('В вопросах стиля плыви по течению; в вопросах принципа стой твердо, как скала.'),
    ('В наше время, чтение книги — это маленькая революция. Чтение создаёт умных людей, а умный человек — это всегда угроза для общества.'),
    ('Скажи отцу, чтоб впредь предохранялся…'),
    ('Смотрю, ты слова плохо понимаешь? Сейчас попробую объяснить на пальцах — ты мой средний палец хорошо видишь?'),
    ('Когда кто-то идет не в ногу, не спеши осуждать его: возможно он слышит звук другого марша. (Генри Торо)'),
    ('Если тебе говорят «пошли», то необязательно пошлить, достаточно просто послать.'),
    ('В любом из нас спит гений. И с каждым днем все крепче.'),
    ('Тише едешь — меньше должен.'),
    ('Хочется верить, что будет хотеться и дальше.'),
    ('Я намерен жить вечно — пока всё идет нормально.'),
    ('Да ничего, ничего, я на Вас не обижаюсь. У меня еще и сосед дебил…'),
    ('Знание некоторых принципов легко компенсирует незнание некоторых фактов.'),
    ('Тебе пришла в голову мысль? Наверное, чтобы умереть там окончательно.'),
    ('Контрольное изнасилование в голову.'),
    ('Извините, что я говорю, когда вы перебиваете.'),
    ('Человек меньше всего похож на себя, когда говорит от своего имени. Дайте ему маску, и он расскажет всю правду. (Оскар Уайлд)'),
    ('Чтобы не переутомиться, спать надо восемь часов в день, и ещё столько же ночью.'),
    ('В каждую погоду благо дать.'),
    ('Все ответы находятся в тебе. Ты знаешь больше, чем написано в книгах. Но чтобы вспомнить это — нужно читать книги, слушать себя и доверять себе.'),
    ('Оптимисты изобретают самолеты, а пессимисты – парашюты.'),
    ('Один в поле — а вони…'),
    ('Девушка, давайте скрепим нашу дружбу половым актом.'),
    ('Заройся в мох и плюйся клюквой…'),
    ('Быть честным хочется… Но меньше, чем богатым.'),
    ('Все мы произносим слова и фразы, которые люди понимают совсем не так, как нам хотелось бы.'),
    ('Ты уже позвонил своему психотерапевту?'),
    ('Как много девушек хороших, мечтают в тайне о плохом.'),
    ('Если чувствуешь, что это твоё, не слушай тех, кто будет отговаривать. (Макс Шупбах)'),
    ('В мире есть только один человек, способный потянуть тебя на дно или вытянуть на верх — это ты сам. (А. Кадочников)'),
    ('Мечтаю стать бумерангом. Тебя кидают, а ты им — обратно, в морду.'),
    ('Ты что, потеряла список кого бояться надо? Тебе напомнить?'),
    ('Если тебе лизнули зад, не расслабляйся — это смазка!'),
    ('Многие еще живы только потому, что убийство уголовно наказуемо.'),
    ('Если окружающие считают тебя странным, возможно это не твоя проблема!'),
    ('Все думают только о себе! Лишь я думаю только обо мне.Дедушка Бабай и Вафай'),
    ('Главное — верить в себя. Мнение окружающих меняется ежедневно.'),
    ('Девушка, вы такая фешенебельная, что мне не рентабельно.'),
    ('Настоящий интеллигент никогда не скажет — «как была дура-дурой, так ею и осталась», он скажет — «время над ней не властно».'),
    ('У меня есть один недостаток: я не умею общаться с дураками.'),
    ('А у меня… кажется, нет характера…- Заведи. Вещь — полезная… (М. Горький «На дне»)'),
    ('После общения с некоторыми людьми у меня появляется ярко выраженный комплекс полноценности.'),
    ('Любишь кататься — катись к чертовой матери'),
    ('Я знал, что она такая, но не знал, что настолько.'),
    ('Я в сотый раз убеждаюсь, что кроме высшего образования нужно иметь хотя бы среднюю сообразительность.'),
    ('Как бы так себя похвалить, чтобы самому тошно не стало?'),
    ('Единственный человек, с которым ты должен сравнивать себя, это ты в прошлом. И единственный человек, лучше которого ты должен быть, это ты.'),
    ('Никогда не рассказывайте о себе ни хорошего, ни плохого. В первом случае вам не поверят, а во втором — приукрасят.'),
    ('Видеть в море одну лишь массу воды — значит совсем не видеть моря. (Виктор Гюго)'),
    ('Думаю, мне хватит самого лучшего.'),
    ('Люди, неспособные мотивировать себя, должны довольствоваться посредственностью, независимо от того, насколько выразительны их прочие таланты. (Эндрю Карнеги)'),
    ('Если вы чего-то не понимаете, спросите меня и нас станет двое.'),
    ('Помните выпуск Ералаш, когда мальчик никак не мог рассказать возлюбленной о своих чувствах и попросил друга.'),
    ('Чтоб оно вам поперек горла встало, когда какать пойдете.'),
    ('Если у тебя совсем нет яиц, тебе нужен тот, у кого их два.'),
    ('Почему ты всегда носишь черное? — «Потому что я всегда готов к твоим похоронам».'),
    ('В здоровом теле — здоровый стул…'),
    ('Упавший духом гибнет раньше срока.'),
    ('Отказ от удовольствий в пользу обязанностей действует на психику разрушающе.'),
    ('Гляжу на тебя и понимаю — у Бога хорошее чувство юмора.'),
    ('Ничего на свете лучше нету, чем скрипеть кроватью до рассвета.'),
    ('Ни стыда. Ни совести. Ничего лишнего.'),
    ('Не бойтесь потерять тех, кто не побоялся потерять вас.'),
    ('Тебе пошли бы искорки из глаз.'),
    ('Готовые слезы указывают на хитрость, а не на печаль. (Публилий Сир)'),
    ('Если вы не можете объяснить пятилетнему ребенку свою мысль, значит, вы сами ее не очень-то понимаете. (Альберт Эйнштейн)'),
    ('Разумный человек гонится за тем, что избавляет его от страданий, а не за тем, что приятно. (Аристотель)'),
    ('И когда количество твоих слов перейдет в качество?'),
    ('Девушка, что вы на меня смотрите, как будто у вас родители на дачу уехали.'),
    ('Хорошего человека и обидеть приятно.'),
    ('Дураки — не мамонты, сами не вымрут…'),
    ('Не хлопай по спине — крылья сломаешь.'),
    ('А у тебя харя не треснет по диагонали зигзагом?!'),
    ('Хотелось бы верить, что будет хотеться и дальше.Кошки закапывают'),
    ('Кораблю безопасней в порту, но он не для этого строился. (Грейс Хоппер)'),
    ('Самооценку снизь, не соответствуешь.'),
    ('А вам приходилось снимать обручальное кольцо, не вынимая руки из кармана?'),
    ('Твои глаза похожи на двух призывников. Один косит, второй реально голубой'),
    ('На кого шуршишь, пакетик?'),
    ('Я Вам всем очень благодарен, но хотел бы попробовать поработать в'),
    ('Когда будете делать ход — убедитесь, что он правильный.'),
    ('Золотое правило девушки: не знаешь, что сказать — улыбнись и поправь лифчик.'),
    ('Спрашивать «быть или не быть» или не спрашивать?'),
    ('Ничего не понял, питекантроп социально неадаптированный?'),
    ('Тебя и в мыслях даже не имел.'),
    ('Только о двух вещах мы будем жалеть на смертном одре — что мало любили и мало путешествовали. (Марк Твен)'),
    ('Может найдем общий язык? — «Разумеется, мы найдем общий язык, если вы прикусите свой».'),
    ('У тебя айкью как у хлебушка, ниже плинтуса.'),
    ('Прикольно двигаешь ртом. А-а-а… Это ты так говоришь.'),
    ('Чего греха таить, коль вы согласны.'),
    ('Да покарает тебя стоматолог!'),
    ('Не принимай никакой негатив. Пока ты его не примешь, он принадлежит тому, кто его принес. (Будда)'),
    ('Вы мне напоминаете меня во младенчестве — тоже норовите всё обоср*ть.'),
    ('Самый подходящий момент наступает в самое неподходящее время.'),
    ('Девушка, вы верите в любовь с первым встречным?'),
    ('Если вы хотите узнать недостатки девушки, похвалите её перед подругами.'),
    ('Завтра — одно из самых опасных слов на свете. Парализует волю похлеще иного заклинания, склоняет к бездействию, в зародыше уничтожает планы и идеи.'),
    ('Умение прощать — свойство сильных. Слабые никогда не прощают. (Махатма Ганди)'),
    ('Как было бы замечательно, если бы и женские киски тоже мяукали, когда проголодаются.'),
    ('Острая интеллектуальная недостаточность.'),
    ('Воскребота — Ночь с субботы на воскресенье.'),
    ('Если не знаешь, что хочешь, получишь, что останется.'),
    ('В мире есть еще множество грабель, на которые не ступала нога человека. (Станислав Ежи Лец)'),
    ('Ах, он меня лишил иммунитета…'),
    ('Влюбленные — это двое, которые любят себя при помощи друг друга.'),
    ('Каждый человек по-своему прав, а по-моему нет.'),
    ('Сокращайте речь до смысла, чтобы понятнее было.'),
    ('Умный мужчина — это так сексуально!'),
    ('Глядя на тебя, мне остается только порадоваться за себя.'),
    ('Ты сейчас нахамить пытался или просто использовал длинные слова, смысл которых тебе не понятен?'),
    ('Мы становимся похожими на тех людей, с которыми общаемся. Выбирайте свое окружение – какими мы не были бы уникальными, оно все равно влияет на нас.'),
    ('У меня силы столько, что могу очком лом перекусить.'),
    ('Напилась — веди себя доступно.Люди без фантазии'),
    ('И никакая это не сентенция, просто мы не хотим, чтобы вас когда-нибудь настигли депривация и фру.'),
    ('Я ведь почему такой злой был? — Потому что у меня велосипед был без сиденья.'),
    ('ИДИОТ — идеальный друг и отличный товарищ.'),
    ('Спроси у меня в долг, и я тебе посочувствую.'),
    ('Будете проходить мимо — проходите мимо.'),
    ('Капля долбит камень не силою, а часто падая. (Джордано Бруно)'),
    ('Ничто так не бодрит с утра, как незамеченный дверной косяк.'),
    ('Ничто так сильно не разрушает человека, как продолжительное бездействие. (Аристотель)'),
    ('Женщины часто думают, почему они не думали, когда надо было думать.'),
    ('Один из способов решить проблему — пообещать решить её завтра.'),
    ('Кто рано встаёт — тот всех достаёт.'),
    ('Пока в твоей жизни не найдется места для человека, который был бы для тебя не менее важен, чем ты сам, ты всегда будешь одинок. (Ричард Бах «Мост через вечность»)'),
    ('Тому, что действительно нужно знать, никто не научит. (Оскар Уайльд)'),
    ('Мы всё отлично понимаем, но это нам нисколько не мешает.'),
    ('С точки зрения геометрической прогрессии, если посмотреть сверху, то снизу покажется, что сбоку ничего не видно.'),
    ('Если весь мир — дерьмо, считай, что все мы — мухи.'),
    ('Широта моей души не знает пределов вашей благодарности.'),
    ('Хочешь сделать лучше всех — сделай сам.'),
    ('Не рассказывай о том, что задумал: не бывает успеха у замысла, что открыт другому.'),
    ('Перед сильным не кланяйся, перед трудностями не сгибайся.'),
    ('У тебя родители не физики? А то выглядишь как неудавшийся научный эксперимент.'),
    ('Настоящий мужчина никогда не поднимет на женщину руку, потому что у настоящего мужчины поднимается совсем не рука…'),
    ('Я бы тебя сильно обидел. Но, вижу, ты и так жизнью обижен.'),
    ('Давайте перейдем на «ты», а то мне по морде вам дать не ловко.'),
    ('У тебя, милок, острая интеллектуальная недостаточность.'),
    ('Не стоит бояться перемен. Чаще всего они случаются именно в тот момент, когда они необходимы. (Конфуций)'),
    ('Иди-ка ты к жене с таким букетом!'),
    ('Подозревать хуже, чем знать. У реальности есть границы, у воображения — нет.'),
    ('Цену состояния узнают тогда, когда его приобрели, а цену друга; когда его потеряли.'),
    ('Привычка находить во всем только смешную сторону — самый верный признак мелкой души, ибо смешное лежит на поверхности. (Аристотель)'),
    ('Я мог бы сделать лучше, но мне помогали.'),
    ('Если бы я согласился с вами, мы оба были бы неправы.'),
    ('Не бойся совершенства — ты никогда его не достигнешь! (Сальвадор Дали)'),
    ('БАР — Библиотека Алкогольного Раритета.'),
    ('Как же ты меркантилен, мой друг. Запомни: всё, что можно купить за деньги — уже дёшево. (Д. Б. Шоу)'),
    ('Никто еще не заблудился, следуя своему внутреннему голосу. (Генри Дэвид Торо)'),
    ('Девушки, играя в поддавки, вы быстрее попадете в дамки.'),
    ('Дорогая, что за фигня? — Встаю ночью, хочу в раковину пописать, а посуда не вымыта.'),
    ('Треунгаляционная симпелляция деструбных гентронов ротора турбулентности дивергенции — элементарнейшая вещь.Плохо слышат'),
    ('Чем старше и мудрее человек, тем меньше ему хочется выяснять отношения. Хочется просто встать, пожелать удачи и уйти.'),
    ('Не люблю я любить девушек, которые любят не любить меня.'),
    ('Я уверен: книгу ничто не заменит в будущем, так же как ничто не могло заменить её в прошлом.'),
    ('Основная причина совершаемых человеком ошибок кроется в постоянной борьбе чувств с разумом. (Блез Паскаль «Мысли»)'),
    ('Не важно как ваши дела сейчас — держать себя и выглядеть нужно словно тот, кем вы хотите быть.'),
    ('Я не тормоз — я просто плавно мыслю.'),
    ('Всякого рода грубость тает, словно на огне, под влиянием ежедневного чтения хороших книг. (Виктор Мари Гюго)'),
    ('Не будите во мне зверя — он и так не высыпается.'),
    ('Армейская дисциплина тяжела, но это тяжесть щита, а не ярма.'),
    ('В жизни всегда есть место подвигу, но некоторые всё же предпочитают оставаться холостыми…'),
    ('Тебе за себя не стыдно?'),
    ('Сейчас очки в два кармана положишь!'),
    ('Будучи искушаем комарами, впал в грех сквернословия.'),
    ('Век бы на тебя смотрел — сквозь оптический прицел…'),
    ('Кто много спрашивает — тому много врут.'),
    ('Тебя, наверное, на спор зачали.'),
    ('Чтобы найти у женщины пупок, нужно поставить указательный палец ей на затылок и медленно опускать вниз. Третья дырка — это пупок.'),
    ('Как же много в мире безмозглых мудрецов!'),
    ('У меня такое неприятное чувство, что вы правы.'),
    ('Я оказался здесь, благодаря квантовому прыжку.'),
    ('Кроме высшего образования надо иметь хотя бы среднюю сообразительность.'),
    ('Я не знаю, как должно быть, но вы делаете неправильно.'),
    ('В чём разница между «Нравится» и «Люблю»? Когда вам нравится цветок, вы его срываете. Но если вы любите цветок, вы ежедневно его поливаете.'),
    ('Никогда не живи с человеком — ради денег, детей и жалости. Деньги пресытятся, дети вырастут, а жалость превратится в гнев!'),
    ('Ну, теперь ты довольна, милая?» — «Да, теперь я довольно милая».'),
    ('Я всё отдам, но где мне это взять?'),
    ('В такую погоду только тещу за пивом гонять.'),
    ('Ты мне напоминаешь меня в двухлетнем возрасте — тоже норовишь всё обо$рать.'),
    ('Асфальта бояться — вообще не ходить.'),
    ('По тебе хор калифорнийских геев плачет…'),
    ('У каждого свой рецепт для счастья. У меня на потолке написано: завтра бросаю жрать. Каждое утро, просыпаясь, вижу эту надпись и думаю: хорошо, что завтра, а не сегодня.'),
    ('Счастливый актер — это мёртвый актер, потому что только после смерти нельзя измениться. После смерти я, наверное, буду кисточкой.'),
    ('Ты тянешь лишь на секс-петарду…'),
    ('Зачем мечтать о чем-то высоком, когда самое приятное снизу.'),
    ('Нам не дано предугадать, кому и где придется дать.'),
    ('Счастья вам и здоровья в личной жизни.'),
    ('Судьба — очень удобное слово для тех, кто никогда не принимает решений. (Джоди Фостер)Получить имеем'),
    ('Чужого нам не надо, но свое мы возьмем, чье бы оно ни было.'),
    ('Вы, слава богу, уходите или, не дай бог, остаетесь?'),
    ('Захочешь — найдешь время, не захочешь — найдешь причину. (Бернард Шоу)'),
    ('Некоторые люди наглеют, если их ежедневно кормить.'),
    ('Никогда не спрашивайте человека, за что он вас любит: стоит ему над этим задуматься, как может оказаться, что любить вас не за что.'),
    ('Мне кажется, что у некоторых людей голова — это лишь декоративное приложение к заднице.'),
    ('Если останавливаться всякий раз, когда тебя оскорбляют или в тебя плюются, то ты никогда не дойдёшь до места, куда тебе надо попасть.'),
    ('Забей на то, что думают другие люди — и жить станет легче.'),
    ('Сегодня утром по зеркалу такие ужасы показывали.'),
    ('Когда совсем падете духом, приходите ко мне в больницу. Один обход ракового отделения в два счета лечит от любой хандры. (Ремарк «Земля обетованная»)'),
    ('Не хочешь заняться спасением природы? У меня есть знакомый хирург, он может тебя стерилизовать.'),
    ('Чем чаще женщину мы это, тем реже женщина того.'),
    ('Бегу и волосы назад — Отказ сделать что-нибудь в грубой форме'),
    ('Пусть мир — дерьмо. Считай, что все мы — мухи.'),
    ('Всей своей жизнью Пушкин учит нас тому, что талантливому человеку нужно сначала научиться стрелять.'),
    ('Береги родину — отдыхай за границей.'),
    ('Да, красотой мир вы не спасёте…'),
    ('То, что сжимают, — расширяется. То, что ослабляют, — укрепляется. То, что уничтожают, — расцветает. Кто хочет отнять что-нибудь у другого, непременно потеряет свое. (Лао Цзы)'),
    ('Трусливый друг страшнее врага, ибо врага опасаешься, а на друга надеешься.'),
    ('Мозгами шевелил — перемешались.'),
    ('Пруха есть — ума не надо.'),
    ('Еще один звук с своей платформы и твой зубной состав тронется!'),
    ('Порядочность — это когда потом чувствуешь себя идиотом.'),
    ('Обуздывать надо бурю, а не жалкий сквозняк.'),
    ('Лучше раз в полгода думать о женитьбе, чем раз в неделю о разводе.'),
    ('Я пришел к тебе с приветом рассказать, что солнце встало и на двадцать сантиметров приподняло одеяло.'),
    ('Лучше сделать один раз вовремя, чем два раза правильно.'),
    ('Вы должны изучать правила игры. И тогда вы будете играть лучше, чем кто либо еще. (Альберт Эйнштейн)'),
    ('Всесторонне недоразвитая личность.'),
    ('Я не поправился — от гордости распёрло.'),
    ('Я — человек доверчивый, но труднообманываемый.'),
    ('БИЧ — бывший интеллигентный человек.'),
    ('Будь как дома, но в холодильник не лазь.'),
    ('Гора не кажется неприступной, если смотреть с ее вершины.'),
    ('Сегодня я благобухаю.'),
    ('Береги брюки сзади, а юбку — спереди.прикольные умные выражения'),
    ('Мужчины очень хотят знать, о чем думают женщины, а когда узнают — не хотят верить в это.'),
    ('Существовать ради самого себя значит быть ничем. (Беррес Фредерик Скиннер)'),
    ('Юмор, по сути, — это лекарство от боли. И мы используем его как пластырь. Если человек умеет шутить, то вся его жизнь становится проще и лучше.'),
    ('Разуй айзы — смотри внимательно.'),
    ('Леонардо ты недовинченный!'),
    ('Никто не запрещает тебе считать себя царем горы, но прошу, знай свою гору.'),
    ('Курить буду, но пить НЕ брошу!'),
    ('Как жаль, что ты наконец-то уходишь.'),
    ('Противник, вскрывающий ваши ошибки, полезнее для вас, чем друг, желающий их скрыть. (Леонардо да Винчи)'),
    ('Человек страдает не столько от того, что происходит, сколько от того, как он оценивает то, что с ним происходит. (Мишель де Монтень)'),
    ('Я хочу тебя! Спроси меня как.'),
    ('Вам пришла в голову мысль?! Умирать пришла?'),
    ('Остановите время, мне нужно починить часы.'),
    ('Тобой в детстве бабайку не пугали?'),
    ('Женщины — они такие же как и мы, только приятней на ощупь.'),
    ('Вы называете свою цену, а я называю свою. Потом мы оба смеемся и приступаем к серьезному разговору.'),
    ('Чего ты такой тихий? — «Почему я такая тихоня? Никто не планирует убийства громко».'),
    ('Только дураки повторяют свои ошибки. Умные совершают новые.'),
    ('Знаете, есть такая пословица: «Тот, кто упорствует в своем безумии, в один прекрасный день окажется мудрецом».'),
    ('И где же тот добрый волшебник, который вам смелость дал?'),
    ('Таких, как ты, не будет. И не надо.'),
    ('Я люблю, когда женщина берет инициативу в свои руки, но еще больше, когда женщина берет инициативу в рот.'),
    ('Мы сами придумываем себе проблемы, преграды, комплексы и рамки. Освободи себя, вдохни жизнь и пойми, что ты можешь все.'),
    ('Ногти на ногах не стриги — обещали гололед.'),
    ('Слушай, да ты совсем нервный стал! Тебе это… успокоиться надо. Может тебе съездить куда-нибудь?… В челюсть, например…'),
    ('Сила не в том, что ты скажешь, а в том, что сделаешь.'),
    ('При общении с людьми важно правильно использовать умные слова и понимать их значение.'),
    ('Чем интересней вопрос, тем очевидней, что задавать его нельзя. (Кингсли Эмис)'),
    ('К своему стыду мне никогда не стыдно.'),
    ('Как трудно быть порядочной свиньёй…'),
    ('Семьдесят процентов хитрости лисиц приходится на тупость куриц.'),
    ('Если бы я понимал все шутки, я бы давно умер от смеха.'),
    ('Не называй чужие вещи своими именами!'),
    ('Источник любви скорее в нас, нежели в любимом существе (Андре Моруа)'),
    ('Молчание не всегда доказывает присутствие ума, но всегда доказывает отсутствие глупости.'),
    ('Алкоголь приносит радость и горе. Радость мнимую, горе настоящее. (Александр Мельников)Про кексы с мозгами'),
    ('Жениться интересно только по любви; жениться же на девушке.'),
    ('Ну что сказать: спасибо, что не позже.'),
    ('Если тебе случится рассердиться на кого бы то ни было, рассердись в то же время на самого себя, хотя бы за то, что сумел рассердиться на другого. (Николай Васильевич Гоголь)'),
    ('Если ты чувствуешь, что достоин, то ты это получишь!'),
    ('Бодливой корове бог быка не дает.'),
    ('Не будь на словах тем, кем не можешь быть на поступках.'),
    ('А вы в детстве были симпатичной или как сейчас?'),
    ('Хочешь возглавить колонну людей, идущих на …? А чё так? Ты бы прекрасно смотрелся в роли лидера.'),
    ('Жизнь прекрасна, если не вспоминать прошлое и не думать о будущем.'),
    ('При таком характере ты могла бы быть и покрасивее.'),
    ('Если красивых и умных одновременно не бывает, то значит я не существую?'),
    ('Природа больше мной не повторится.'),
    ('Ну что ж вернемся к нашим баранам… и возглавим стадо.'),
    ('С твоим лицом регистрироваться в ВК нельзя. Используй лучше фото своей бабушки.'),
    ('Думаю, не ошибусь, если промолчу.'),
    ('Как хотите, но таково мое мнение, а если оно вам не нравится, то у меня есть другое.'),
    ('Ночь. Город засыпает. Просыпаются сидящие на диете и идут к холодильнику.'),
    ('Клятвы дают те, кто кроме клятв ничем другим удержать не может. (Дмитрий Гринберг)'),
    ('У женщины есть три пути сделать карьеру: два спереди и один сзади.'),
    ('Не иди позади меня — возможно, я не поведу тебя. Не иди впереди меня — возможно, я не последую за тобой. Иди рядом, и мы будем одним целым. (Индийская мудрость)'),
    ('Внутри каждого яблока находится огрызок.'),
    ('Доброта и нежность — это не признак слабости и бессилия, а проявление силы и решимости.'),
    ('Не подражайте другим. Найдите себя и оставайтесь собой, ведь «зависть — это невежество», а «подражание — самоубийство». (Дейл Карнеги)'),
    ('Нет величия там, где нет простоты, добра и правды. (Л. Толстой)'),
    ('Не говорите мне, что у вас всё хорошо — мне от этого плохо.'),
    ('Я не такой дурак, как ты выглядишь.'),
    ('Главное не эффект, а эффективность в действиях.'),
    ('Чтобы избегать ошибок, надо набираться опыта; чтобы набираться опыта, надо делать ошибки. (Лоуренс Питер)'),
    ('И нет величия там, где нет простоты, добра и правды.'),
    ('Родился ты назло презервативу.'),
    ('В основном, свободу человек проявляет только в выборе зависимости. (Герман Гессе)'),
    ('Тупость и грубость — синонимы тебя.'),
    ('Часто люди гордятся чистотой своей совести только потому, что они обладают короткой памятью.'),
    ('Влюбленную женщину легко заставить делать всё, что ей хочется.'),
    ('Если ты выглядишь, как свинья, то это не значит, что нужно вести себя соответственно.'),
    ('А кое-кто жалеет… Где ты, Кое?'),
    ('Ты из принципа игнорируешь здравый смысл или у тебя к нему личная неприязнь?'),
    ('Иногда самое лучшее высказывание — молчание. А самый лучший для себя совет — свой. (Мемуары гейши)'),
    ('Ой, извини. Кажется, середина моего предложения перебивает начало твоего.'),
    ('Ваши мысли настолько гениальны, что санитары уже приехали!'),
    ('Истинная щедрость по отношению к будущему — это всё посвятить настоящему. (Альбер Камю)'),
    ('Забудьте о существовании слова «если». Оно делает нас слабыми, заставляя думать о других возможностях. (Пауло Коэльо)'),
    ('Назови меня наглецом и ляг со мной в постель.'),
    ('Не существует безвыходных ситуаций, лишних людей, случайных встреч и потерянного времени. (Валерио Альбисетти)'),
    ('Я не смеюсь над теми, над кем Бог уже поугарал.'),
    ('Да, ваша голова нуждается в прополке…'),
    ('Истинное величие начинается с понимания собственного ничтожества. (Гете)'),
    ('Есть женщины в русских селеньях, их бабами нежно зовут. Коня на скаку остановят и хобот ему оторвут.'),
    ('Обделался легким испугом.'),
    ('Если нельзя возразить, то лучше и не слушать.'),
    ('Не можете убедить — сбейте с толку.'),
    ('По факту исчезновения мужа возбуждено два соседа.'),
    ('Я думал, я ошибся, но я ошибся.Собрание мыслей'),
    ('Все люди такие разные, и только я один такой одинаковый.'),
    ('Жена — это та, единственная и неповторимая вредная привычка, которая может бросить тебя сама!'),
    ('Умные слова для общения нужно знать, чтобы не прослыть невеждой, если твой собеседник вставляет их через раз.'),
    ('Хотели как лучше, а вспотели как всегда.'),
    ('В гавани корабль в безопасности, но предназначение корабля совсем не в этом. (Джон Шедд)'),
    ('Красивые и модные умные слова для разговора и общения про любовь: в стихах и прозе.'),
    ('Кто не знает, куда направляется, очень удивляется, попав не туда.'),
    ('Лучший способ испортить удовольствие — превратить его в привычку.'),
    ('Спи быстрей — подушка нужна.'),
    ('Будь проще, и микробиологи к тебе потянутся.'),
    ('В жизни все временно. Так что, если все идет хорошо, наслаждайся – вечно это не продлится. А если все идет плохо – не переживай, это тоже не продлится вечно.'),
    ('Как идиот вы были безупречны.'),
    ('В такую грудь Амур не промахнется.'),
    ('Любовь — ответ на проблему человеческого существования. (Эрих Фромм)'),
    ('Чем дольше ты держишь всё в себе, копишь и прогибаешься, тем сильнее будет «взрыв», когда ты дойдешь до своей точки кипения.'),
    ('На каждое ваше «увы» есть наше «зато».'),
    ('Я что-то пропустил? — «Да, одну ступень эволюции».'),
    ('Когда разговариваешь с очень умным, чувствуешь себя тупым. А когда разговариваешь с тупым, чувствуешь, как тупеешь.'),
    ('Они есть повсюду — эти странные люди, которые не знают, что вчера — это вчера, и которые каждое утро просыпаются с прошлогодними мыслями в голове. (Генри Форд)'),
    ('Раньше я говорил: » Я надеюсь, что все изменится.» Затем я понял, что существует единственный способ, чтобы все изменилось-измениться мне самому. (Джим Рон)'),
    ('Нет хорошего — есть то, что нравится тебе. (Слова Ванталы)'),
    ('Ты и вправду веришь, что подобные реплики поднимают тебя в глазах окружающих?'),
    ('Лучше — один раз вовремя, чем — два раза неправильно.'),
    ('Вам ответить как: вежливо или честно?'),
    ('Что-что, а это я умею — тактично приказывать.'),
    ('«У Вас есть сигарета?» — «Есть, спасибо».'),
    ('Почему твой язык работает быстрее мозга?'),
    ('Там, где кончается терпение, начинается выносливость.'),
    ('Вот так, шутка за шутку, ежик и получил по морде.'),
    ('Если ты не такой как все, тебя сложнее использовать.'),
    ('Научившись компетентно и искусно вести диалог, можно добиться многих благ как в личной жизни, так и в карьере.'),
    ('В нашей деревне всего два развлечения, и обе уже спят.'),
    ('Я не зеркало, чтобы тебя пугать.'),
    ('Принимайте всё, когда оно приходит к вам, наслаждайтесь всем, пока оно длится, отпускайте всё, когда оно должно уйти. (Нисаргадатта Махарадж)'),
    ('Умные люди тоже наступают на грабли, но только для того, чтобы поднять их с земли не нагибаясь.'),
    ('Если хотите душевного покоя, бросьте искать недостатки в других. Научитесь принимать каждого, как «своего». Никто вам не чужой, весь мир – ваш.'),
    ('Рот свой у стоматолога открывать будешь!'),
    ('Некоторым женщинам изнасилование следует расценивать как комплимент.'),
    ('Скажите, вам помочь или не мешать?Умные мысли в голову'),
    ('В книге «Кто есть кто» тебя следует искать в главе «Что Это»?'),
    ('Остынь и приляг. Желательно на рельсы.'),
    ('Если что-то в вашей жизни причиняет вам страдания, бегите от этого, дорогие мои, со всех ног и побыстрей. (Анна Гавальда)'),
    ('Для чего действительно нужна смелость, так это для искренности (Майкл Джексон)'),
    ('Открывать рот будешь, когда я расстегну ширинку.'),
    ('Иду чувствую сквозняк… а вы тут оказывается воздух пинаете.'),
    ('Твои в лесу грибы и шишки (на заявление — это МОЕ).'),
    ('Единственное мое желание — чтобы исполнялось всё, что я хочу.'),
    ('Пессимист видит трудности при каждой возможности. Оптимист видит возможности в каждой трудности.'),
    ('Почему в сказке про трёх поросят дунул волк, а крышу снесло поросятам?'),
    ('О, как морозно в январе, Когда удобства во дворе!…'),
    ('Оставшись с носом, стал совсем несносен!'),
    ('Теперь всё утро недолюбленным ходить.'),
    ('Когда говоришь, что думаешь — думай, что говоришь.'),
    ('Скромных людей не бывает. Просто некоторым нечем хвастаться.'),
    ('Курение убивает. А если вы убиты, то теряете важную часть своей жизни.'),
    ('Замысел без умысла называется вымыслом.'),
    ('А твоя сиделка знает, что ты здесь?'),
    ('Одна пара губ, — чтобы наговорить кучу обидных вещей. И еще две пары, — чтобы попросить за это прощения.'),
    ('Если сейчас же не заткнешься, будешь деснами улыбаться.'),
    ('Тебе что шапка на голове мозоль натёрла?'),
    ('Нас рано, нас рано мама разбудила. С раками, с раками суп она сварила.'),
    ('Хочешь завтрак в постель — спи на кухне.'),
    ('Будьте мягкими. Не позволяйте миру сделать вас жесткими. Не позволяйте боли заставить вас ненавидеть. Не позволяйте горечи украсть вашу сладость. (Курт Воннегут)'),
    ('Ты часом не Баран по гороскопу?'),
    ('О свой скромности я могу говорить часами.'),
    ('Как два байта переслать.'),
    ('Лучше ни черта не делать, чем делать черти что.'),
    ('Что тебе мешает понять это? Лишние хромосомы?'),
    ('У каждого из нас есть только одно истинное призвание — найти путь к самому себе. (Герман Гессе)'),
    ('Если ты идешь навстречу, значит, нам не по пути.'),
    ('Ученье — свет, а неученых — тьма…'),
    ('Ищешь проблему? Я к твоим услугам!'),
    ('Есть три ловушки, которые воруют радость и мир: сожаление о прошлом, тревога за будущее и неблагодарность за настоящее.'),
    ('Сегодняшний день еще вчера не заладился.'),
    ('Ты снова упустил прекрасный шанс промолчать.'),
    ('Я верю в силу человеческой личности, но ты, видно, не личность.'),
    ('Для такого мнения у вас зубов должно быть в два раза больше.'),
    ('Если бы жизнь не прощала ошибок, мало кто доживал бы до пяти лет.'),
    ('Виски — Вот Иностранцы Срань Какую Изобрели…'),
    ('Всё самое лучшее случается неожиданно.'),
    ('Главная жизненная задача человека — дать жизнь самому себе. (Эрих Фромм)'),
    ('Что с памятью? — «Я вам не Википедия, чтобы всё помнить».'),
    ('Одна боль всегда уменьшает другую. Наступите вы на хвост кошке, у которой болят зубы, и ей станет легче.'),
    ('Я без понтов понтовый, а ты с понтами беспонтовый!Цели реальные'),
    ('Баранов на шашлык не приглашают.'),
    ('В конце концов, среди концов найдешь конец ты наконец.'),
    ('Если бы мне нравилось общаться с суками, я бы завёл собаку.'),
    ('Первое впечатление от человека — самое верное, так как он еще не знает, что от вас скрывать. (Константин Мелихан)'),
    ('Ты такой умный — тебе череп не жмет?'),
    ('А с поцелуями торопиться не будем, — сказал принц, слезая со спящей красавицы.'),
    ('Я не видел ничего потому, что слишком пристально смотрел. (Сёрен Кьеркегор)'),
    ('Толку мне тебя посылать. Ты и так бываешь там чаще, чем на улице.'),
    ('Ведь кто-то должен тратить Ваши деньги…'),
    ('Девушка, прикройте колени — и вам теплее будет, и я дрожать перестану.'),
    ('И про старуху бывает порнуха.'),
    ('Люди судят о вещах и событиях в соответствии с тем, что имеют в себе сами. (Преподобный Паисий Святогорец)'),
    ('Тебе следует пойти в зоопарк, там тебя примут за своего.'),
    ('Творчество состоит в том, чтобы позволить себе совершить ошибки. Искусство — в том, чтобы знать, в каких из них упорствовать'),
    ('Если бы люди никогда не делали глупостей, то не свершилось бы ничего и умного. (Людвиг Витгенштейн)'),
    ('Эй, ты, выкидыш беременной селёдки. Ещё одно горбатое слово и будешь всё жизнь двигаться рывками.'),
    ('Чем бы дитя не тешилось, лишь бы соску на пипку не натягивало.'),
    ('Бог его обидел и поступил совершенно правильно.'),
    ('Время лечит, но за деньги получается намного быстрее.'),
    ('Настоящая красота живёт в сердце, отражается в глазах и проявляется в поступках. (Ошо)'),
    ('Не столько запах плох, насколько чувства наши совершенны.'),
    ('За что ни возьмусь — везде приятно!')

```

```shell
sudo nano /etc/sphinxsearch/sphinx.conf
```

```shell
# Sphinx configuration file sample

source library
{
	type			= pgsql

	sql_host		= 192.168.102.99
	sql_user		= root
	sql_pass		= secret
	sql_db			= collection
	sql_port		= 11111

	sql_query		= \
		SELECT id, content \
		FROM library.documents
}

index content_idx
{
	source			= library
	path			= /var/lib/sphinxsearch/data/content_idx

	docinfo			= extern
	dict			= keywords
	mlock			= 0

	morphology		= stem_ru

	min_word_len		= 1

	# prefix_fields		= filename
	# infix_fields		= url, domain

	html_strip		= 0
	# html_index_attrs	= img=alt,title; a=title;
	# html_remove_elements	= style, script
}

index rt
{
	type			= rt
	path			= /var/lib/sphinxsearch/data/rt
	# rt_mem_limit		= 512M
	rt_field		= content
}

indexer
{
	mem_limit		= 128M
}

searchd
{
	listen			= 127.0.0.1:9312:sphinx
	listen			= 127.0.0.1:9306:mysql41
	log			    = /var/log/sphinxsearch/searchd.log
	query_log		= /var/log/sphinxsearch/query.log
	read_timeout		= 5
	client_timeout		= 300
	max_children		= 30
	persistent_connections_limit	= 30
	pid_file		    = /var/run/sphinxsearch/searchd.pid
	seamless_rotate		= 1
	preopen_indexes		= 1
	unlink_old		    = 1
	mva_updates_pool	= 1M
	max_packet_size		= 8M
	max_filters		    = 256
	max_filter_values	= 4096
	max_batch_queries	= 32
	workers			= threads # for RT to work
}

common
{
}
```

```
crontab
@hourly /usr/bin/indexer --rotate --config /etc/sphinxsearch/sphinx.conf --all
 ```

```
sudo sed -i 's/START=no/START=yes/g' /etc/default/sphinxsearch
sudo systemctl restart sphinxsearch.service
sudo systemctl status sphinxsearch.service
nano collection
mysql -h127.0.0.1 -P9306

 
```

```mysql-sql

SELECT * FROM content_idx WHERE MATCH('голова'); SHOW META;

+------+
| id   |
+------+
|   14 |
|   15 |
|  195 |
|  237 |
|  307 |
|  333 |
|  353 |
|  374 |
+------+
8 rows in set (0.001 sec)

+---------------+------------+
| Variable_name | Value      |
+---------------+------------+
| total         | 8          |
| total_found   | 8          |
| time          | 0.000      |
| keyword[0]    | голов      |
| docs[0]       | 8          |
| hits[0]       | 8          |
+---------------+------------+
6 rows in set (0.000 sec)

CALL KEYWORDS ('голова мысль идея', 'content_idx', 1);
+------+--------------+------------+------+------+
| qpos | tokenized    | normalized | docs | hits |
+------+--------------+------------+------+------+
| 1    | голова       | голов      | 8    | 8    |
| 2    | мысль        | мысл       | 10   | 10   |
| 3    | идея         | иде        | 0    | 0    |
+------+--------------+------------+------+------+
3 rows in set (0.000 sec)

```

На заметку: netstat -tulpn | grep LISTEN

### О грустном

Для поиска фраз необходимо учитывать особенности формообразования слов русского языка.
Так, фраза в БД "Курение убивает..." по ключу "курение убъет" найдена не будет, так как 
Sphinx не выделяет корень так, как надо.

```mysql-sql
SELECT * FROM content_idx WHERE MATCH('курение убъет'); SHOW META;
Empty set (0.001 sec)

+---------------+------------+
| Variable_name | Value      |
+---------------+------------+
| total         | 0          |
| total_found   | 0          |
| time          | 0.000      |
| keyword[0]    | курен      |
| docs[0]       | 1          |
| hits[0]       | 1          |
| keyword[1]    | убъет      |
| docs[1]       | 0          |
| hits[1]       | 0          |
+---------------+------------+
9 rows in set (0.000 sec)

```

## API

```shell
python2 -m pip install sphinx
```

```python
# coding: utf-8
# This is api.py
from pprint import pprint
import sphinxsearch

client = sphinxsearch.SphinxClient()
client.SetServer('localhost', 9312)
result = client.Query(r'голова')

pprint(result)
```

```shell
python2 ./api.py
```

```
{'attrs': [],
 'error': '',
 'fields': ['content'],
 'matches': [{'attrs': {}, 'id': 14, 'weight': 1},
             {'attrs': {}, 'id': 15, 'weight': 1},
             {'attrs': {}, 'id': 195, 'weight': 1},
             {'attrs': {}, 'id': 237, 'weight': 1},
             {'attrs': {}, 'id': 307, 'weight': 1},
             {'attrs': {}, 'id': 333, 'weight': 1},
             {'attrs': {}, 'id': 353, 'weight': 1},
             {'attrs': {}, 'id': 374, 'weight': 1}],
 'status': 0,
 'time': '0.000',
 'total': 8,
 'total_found': 8,
 'warning': '',
 'words': [{'docs': 8,
            'hits': 8,
            'word': '\xd0\xb3\xd0\xbe\xd0\xbb\xd0\xbe\xd0\xb2'}]}
```

### О грустном в API

Итак:
* в консоль выпало кодированное `\xd0\xb3\xd0\xbe\xd0\xbb\xd0\xbe\xd0\xb2`, что там будет при работе - пока не понятно, 
  но уже напрягает этот момент;
* необходимо указывать дерективу кодировки файла, иначе
```
python2 ./api.py 

SyntaxError: Non-ASCII character '\xd0' in file ./api.py on line 7, 
but no encoding declared; see http://python.org/dev/peps/pep-0263/ for details
```
* под python3 не работает

```shell
python3 -m pip install sphinx
python3 ./api.py 
Traceback (most recent call last):
  File "./api.py", line 4, in <module>
    import sphinxsearch
  File "/home/developer/.local/lib/python3.8/site-packages/sphinxsearch/__init__.py", line 75
    SPH_ATTR_MULTI                      = 0X40000000L
```