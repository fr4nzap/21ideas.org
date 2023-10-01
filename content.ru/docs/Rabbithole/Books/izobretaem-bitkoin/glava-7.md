---
title: "Глава 7: Учетные записи, не идентифицирующие личность"
tags: ["книга", "новичкам", "основы"]
description: "Теперь давайте разберемся с идентификацией. В традиционной банковской системе вы отправляете деньги, раскрывая свою личность перед банком."
url: izobretaem-bitkoin/glava-7
bookFlatSection: false
bookToc: true
weight: 8
---

{{< expand "Оглавление" "..." >}}

[Главная страница](/izobretaem-bitkoin)

[Вступление](/izobretaem-bitkoin/vstuplenie)  

[Глава 1: Что такое Биткоин](/izobretaem-bitkoin/glava-1)

[Глава 2: Отказываемся от посредника](/izobretaem-bitkoin/glava-2)

[Глава 3: Proof of Work](/izobretaem-bitkoin/glava-3)

[Глава 4: Майнинг](/izobretaem-bitkoin/glava-4)

[Глава 5: Обеспечение безопасности реестра](/izobretaem-bitkoin/glava-5)

[Глава 6: Форки и атаки 51%](/izobretaem-bitkoin/glava-6)

[Глава 7: Учетные записи, не идентифицирующие личность](/izobretaem-bitkoin/glava-7)

[Глава 8: Кто устанавливает правила?](/izobretaem-bitkoin/glava-8)

[Глава 9: Что дальше?](/izobretaem-bitkoin/glava-9)

{{< /expand >}}

# Глава 7: Учетные записи, не идентифицирующие личность

Мы создали распределенный реестр, не зависящий от центрального органа, систему лотереи майнинга для выбора тех, кто производит записи в систему, систему вознаграждения честных майнеров и наказания недобросовестных, способ корректировки сложности майнинга для обеспечения согласованного графика выпуска и уменьшения количества конфликтов, а также систему проверки достоверности цепочки путем рассмотрения совокупного Proof of Work и истории транзакций.

Теперь давайте разберемся с идентификацией. В традиционной банковской системе вы отправляете деньги, раскрывая свою личность перед банком. Вы предоставляете документ, удостоверяющий личность, пин-код в банкомате или вводите имя пользователя и пароль в приложении. Банк гарантирует, что два человека не могут быть идентифицированы как одна и та же личность.

Поскольку у нас сейчас нет центрального органа, который бы проводил идентификацию личности, как нам открывать счета в нашей новой финансовой системе на основе Биткоина? Как нам решить задачу Сатоши по разрыву связи между личными данными и финансовыми операциями, чтобы избежать кражи личных данных и не быть вынужденными доверять нашу информацию центральным органам? Как нам гарантировать, что, когда Элис объявит, что хочет заплатить Бобу, что это действительно она и что она имеет право перевести эти средства?

# Создание Биткоин-аккаунта

Мы не можем полагаться на центральный орган, такой как банк, для ведения учета всех счетов. А что, если мы позволим каждому регистрировать собственные имя пользователя и пароль? Банк обычно проверяет, что имя пользователя еще не используется, но здесь это невозможно, поскольку у нас нет центрального органа, выдающего удостоверения личности. Нам нужно что-то больше, сильнее и уникальнее, чем имя пользователя и пароль. Эта техника знакома нам из предыдущих глав. Нам снова нужно гигантское случайное число.

Для создания учетных записей мы можем использовать тот же прием, который предоставил возможность каждому участнику становиться обладателем лотерейных билетов, генерируя огромные случайные числа,. Чтобы создать Биткоин-аккаунт, также известный как _адрес_, мы сгенерируем пару 256-битных чисел с математической связью, известную как связка _публичного и приватного_ ключей. Не забывайте, что 256-битное число примерно равно числу атомов во Вселенной. Поэтому вероятность того, что два человека случайно сгенерируют одну и ту же пару ключей, практически отсутствует. Мы будем давать наш публичный ключ (адрес) любому, кто хочет отправить нам монеты. А приватный ключ мы будем использовать, чтобы их тратить. Вот как это работает.

Шифрование — это метод сбора и сокрытия некоторых данных, так что только тот, у кого есть приватный ключ, может прочитать исходное сообщение, расшифровав его. В детстве некоторые из нас играли с простыми игрушками для кодирования/декодирования, которые использовали ключ, чтобы превратить сообщение в бессмыслицу, а затем обратно в исходное сообщение. Этот вид шифрования, использующий только один ключ,  называется симметричным. Система, в которой используется связка публичного и приватного ключей, асимметрична, поскольку вы шифруете данные одним ключом, а расшифровываете другим.

Вы можете поделиться своим публичным ключом со всем миром. Люди, которые хотят отправлять вам сообщения, могут зашифровать их с помощью вашего публичного ключа. А поскольку только у вас есть приватный ключ, вы единственный, кто может их расшифровать.

Давайте рассмотрим, как Элис отправляет монеты Бобу. Чтобы провести сделку, Боб генерирует пару ключей. Свой приватный ключ он хранит в секрете/сохраняет в тайне. А на основе хеша его публичного ключа, Боб создает Биткоин-адрес — большое число, которым он делится с Элис.

Вы можете думать об адресе в сети Биткоин как о почтовом ящике. Вместо писем Элис может бросать в этот почтовый ящик монеты. Но только у Боба есть приватный ключ, который открывает почтовый ящик, чтобы тратить монеты.

Когда вы переводите деньги в банк, вы даете ему свое имя пользователя и пароль. Когда вы выписываете чек, вы подписываетесь своим именем, чтобы подтвердить, что именно вы выписываете чек. Когда вы перемещаете биткоины, вы подтверждаете, что владеете ключом к адресу, на котором хранятся монеты.

Элис должна доказать, что у нее есть приватный ключ, связанный с адресом, на котором хранятся монеты, но она не хочет раскрывать свой приватный ключ никому, иначе его смогут украсть и потратить средства из ее почтового ящика.

Доказательство владения ключом Элис называется цифровой подписью. Элис создает транзакцию, которая по сути представляет собой фрагмент данных, который выглядит примерно так:

Адрес 12345, содержащий 2,5 биткоина, отправляет 2 биткоина на адрес 56789 и 0,5 биткоина обратно на адрес 12345 [^1].

Затем она шифрует данную транзакцию с помощью своего приватного ключа и создает уникальную _цифровую подпись_.

Когда Элис сообщает о своей транзакции другим нодам в сети, она делится информацией о публичном ключе почтового ящика, с которого она отправляет транзакцию, и зашифрованной приватным ключом подписью. Элис объявляет следующее:

• Я отправляю монеты с адреса 12345

• Вот публичный ключ для адреса 12345, и вы можете убедиться в том, что это тот самый публичный ключ, получив адрес посредством хеширования этого ключа.

• Вот подпись, которую я зашифровала с помощью приватного ключа, соответствующего этому адресу. Вы можете использовать публичный ключ, чтобы расшифровать ее и убедиться, что она соответствует данным транзакции, которые я отправляю.

![ib7-1](/img/ib-466.png)
|:--:|
_Транзакция, которая перемещает монеты, зашифрована с использованием приватного ключа и подтверждена цифровой подписью. Она расшифровывается с помощью публичного ключа, который известен всем._

Поскольку у всех теперь есть публичный ключ от почтового ящика Элис, они могут легко расшифровать цифровую подпись. Благодаря возможности удостовериться в правильности/корректности/валидности подписи, зная только публичный ключ отправителя, можно быть уверенным, что Элис использовала приватный ключ именно от этого адреса для подписи транзакции. В противном случае ее расшифровка не увенчалась бы успехом, поскольку публичный ключ может расшифровывать только сообщения, зашифрованные с помощью соответствующего приватного ключа. Но важно понимать, что ноды на самом деле видели не ее приватный ключ, а лишь доказательство того, что она смогла использовать его для шифрования своей подписи.

В отличие от подписи на чеке или банковского пароля, ваша цифровая подпись относится только к тем уникальным транзакционным данным, которые вы подписываете. Таким образом, ее нельзя украсть и использовать повторно в другой транзакции. Каждая транзакция получает новую подпись (даже если она отправляется с того же адреса с использованием того же приватного ключа), поскольку любое изменение входных данных приводит к изменению подписи.

# Возможно ли угадать приватный ключ?

Давайте высчитаем шансы угадать приватный ключ, который даст вам возможность переместить монеты c соответствующего публичного адреса. Помните, что ключ состоит из 256 бит. Каждый бит имеет только два возможных значения (один или ноль). Это означает, что каждый бит можно представить как бросок монеты.

Если бы у нас был 1-битный приватный ключ, это было бы равносильно тому, чтобы бросить монету один раз. Орел или решка, один или ноль? Ваш шанс угадать — один к двум.

Быстрый базовый обзор статистики: вероятность возникновения нескольких событий рассчитывается путем умножения между собой индивидуальных вероятностей каждого события. Если при подбрасывании монеты вероятность выпадения решки равна 1/2, то вероятность выпадения решки при подбрасывании двух монет подряд составляет 1/2 x 1/2 = 1/4 или 1 к 4.

Если бы вы пытались угадать результат 8 бросков монет подряд, вероятность успеха приравнивалась бы к одному из 28 исходов или один шанс из 256.

Автомобильный номерной знак имеет 6 букв и цифр. В английском языке — 26 букв и 10 цифр, так что всего 36 символов. Так как символов шесть, количество возможных номерных знаков = 366, так что ваши шансы угадать номерной знак моего авто — один к двум миллиардам [^2].

Номер кредитной карты состоит из шестнадцати цифр. Каждая цифра может иметь 10 значений, а цифр — 16, так что ваши шансы угадать номер моей кредитной карты равны 1 к 1016, то есть один к 10,000,000,000,000,000, или примерно один к десяти квадриллионам.

На Земле около 1050 атомов. Если я в случайном порядке подумаю об одном из них, ваши шансы угадать его будут

Один к <mark style="background-color: yellow">1,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000</mark>

В приватном ключе — 256 бит, что составляет 2256 или примерно 1077. Угадывание всего ключа было бы сродни угадыванию определенного атома из всей Вселенной или выигрышу в лотерею Powerball 9 раз подряд:

Один шанс из <mark style="background-color: yellow">115,792,089,237,316,195,423,570,985,008,687,907,853,269,984,665,640,564,039,457,584,007,913,129,639,936</mark>

Но что, если бы у вас был сверхмощный компьютер, который бы производил вычисления? Я не могу осветить эту тему лучше, чем пост на площадке Reddit: [https://bit.ly/2Dbw9Qd](https://bit.ly/2Dbw9Qd), который я рекомендую прочитать полностью. Хотя он и технический, последний абзац хорошо иллюстрирует насколько сложно перебрать все возможные 256-битные ключи:

> _"Итак, если бы вы могли использовать всю планету в качестве жесткого диска, сохраняя 1 байт на атом, используя звезды в качестве топлива и циклически перебирая 1 триллион ключей в секунду, вам потребовалось бы 37 октиллионов (1027) планет Земля для хранения информации и 237 миллиардов Солнц для питания устройства, способного на это, и все это заняло бы у вас 3.6717 окто-миллиарда лет”. —_ u/PSBlake на r/Bitcoin

По сути, вы не можете угадать чей-то приватный ключ. Более того, количество возможных адресов Биткоин настолько велико, что лучшие Биткоин-решения фактически генерируют новый адрес с новым приватным ключом для каждой транзакции, которую вы совершаете. Таким образом, вместо одного банковского счета, вы можете иметь тысячи или даже миллионы Биткоин-счетов: по одному на каждую транзакцию, которую вы когда-либо получали.

Возможно, вас смущает, что ваша учетная запись в сети Биткоин защищена только _случайностью_. Но, надеюсь, приведенное выше объяснение дает вам представление о том, что это намного безопаснее, чем пароль к вашему банковскому счету, находящемуся на центральном сервере, доступном для хакеров.

# Отслеживание остатков

Пришло время исправить одну последнюю невинную ложь, которую мы повторяли в предыдущих главах. На самом деле, в реестре нет остатков. Вместо этого Биткоин использует модель под названием UTXO: неизрасходованные транзакционные выходы. Неизрасходованные транзакционные выходы — это просто термин для обозначения монет, которые вы получили вследствие предыдущей транзакции, независимо от того, были они отправлены вам кем-то или добыты в процессе майнинга в виде _coinbase_-транзакции.

В отличие от металлических монет, которые могут быть определенного номинала, например 10, 25, 50 центов и т. д., Биткоин делится на 100,000,000 единиц, называемых сатоши. Поэтому, в зависимости от того, какие номиналы вы получили на свои адреса, вам может потребоваться объединить монеты с нескольких адресов или разделить более крупный UTXO на меньшие части для отправки кому-либо еще. Рассматривайте это, как отправку пачки монет в машину, которая их расплавляет и чеканит новые монеты любого номинала. Кошельки, о которых речь пойдет ниже в этой главе, обычно управляют всем этим за кулисами, так что вы просто указываете сумму, которую хотите отправить.

Допустим, у Элис есть адрес, который содержит 1 биткоин. Она хочет отправить Бобу 0.3 биткоина. Она генерирует транзакцию, которая показывает ее адрес с одним биткоин-UTXO в качестве ввода и двух выводов: новый биткоин-UTXO номиналом 0,3 на адрес Боба и новый биткоин-UTXO стоимостью 0,7 обратно на свой собственный адрес в качестве сдачи. Сдача может быть отправлена на исходный адрес отправителя или, для лучшей конфиденциальности, можно отправить ее на новый адрес, который она генерирует налету.

![ib7-2](/img/ib-467.png)
|:--:|
_Если у вас нет UTXO непосредственно с тем количеством BTC, которое вы хотите отправить, то он будет разделен и вы получите сдачу. Вы также можете объединить несколько UTXO для перевода большего количества BTC._

В блокчейне невозможно сказать, кто контролирует какой адрес так как для этого вам необходимо связать соответствующие приватные ключи с реальными личностями. Модель UTXO поддерживает очень хороший механизм обеспечения конфиденциальности, отправляя сдачу на новый адрес каждый раз, когда монеты перемещаются. Таким образом, человек может иметь сотни или тысячи адресов, если он отправлял или получал монеты много раз. Программное обеспечение кошелька управляет всем процессом за нас, поэтому нам не нужно беспокоиться о деталях.

Соответственно, чтобы проверить “баланс” определенного адреса, нам фактически нужно сложить все UTXO, которые имеют этот адрес в качестве вывода. Общий набор текущих UTXO в Биткоине растет, когда люди инициируют транзакции с одного адреса на несколько адресов, и сокращается, когда выполняют операции консолидации, при которых монеты с нескольких адресов отправляются на один адрес.

Модель UTXO позволяет легко и эффективно проверять двойное расходование, поскольку любой конкретный UTXO можно потратить только один раз. Нам не нужно знать всю историю расходов конкретного аккаунта.

Мы также можем создавать и уничтожать любое количество UTXO одновременно, создавая сложные транзакции, которые смешивают разные вводы и выводы.

Это поддерживает идею CoinJoin [^3], где несколько адресов участвуют в одной транзакции Биткоин, которая смешивает любое количество вводов для получения любого количества выводов, тем самым скрывая историю UTXO. Популярность подобных методов растет, и они важны для обеспечения конфиденциальности и _взаимозаменяемости_. Этот термин означает, что любой биткоин эквивалентен любому другому биткоину. Таким образом, если некоторые биткоины окажутся в руках сомнительных участников, они не испортятся навсегда только потому, что их когда-то использовали для чего-то безнравственного.

# Кошельки

Создание учетной записи в Биткоин-сети — это не что иное, как генерирование пары 256-битных случайных ключей. Мы можем создать тысячи или миллионы учетных записей, поэтому нам нужен способ их отслеживать. В сети Биткоин слово _кошелек_ используется для обозначения любого типа устройства, которое отслеживает ваши ключи. Оно может быть таким простым, как лист бумаги или сложным, как специализированное оборудование.

Оригинальный код Биткоин, опубликованный Сатоши, появился вместе с программным кошельком. Этот кошелек генерировал для вас адреса, хранил ваши ключи и выбирал для вас UTXO, чтобы вы могли легко отправлять любую сумму в биткоинах.

В отличие от вашего кошелька в банке, который обычно представляет собой мобильное или веб-приложение, созданное вашим банком, Биткоин является полностью открытой системой. Поэтому, существуют десятки кошельков, большинство из которых являются бесплатными, многие из которых — с открытым исходным кодом, а также с полдюжины вариантов специальных устройств и методов хранения монет; количество решений по хранению средств растет с каждым годом и большое количество новых кошельков на подходе. Любой, кто обладает знаниями в области компьютерного программирования, может создать свой собственный кошелек или изучить открытый исходный код кошелька, чтобы убедиться, что ничего подозрительного под капотом не происходит.

Поскольку ваш приватный ключ — единственное, что вам нужно, чтобы тратить свои монеты, вы должны очень тщательно оберегать его. Если кто-то украл вашу кредитную карту, вы можете позвонить в компанию, подать жалобу на факт мошенничества и попытаться вернуть ваши деньги. В сети Биткоин нет контролирующего органа. Если у кого-то есть ваш приватный ключ, он контролирует ваши монеты, и вам некому позвонить чтобы вернуть средства.

Приватные ключи также могут быть утеряны. Если вы храните свой кошелек на компьютере, а компьютер украден или сгорел, у вас проблема. Если вы будете следовать лучшим практикам сети Биткоин и генерировать новый адрес каждый раз, когда получаете платежи, безопасное хранение и резервное копирование этих приватных ключей быстро станет обременительным.

Со временем в экосистеме Биткоин появилось несколько решений этой проблемы. В 2012 году для создания Иерархических Детерминированных Кошельков было предложено BIP32 (Предложение по улучшению Биткоина (БИП) — механизм для распространения идей о том, как улучшить Биткоин). Идея заключается в том, что, используя только одно случайное число, известное под названием _сид (seed)_, мы можем непрерывно сгенерировать огромное количество пар ключей, представляющих Биткоин-адреса и привязанные к ним приватные ключи.

В настоящее время, если вы используете какое-либо общедоступное программное обеспечение или холодные кошельки, они автоматически генерируют для вас новые ключи для каждой транзакции, позволяя вам создавать резервные копии только одного мастер-ключа.

В 2013 году появился BIP39, чтобы сделать резервное копирование ключей еще проще. Вместо использования случайного числа ключи стали генерироваться из случайного набора человекочитаемых слов. Вот пример фразы _сид-фразы_:

<mark style="background-color: yellow">witch collapse practice feed shame open despair creek road again ice least</mark>

Благодаря этому методу резервное копирование ключей стало очень простым: вам достаточно записать сид-фразу на листе бумаги и положить его в сейф. Вы могли бы даже запомнить эту фразу и покинуть государство на грани экономического распада, такое, как Венесуэла, “ничего” при себе не имея. Никто бы не догадался, что вы перевозите свое богатство в собственной памяти.

Кроме того, для доступа к адресу Биткоин может требоваться более одного приватного ключа. Адреса с мультиподписью или _мультисиг-адреса_ могут использовать большое разнообразие схем безопасности. Например, два человека могут иметь общий счет с использованием мультисиг 1 из 2, где любая из сторон может подписывать транзакции и тратить монеты.

Мультисиг 2 из 2 – это вариант реализации мультиподписи, при котором для расходования монет требуется предоставить приватные ключи обоих владельцев. Это может использоваться для предотвращения единоличного контроля Биткоин-аккаунта (учетной записи в Биткоине), например, между деловыми партнерами.

Вы можете создать простую систему условного депонирования, используя мультисиг 2 из 3. Покупатель получает один ключ, продавец получает другой ключ, а третий ключ выдается арбитру. Если покупатель и продавец согласны, они могут разблокировать средства вместе. В случае возникновения спора арбитр может действовать совместно с одной из сторон, чтобы разблокировать средства.

Чтобы защититься от потери единственного приватного ключа, вы можете использовать схему мультиподписи 3 из 5. Это позволит вам получить доступ к средствам даже, если вы потеряете 2 ключа из 5 ключей и при этом иметь возможность разблокировать учетную запись. К примеру, вы можете хранить два ключа в разных местах, два — у разных доверенных, незнакомых между собой лиц и один — с помощью кастодиального _(custody)_ сервиса, такого как BitGo. Подобные сервисы вместе с вами подписывают ваши транзакции, делая ваш Биткоин очень устойчивым к краже, при этом, защищая вас от потери ключей.

Вы можете пойти еще дальше и создать адреса, которые будут разблокированы при выполнении довольно сложных условий, используя программные скрипты, такие как условные операторы (“если .. , то ..”). Вы можете даже заблокировать монеты на определенном адресе и сделать их вывод доступным только через 10 лет, и даже вы, как создатель данного адреса, не сможете изменить код, чтобы потратить эти монеты раньше указанного времени.

Такие компании, как _Casa_ и _Unchained Capital_, предлагают все больше и больше кастодиальных решений, которые помогают хранить ключи в безопасности. В отличие от банка, который может заморозить вашу учетную запись, эти кастодиальные сервисы действуют как резервный или доверенный соучредитель, но сами не могут получить контроль над вашими средствами без ваших ключей.

Программное обеспечение кошельков постоянно развивается, потому что для этого не требуется чье-либо разрешение, в отличие от приложения вашего банка. Поэтому мы постоянно видим новых участников и все больше инноваций.

Эти инновации значительны, они меняют мир к лучшему. Никогда прежде не представлялось возможным транспортировать свои сбережения настолько защищенным от изъятия или кражи образом.

{{< expand "Оглавление" "..." >}}

[Главная страница](/izobretaem-bitkoin)

[Вступление](/izobretaem-bitkoin/vstuplenie)  

[Глава 1: Что такое Биткоин](/izobretaem-bitkoin/glava-1)

[Глава 2: Отказываемся от посредника](/izobretaem-bitkoin/glava-2)

[Глава 3: Proof of Work](/izobretaem-bitkoin/glava-3)

[Глава 4: Майнинг](/izobretaem-bitkoin/glava-4)

[Глава 5: Обеспечение безопасности реестра](/izobretaem-bitkoin/glava-5)

[Глава 6: Форки и атаки 51%](/izobretaem-bitkoin/glava-6)

[Глава 7: Учетные записи, не идентифицирующие личность](/izobretaem-bitkoin/glava-7)

[Глава 8: Кто устанавливает правила?](/izobretaem-bitkoin/glava-8)

[Глава 9: Что дальше?](/izobretaem-bitkoin/glava-9)

{{< /expand >}}

[^1]: На самом деле, адресные номера — это гигантские 160-битные числа.

[^2]: Источником вдохновения для этого раздела послужила отличная публикация на площадке Medium, в которой подробно описываются вероятности различных событий. Я рекомендую прочитать полный пост для более глубокого понимания контекста: [https://medium.com/breathe-publication/a-dance-with-infinity-980bd8e9a781](https://medium.com/breathe-publication/a-dance-with-infinity-980bd8e9a781)

[^3]: [https://en.bitcoin.it/wiki/CoinJoin](https://en.bitcoin.it/wiki/CoinJoin)