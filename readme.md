Генератор DocBlock для Yii. Добавляет поддержку автодополнения для
публичных геттеров, сеттеров, событий, скоупов, релейшенов, поведений, атрибутов моделей AR

#Пример результата

~~~
[php]
/**
 *
 * !Attributes - атрибуты БД
 * @property string           $language
 * @property string           $status
 * @property integer          $comments_denied
 * @property string           $id
 * @property string           $user_id
 * @property string           $title
 * @property string           $url
 * @property string           $text
 * @property string           $date_create
 * @property integer          $order
 *
 * !Accessors - Геттеры и сеттеры класа и его поведений
 * @property                  $href
 * @property                  $content
 * @property                  $errorsFlatArray
 * @property                  $updateUrl
 * @property                  $createUrl
 * @property                  $deleteUrl
 *
 * !Relations - связи
 * @property Language         $language_model
 * @property TagRel[]         $tags_rels
 * @property Tag[]            $tags
 * @property int|null         $comments_count
 * @property User             $user
 * @property PageSectionRel[] $sections_rels
 * @property PageSection[]    $sections
 *
 * !Scopes - именованные группы условий, возвращают этот АР
 * @method   Page             published()
 * @method   Page             sitemap()
 * @method   Page             ordered()
 * @method   Page             last()
 *
 */

~~~

#Использование

1) Конфигурируется, как и любая консольная комманда Yii, однако сначала применяется базовая конфигурация:
`docBlock/configs/stdConfig.php`, затем файл заданный через свойство `$config` из той же директори
(для возможности задавать различные конфигурации из консоли), затем конфигурация из `commandMap`
2) Комманда работает с 2-мя итераторами: по файлам и по свойствам/методам класса - т.е. вы можете однозначно задать
для каких файлов и каких свойств/методов генерировать dockBlock'и.
По умолчанию в качестве итератора по файлам используется `ModelInModuleFilesIterator`,
он рекурсивно проходит по всем директориям вида `/moduleId/models/*`
А в качестве итератора по свойствам используется `YiiComponentPropertyIterator` - который обходит:
`attributes`, `events`, `accessors`, `relations`, `scopes`

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
- Аннотации
`author|api|category|deprecated|example|filesource|ignore|internal|license`,
`link|package|see|since|subpackage|todo|version|uses|used-by`
будут сохранены(думаю этой простыни вам хватит)
- Преобразование стилей кодирования camelCaseToUnderscore (по умолчанию выключено, т.к. требует внешнего преобразователя)
- Ну и приятный бонус: вертикальное выравнивание (можно выключить)
