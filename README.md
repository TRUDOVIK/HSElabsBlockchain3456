Лаба 3
1) Смарт-контракты без конструктора - это смарт-контракты, которые не имеют специальной функции
   для инициализации переменных или параметров при создании контракта. Это означает, что такие контракты не могут получать аргументы 
   при развертывании и должны использовать значения по умолчанию для своих переменных.
   Такие контракты могут быть полезны, если вы хотите создать простой и статичный контракт,
   который не зависит от внешних факторов или ввода пользователя.
2) Contract - это базовый тип смарт-контракта, который содержит переменные, функции, модификаторы и события.
   Это самый распространенный тип смарт-контракта, который используется для создания логики и правил взаимодействия между участниками сети.
   Contract может наследовать другие контракты или интерфейсы, а также иметь конструктор для инициализации параметров при развертывании.
   Library - это специальный тип смарт-контракта, который содержит многократно используемый код, который может быть вызван из других контрактов.
   Library не может хранить свое состояние (переменные) и не может наследовать другие контракты или интерфейсы.
   Library также не может иметь конструктор или получать эфир при вызове функций. Library используется для оптимизации газа,
   уменьшения размера байткода и повышения читаемости кода.
3) EVM имеет три типа памяти, которые используются для разных целей:
   Стек - это область памяти, которая хранит ограниченное количество 256-битных значений. 
   Стек работает по принципу LIFO (last in, first out), то есть последнее добавленное значение извлекается первым. 
   Стек используется для хранения локальных переменных и параметров функций смарт-контракта. 
   Стек ограничен 1024 элементами и не может быть адресован напрямую.
   Память - это область памяти, которая хранит произвольное количество байтов. 
   Память работает по принципу FIFO (first in, first out), то есть первое добавленное значение извлекается первым. 
   Память используется для хранения временных данных, таких как массивы, структуры и строки. Память может быть адресована напрямую и расширяется по мере необходимости.
   Хранилище - это область памяти, которая хранит постоянные данные смарт-контракта. Хранилище работает по принципу ключ-значение, 
   то есть каждому значению соответствует уникальный 256-битный ключ. Хранилище используется для хранения глобальных переменных и состояния смарт-контракта. 
   Хранилище может быть адресовано напрямую и сохраняется в блокчейне.
4) ABI (Application Binary Interface) необходим для кодирования и декодирования данных, передаваемых между смарт-контрактами и внешними вызывающими.
   ABI определяет формат данных и способ вызова функций контракта, что позволяет клиентским приложениям и другим контрактам взаимодействовать с контрактом.
5) Вставки assembly в смарт-контракт - это способ написания низкоуровневого кода,
   который работает непосредственно с виртуальной машиной Ethereum (EVM). Они позволяют оптимизировать производительность и
   стоимость исполнения смарт-контракта, а также реализовать функции, которые недоступны на языке Solidity.
6) msg - это переменная, которая содержит данные о вызывающем смарт-контракт или внешнем аккаунте.
   tx - это переменная, которая содержит данные о текущей транзакции.
   block - это переменная, которая содержит данные о текущем блоке.
7) Идеальных способов получения случайного числа в блокчейне не существует. Однако можно использовать хеш блока или транзакции как источник случайности.
   Использовать оракулы - это специальные смарт-контракты или сервисы, которые предоставляют данные из внешнего мира в блокчейн.
   Использовать комитмент-схемы - это протоколы, которые позволяют участникам обязаться к определенному значению без раскрытия его до определенного момента.
   Например, участники могут отправить хеш своего выбранного случайного числа в смарт-контракт, а затем раскрыть его после того, как все сделали то же самое.
   Смарт-контракт может затем вычислить общее случайное число путем комбинирования всех раскрытых значений.

Лаба 4
1) Формальные спецификации и проверки смарт-контрактов - это область, которая развивается и получает все больше внимания в индустрии блокчейна.
   Формальные спецификации позволяют описать желаемое поведение и свойства смарт-контрактов на строгом математическом языке, а формальные проверки позволяют автоматически или полуавтоматически доказать,
   что код смарт-контракта соответствует спецификации и не содержит ошибок или уязвимостей. Это важно для обеспечения безопасности,
   надежности и доверия к смарт-контрактам, которые могут управлять большими суммами денег или другими ценными активами.
   
Лаба 5
1) Во-первых, локальная EVM позволяет тестировать и отлаживать смарт-контракты в изолированной и контролируемой среде,
   без риска повлиять на реальный блокчейн или потерять реальные средства.
   Во-вторых, локальная EVM обычно работает быстрее и дешевле, чем рабочая EVM,
   так как она не требует синхронизации с другими узлами, ожидания подтверждения транзакций или оплаты комиссий за газ.
   В-третьих, локальная EVM дает больше гибкости и возможностей для экспериментов с разными параметрами, версиями и функциями EVM.
2) Для call:
   (bool success, ) = targetAddress.call{value: msg.value}(""); require(success, "Call failed");
   Для delegatecall:
   Функция delegatecall не позволяет напрямую передавать ETH, так как он выполняет код целевого контракта в контексте вызывающего контракта, сохраняя msg.sender и msg.value неизменными. 
   Если нужно передать ETH вместе с вызовом delegatecall, можно сначала отправить ETH на адрес контракта, а затем использовать delegatecall для вызова функции, которая будет управлять этими средствами.