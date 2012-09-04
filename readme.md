Всех же ломает описывать свойства над классами? Особенно когда добавляешь новое поле в базу или новый геттер?
А Автокомплита хочется.
Хочется - получите! Автогенератор DocBlock для классов.

#Список реализованных фич:

- Произвольный итератор для файлов (значит вы можете контролировать какие именно файлы будут обработаны). В комплекте идет итератор, который перебирает все модели всех модулей, т.е. рекурсивно проходится по директориям models всех модулей, доступных через Yii::app()->getModules().
- Произвольный итератор для свойств (значит вы можете контролировать для каких именно свойств будут сгенерированны аннотации). В комплекте идет итератор, который перебирает все публичные свойства, геттеры, сеттеры, события, поведения(их свойства, геттеры и сеттеры, если компонент поддерживает метод behaviors), атрибуты моделей(т.е. если компонент поддерживает метод getAttributes(), то итератор не побрезгует им воспользоваться)
- Если геттер(сеттер) имеет больше нуля(одного) обязательных параметров, то он игнорируется.
- Если свойство уже описано в одном из родительских классов, то он игнорируется.
- Если для геттера описана аннотация @return она будет учтена(тип и комментарий будут добавлены в свойство чтения).
- Самая вкусняшка: Сгенерированные комментарии можно редактировать! т.е. если вы захотите добавить описание в блок комментариев(так называемые shortDescription и longDescription), то при перегенерации они будут сохранены(вы же старались!).
- Если для задания описания или типа свойства не хватило информации в текущих исходниках, то вы можете добавить их прямо в сгенерированный блок комментариев и они будут использоваться в дальнейшем и не потеряются при перегенерации. Конечно же, если информации в исходниках достаточно для генерации типа или комментария, то будет использована она, так что редактировать сгенерированные типы или комментарии бесполезно - нужно редактировать источник информации, например комментарии к геттеру.
- Аннотации author|api|category|deprecated|example|filesource|ignore|internal|license|link|package|see|since|subpackage|todo|version|uses|used-by будут сохранены(думаю этой простыни вам хватит)
- Поддержка @property-read/@property-write (по умолчанию выключено)
- Преобразование стилей кодирования camelCaseToUnderscore (по умолчанию выключено, т.к. требует внешнего преобразователя)
- Ну и приятный бонус: вертикальное выравнивание (можно выключить)

#Already can:

- Custom file iterator
- Custom property iterator
- If getter(setter) has more than 0(1) required params, it ignoring
- If property describe in any parent class, it ignoring
- If getter has @return annotation, will using type and comment from it
- You can edit Autogenereting comments! If  you wanna add description for docBlock or property it will saved
after regenereting. Info from source have higher priority.
- Will save next annotations: author|api|category|deprecated|example|filesource|ignore|internal|license|link|package|see|since|subpackage|todo|version|uses|used-by
- Support @property-read/@property-write (disabled by default)
- Convert coding style camelCaseToUnderscore (disabled by default)
- Vertical alignment (enabled by default)