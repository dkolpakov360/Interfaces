# Импорт/Экспорт с интерфейсами =-

Необходимо разработать механизм, с помощью которого можно провезти импорт/экспорт, взяв данные из
любого источника данных и положив результат их обработки в любое другое место. При этом эти данные могут
быть преобразованы любым способом.

Таким образом нужно разработать импорт, который делает следующее: считывает данные из выбранного
источника, затем каждый элемент этих данных конвертирует всеми указанными конвертерами, а затем записывает
результат в указанное место.

a. Создайте следующие интерфейсы
- Reader - драйвер чтения - содержит один метод read(): array - который читает и возвращает
данные в виде массива

- Writer - драйвер записи - содержит один метод write(array $data) - который принимает
данные в виде массива для записи

- Converter - конвертация строки данных - содержит один метод convert($item) - конвертирует
один элемент массива и возвращает результат конвертации.

b. Создайте класс импорта Import, со свойствами $reader, $writer и $converters = []

- public function from(Reader $reader) - устанавливает значение свойства $reader и возвращает
$this  

- public function to(Writer $writer) - устанавливает значение свойства $writer и возвращает
$this  

- public function with(Converter $converter) - Добавляет конвертер в свойство $converters и
возвращает $this  

- public function execute() - производит импорт/экспорт данных из $reader в $writer  

c. Реализуйте описанные методы.

d. Согласно разработанному коду импорт можно произвести, примерно, такой конструкцией (new Import()) // Создаем новый объект - импорт

->from(new YourReader()) // Регистрируем в импорте reader - как будем читать  
->to(new YourWriter()) // Регистрируем в импорте writer - куда будем писать  
->with(new YourConverter()) // Регистрируем в импорте сколько угодно конвертеров - как данные будут обработаны перед записью   
->with(new YourConverter())  
->execute()  

e. В конструкции классы YourReader, YourWriter и YourConverter - это названия для демонстрации кода, под ними подразумеваются ваши реализации соответствующих интерфейсов. Названия ваших реализация должны быть осмысленными, например ArrayReader , но точно не YourReader.

f. Создайте свои реализации Reader и Writer, например читать из файла или массива, и писать в
файл, в массив, в строку, в сессию куда угодно. Создайте свои реализации Converter’а.

g. Проведите свой импорт/экспорт.
