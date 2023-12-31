# 2.1LibraryTask

Сущности:

Читатели (Readers):

Номер читательского билета (ReaderID) - первичный ключ
ФИО (FullName)
Адрес (Address)
Телефон (Phone)


Книги (Books):

Шифр книги (BookID) - первичный ключ
Название (Title)
Шифр автора (AuthorID)
Год издания (PublicationYear)
Объём (Volume)
Цена (Price)
Количество экземпляров в фонде (QuantityInStock)
Шифр издательства (PublisherID) - внешний ключ 

Издательства (Publishers):

Шифр (PublisherID) - первичный ключ
Название (PublisherName)
Город (City)

Авторы (Authors)

Шифр автора (AuthorID)
ФИО автора (AuthorName)


Связи между сущностями:

Один читатель может взять несколько книг из библиотеки, и каждая книга может быть взята несколькими читателями. Таким образом, у нас здесь многие ко многим (many-to-many) отношение. Для этого создадим промежуточную таблицу "Читательский билет - Книга" (ReaderBook), чтобы отслеживать, какие книги взяты каждым читателем, и какие читатели взяли каждую книгу. Эта таблица будет иметь следующие поля:

Номер читательского билета (ReaderID) - внешний ключ к таблице "Читатели"
Шифр книги (BookID) - внешний ключ к таблице "Книги"
Дата возврата (ReturnDate) - это поле может использоваться для отслеживания, когда книга была возвращена читателем.

Один автор может написать несколько книг, а одна книга может быть написана несколькими авторами. Получается связь многие ко многим (many-to-many). Для связи между ними, сохдадим промежуточную таблицу "Автор - Книга" (AuthorBook), чтобы отслеживать, какие книги написаны каким писателем, и какие писатели написали какую книгу. Эта таблица будет иметь следующие поля:
Шифр писателя (AuthorID) - внешний ключ к таблице "Авторы"
Шифр книги (BookID) - внешний ключ к таблице "Книги"

Каждая книга издана определенным издательством, поэтому между таблицами "Книги" и "Издательства" существует связь один ко многим (one-to-many). В таблице "Книги" мы добавим внешний ключ "Издательство", который будет ссылаться на таблицу "Издательства".


Ключи:
Первичные ключи:

В каждой таблице определен первичный ключ, который уникально идентифицирует каждую запись в этой таблице:
Читатели: ReaderID
Книги: BookID
Издательства: PublisherID
Авторы: AuthorID

Внешние ключи:

В таблице "Читательский билет - Книга", есть два внешних ключа:
Номер читательского билета (ReaderID) - ссылается на таблицу "Читатели"
Шифр книги (BookID) - ссылается на таблицу "Книги"

В таблице "Автор - Книга", есть два внешних ключа:
Шифр автора (AuthorrID) - ссылается на таблицу "Авторы"
Шифр книги (BookID) - ссылается на таблицу "Книги"

В таблице "Книги", есть внешний ключ "Шифр издательства", который ссылается на таблицу "Издательства".

