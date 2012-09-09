Генератор DocBlock для Yii. Добавляет поддержку автодополнения для
публичных геттеров, сеттеров, событий, скоупов, релейшенов, поведений, атрибутов моделей AR


#Список реализованных фич:

- Если геттер(сеттер) имеет больше нуля(одного) обязательных параметров, то он игнорируется.
- Если свойство уже описано в одном из родительских классов, то он игнорируется.
- Сгенерированные комментарии можно редактировать! т.е. если вы захотите добавить описание в блок
комментариев(так называемые shortDescription и longDescription), то при перегенерации они будут
сохранены(вы же старались!).
- Если для задания описания или типа свойства не хватило информации в текущих исходниках,
то вы можете добавить их прямо в сгенерированный блок комментариев и они будут использоваться в дальнейшем
и не потеряются при перегенерации. Конечно же, если информации в исходниках достаточно для генерации
типа или комментария, то будет использована она, так что редактировать сгенерированные типы или
комментарии бесполезно - нужно редактировать источник информации, например комментарии к геттеру.
- Аннотации author|api|category|deprecated|example|filesource|ignore|internal|license|link|package|see|since|subpackage|todo|version|uses|used-by
будут сохранены(думаю этой простыни вам хватит)
- Поддержка @property-read/@property-write (по умолчанию выключено)
- Преобразование стилей кодирования camelCaseToUnderscore (по умолчанию выключено, т.к. требует внешнего преобразователя)
- Ну и приятный бонус: вертикальное выравнивание (можно выключить)

#Расширяемость

- Произвольный итератор для файлов (значит вы можете контролировать какие именно файлы будут обработаны). В комплекте идет итератор, который перебирает все модели всех модулей, т.е. рекурсивно проходится по директориям models всех модулей, доступных через Yii::app()->getModules().
- Произвольный итератор для свойств (значит вы можете контролировать для каких именно свойств будут сгенерированны аннотации). В комплекте идет итератор, который перебирает все
