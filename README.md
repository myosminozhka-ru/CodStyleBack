# Меню

<div class="filter">
    <details>
    <summary>Общие рекомендации</summary>

* [Развертывание проекта](#Развертывание-проекта)
   * [Git](#git)
   * [Файлы](#Файлы)
   * [Строки](#Строки)
   * [Именования](#Именования)

* [Основы синтаксиса](#Основы-синтаксиса)
   * [Массивы](#Массивы)
   * [Функции](#Функции)
   * [Управляющие конструкции](#Управляющие-конструкции)

    </details>

    <details>
    <summary>Объектно-ориентированное программирование</summary>

+ [Пространства имён и оператор use](#Пространства-имён-и-оператор-use)
+ [Классы, свойства и методы](#Классы-свойства-и-методы)
+ [Extends и implements](Extends-и-implements)
+ [Свойства](#Свойства)
+ [Методы](#Методы)
+ [Аргументы методов](#Аргументы-методов)
+ [abstract, final и static](#abstract-final-и-static)

    </details>

    <details>
    <summary>Документация</summary>

* [Классы](#Классы)

    </details>

</div>

----

<br>

## Общие рекомендации
<br>

+  ### Развертывание проекта

    + #### Git
      + При развертывании проекта обязательно нужно составить .gitgnore\

      + Подключить гит, в гит не должны попадать авторизационные данные проекта. подключение к бд, ssh ..

      + Проект должен быть приватным и находится в гите компании.


   + #### Файлы

     + Все файлы структуры должны быть именованы максимально информативно, Информацию может нести как путь к файлу, так и именование самого файла.

        ```php
        GetUsers.php или Users/Get.php
        ```

     + Структура проекта должна быть понятной, минимальное подключение файлов через ```include_once() ``` , для повторного использования кода используйте ```use```

     + Файлы должны быть написаны в кодировке ```UTF-8``` (в редакторах это стандарт)


   + #### Строки
     + Длина строки желательно не должна превышать 80 символов.

     + Недопустимы конструкции по типу:
       ```php
       if(1>+{ true }

        Можно заменить на:

          1>1 ?: false;

        Или:

           if(1>+
           {
               true
           }
       ```
     + Используйте пустые строки для улучшения читаемости кода
       ```php
       Правильно:

          protected $data;

          function newFunction($result)
          {
              return $result
          }

          function newFunction2($result)
          {
              return $result
          }

       Не правильно:

          protected $data;
          function newFunction($result)
          {
              return $result
          }
          function newFunction2($result)
          {
              return $result
          }
       ```


   + #### Именования

     + Всем файлам, переменным, константам, функциям, классам и методам давать "говорящие" названия, чтобы они отражали свою суть, а не были набором безсмысленных символов.

     + В рамках одного проекта придерживаться одного стиля именования переменных, `camelCase` или `snake_case`

     +  Имена констант и глобальных переменных всегда должны быть в верхнем регистре в стиле `UPPER_CASE`.

     +   Функции/методы класса писать в верблюжьей нотации, где первое слово начинается с маленькой буквы, все остальные с большой в стиле `сamelCase()`.

     +   В функциях/методах класса использовать префиксы: `is (обозначение вопроса)`, `get (получить значение)`, `set (установить значение)`.

     + Имена классов в стиле StudlyCaps.
     Каждое слово в имени класса с большой буквы и никаких символов, кроме букв латинского алфавита.


+ ### Основы синтаксиса
  + Однострочный комментарий `//` `#` использовать можно везде.
  Комментарии писать грамотно с заглавной буквы и делать отступ в один пробел слева.
     ```php
         Правильно:
         // мой комментарий
         #
         Не правильно:
         //мой комментарий
     ```
  +  В качестве отступов использовать табуляцию длиной равной 4-м и не лепить код к левому краю.
      ```php
          if()
              if()
                  echo 'ok';

          die();
      ```
  + Булевы значения писать явно `true` , `false`, `null` , не заменять на `0` или `1`
  +  Нельзя писать на одной строке более одной инструкции.
      ```php
      //Неправильно
      $a = $b; $b = $c; $c = $a;

      //Правильно
      $a = $b;
      $b = $c;
      $c = $a;
      ```

  + При выводе `HTML` через `PHP` также придерживаться длины строки 80 символов используя конкатенацию, табуляцию и перенос строк.
  + В тернарном операторе заключать  в скобки только условие, при сложном условии стоит заменить его на `if/else` и не стесняться его использовать.
     ```php
      $var = (условие) ? 'если true' : 'если false';
     ```
  + Использовать сокращение тернарного оператора
     ```php
         $var = 'переменная' ?: 'другая переменная';
     ```
  + Использовать null-коалисцентный оператор только для проверки на null. Часты случаи ошибок в коде из-за неправильного использования оператора `??`.
  + Короткие строки писать выше длинных.
     ```php
     use \Bitrix\Main\Entity,
         \Bitrix\Highloadblock as HL,
         \Godra\Api\Helpers\Utility\Misc;
     ```
  + #### Массивы
    + При множественной инициализации переменных выравнивать значения между ними по правому краю используя доп. пространство.
        ```php
            protected static $row_data    = [];
            protected static $select_rows = [];
            protected static $api_ib_code = false;
        ```
    + Все массивы прописывать через `[]` вместо стандартного `array()`.
    + Придерживаться такому форматированию массивов

        ```php
        // Если значений больше 2х - каждый аргумент с новой строки
            protected static $select_rows = [
                [ 'name' => 'URL'],
                [ 'name' => 'NAME'],
                [ 'name' => 'CODE'],
                [ 'name' => 'IBLOCK_ID'],
                [ 'name' => 'ID', 'alias' => 'id'],
                [ 'name' => 'PICTURE', 'method' => '\\CFile::getPath'],
            ];

        // По возможности выравнивать оператор |=>| , после последнего элемента оставлять запятую.
            [
                'limit'  => 1,
                'select' => ['*'],
                'filter' => [ 'UF_URL' => $url ],
            ]
        ```

  + #### Функции
    + При вызове функции пробелы между названием функции и открывающей круглой скобкой недопустимы.
    + В списке аргументов необходим один пробел после каждой запятой и недопустимы пробелы перед запятыми.

  + #### Управляющие конструкции
    + Стараться короткие конструкции умещать в тернарный оператор
      ```php
          // Не правильно
          if($x>$y)
          {
              $res = $x;
          }
          else
          {
              $res = $y
          }

          // Правильно
          $res = $x > $y ? $x : $y;
       ```

    + Использовать в конструкциях фигурные скобки `{}`
       ```php
       // Не правильно
          if(true):
              return 'ok';
          endif;

       // Правильно
          if(true)
          {
              return 'ok';
          }
       ```
    + Открывающую фигурную скобку ставить под началом выражения и на одном уровне вертикально с закрывающей
        ```php
       if(true)
       {
           return 'ok';
       }
        ```
    + Избегать лишних фигурных скобок если в условии/блоке одно выражение.
       ```php
       if(isset($name))
          return $name;
       ```
<br>

## Объектно-ориентированное программирование

  + ### Пространства имён и оператор use
    + После объявления пространства имен namespace необходима одна пустая строка.
    +  Оператор use должен быть после объявления простарнства имён namespace.

    + Использовать один `use` для всех обьевленных namespas-ов
    +  После блока операторов  use должна быть одна пустая строка.

    ```php
    namespace Godra\Api\HighloadBlock;

    use \Godra\Api\Iblock,
        \Bitrix\Iblock\SectionTable,
        \Godra\Api\Helpers\Utility\Misc;

       ```
  + ### Классы, свойства и методы
    +  Каждый класс должен располагаться в отдельном файле именовоном так-же как и сам класс.

  + ### Extends и implements
    +  Ключевые слова extends и implements располагать на одной строке с именем класса.
    +  Наследование классов не должно быть слишком запутанным, максимум 2 наследования.
    +  Все используемые пространства имён нужно прописать в `use` и использовать в коде не полный namespace, а только его последнее или 2 последних именования

    <br>

    ```php
    use \Godra\Api\Iblock,
        \Bitrix\Iblock\SectionTable,
        \Godra\Api\Helpers\Utility\Misc;

    class Base
    {
        function __construct()
        {
            SectionTable::getList();
            Misc::getDte();
        }
    }
    ```
  + ### Свойства
    + Для всех свойств и методов класса необходимо объявлять область видимости public, static, protected, private;
    +  Разделять пустой строкой константы и группы свойств по области видимости.
    +   Недопустимо в одном объявлении указывать более одного свойства.

    ```php
    abstract class Base
    {
        public static $select_rows = [];
        protected static $row_data = [];
        private static $api_ib_code = false;
    }
    ```
  + ### Методы
    +  Для всех методов класса необходимо объявлять область видимости public, static, protected, private;
    +   Недопустимо объявлять методы с пробелом между названием и круглой скобкой.

  + ### Аргументы методов
    +  Аргументы метода со значениями по-умолчанию располагать в конце списка аргументов.
        ```php
        public function getNameByIdOrCode($id_or_code, $type = null )
        {
            if($type)
                $filter = [$type => $id_or_code];
        }
        ```
  + ### abstract, final и static
    + Ключевые слова abstract и final пишутся перед модификаторам видимости.
    + Ключевое слово static пишется после модификатора видимости.

    ```php
    abstract class Base
    {
        protected satic function getName()
        {
            return;
        }
    }
    ```
---
<br>

## Документация
  + ### Классы
    + Каждый класс должен иметь phpDoc блок с описанием входных данных `__construct` и сути класса
    + Переменные в классе также должны быть описаны
    + Каждая функция/метод класса должна иметь doc-блок.

    ```php
    use \Bitrix\Iblock\IblockTable;

    /**
     * Базовый абстрактный класс Каталога
     * @param int $id id Каталога
     */
    abstract class Base
    {
        /**
         * Id каталога
         * @var int
         */
        protected $id;

        function __construct($id)
        {
            $this->id = $id;
            $this->getCatalogById($this->id)
        }

        /**
         * Получение инфоблока каталога
         * @param int $id ID инфоблока
         * @return string|void
         */
        protected function getCatalogById($id)
        {
            return IblockTable::getById($id)->fetch()['NAME'];
        }
    ```