# Module Documentation

## Module Text.Markdown.SlamDown

### Types


    data Block where
      Paragraph :: [Inline] -> Block
      Header :: Number -> [Inline] -> Block
      Blockquote :: [Block] -> Block
      List :: ListType -> [[Block]] -> Block
      CodeBlock :: CodeBlockType -> [String] -> Block
      Rule :: Block


    data CodeBlockType where
      Indented :: CodeBlockType
      Fenced :: Boolean -> String -> CodeBlockType


    data Date where
      Date :: Number -> Number -> Number -> Date


    data DateTime where
      DateTime :: Date -> Time -> DateTime


    data Expr a where
      Literal :: a -> Expr a
      Evaluated :: String -> Expr a


    data FormField where
      TextBox :: Expr String -> FormField
      RadioButtons :: Expr String -> Expr [String] -> FormField
      CheckBoxes :: Expr [Boolean] -> Expr [String] -> FormField
      DropDown :: Expr [String] -> Expr String -> FormField
      DatePicker :: Expr Date -> FormField
      TimePicker :: Expr Date -> FormField
      DateTimePicker :: Expr DateTime -> FormField


    data Inline where
      Str :: String -> Inline
      Entity :: String -> Inline
      Space :: Inline
      SoftBreak :: Inline
      LineBreak :: Inline
      Emph :: [Inline] -> Inline
      Strong :: [Inline] -> Inline
      Code :: Boolean -> String -> Inline
      Link :: [Inline] -> String -> Inline
      Image :: [Inline] -> String -> Inline
      FormField :: String -> Boolean -> FormField -> Inline


    data ListType where
      Bullet :: String -> ListType
      Ordered :: String -> ListType


    data SlamDown where
      SlamDown :: [Block] -> SlamDown


    data Time where
      Time :: Number -> Number -> Time


### Type Class Instances


    instance eqListType :: Eq ListType


    instance eqSlamDown :: Eq SlamDown


    instance monoidSlamDown :: Monoid SlamDown


    instance ordSlamDown :: Ord SlamDown


    instance semigroupSlamDown :: Semigroup SlamDown


    instance showBlock :: Show Block


    instance showCodeAttr :: Show CodeBlockType


    instance showDate :: Show Date


    instance showDateTime :: Show DateTime


    instance showExpr :: (Show a) => Show (Expr a)


    instance showFormField :: Show FormField


    instance showInline :: Show Inline


    instance showListType :: Show ListType


    instance showSlamDown :: Show SlamDown


    instance showTime :: Show Time


### Values


    eval :: (Maybe String -> [String] -> String) -> SlamDown -> SlamDown


    everywhere :: (Block -> Block) -> (Inline -> Inline) -> SlamDown -> SlamDown


## Module Text.Markdown.SlamDown.Html

### Types


    data Html


### Values


    markdownToHtml :: String -> String


    renderHtml :: Html -> String


    toHtml :: SlamDown -> [Html]


## Module Text.Markdown.SlamDown.Parser

### Values


    parseMd :: String -> SlamDown


## Module Text.Markdown.SlamDown.Pretty

### Values


    prettyPrintMd :: SlamDown -> String


## Module Text.Markdown.SlamDown.Parser.Inline

### Values


    parseInlines :: [String] -> [Inline]


## Module Text.Markdown.SlamDown.Parser.Utils

### Values


    flags :: R.RegexFlags


    isEmailAddress :: String -> Boolean


    isWhitespace :: String -> Boolean


    trim :: String -> String


    trimEnd :: String -> String



