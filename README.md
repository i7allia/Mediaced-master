# Портал объявлений Mediaced
 Test Blazor Project for QA Studing Group
 Client and Server

 Инструкция по развёртыванию:
 1. Основной файл проекта находится в папке Mediaced\Mediaced.sln - для открытия проекта в Visual Studio нужно щелкнуть его мышью два раза 
 2. Для корректной работы проекта должен работать Mock-сервис Mockoon на порту 3000 :
![Mockoon](md/Mockoon1.png)
 3. Также в заголовках Mockoon должен быть прописан заголовок "Access-Control-Allow-Origin":"*"
![Mockoon](md/Mockoon2.png)
4. В файле сервера \MediacedServer\Prefs\Database.cs нужно прописать путь к свой базе данных с объявлениями (скрипты ниже), при этом если вы устанавливали по инструкции, то скорее всего поднят отдельный инстанс NODE1. Путь к базе будет выглядеть следующим образом:
    > "Data Source=localhost\\NODE1;Initial Catalog=Mediaced;Persist Security Info=False;User ID=sa;Password=Pa$$w0rd"
5. Перед запуском проектом создать базу данных Mediaced
6. Добавить таблицу 'advertisments':
    ```sql
    CREATE TABLE [dbo].[advertisements](
        [id] [int] NOT NULL,
        [firstname] [nvarchar](50) NOT NULL,
        [lastname] [nvarchar](50) NOT NULL,
        [patronimic] [nvarchar](50) NULL,
        [phonenumber] [varchar](50) NOT NULL,
        [email] [varchar](50) NOT NULL,
        [age] [int] NOT NULL,
        [advtext] [text] NOT NULL,
        [priceusd] [float] NOT NULL,
        [courseusd] [float] NOT NULL,
        [pricebyn] [float] NOT NULL
    );
    ```
7. Для возможности проверки отображения вставить строку данных:
```sql
INSERT INTO [dbo].[advertisements]
           ([id]
           ,[firstname]
           ,[lastname]
           ,[patronimic]
           ,[phonenumber]
           ,[email]
           ,[age]
           ,[advtext]
           ,[priceusd]
           ,[courseusd]
           ,[pricebyn])
     VALUES
           (1, 'Name1', 'LastName1', 'Patronimic', '+375275874747', 'email@email.com', 32, 'Advertisement Text', 20.5, 3.2, 65.6);
```
