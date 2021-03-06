# 정규 표현식 (Regular Expression)
- 여러가지 패턴의 문자열을 하나의 문자열에 표현하는 방식이다.
- [手と目で覚える正規表現入門シリーズ](https://qiita.com/jnchito/items/893c887fbf19e17d3ff9) 블로그의 내용으로 [regex101](https://regex101.com/)에서 연습하는 것을 추천한다.

- *정규표현식의 구성요소*

구성요소 | 개요
--------|------
앵커(Anchor) | 문자열이 매칭되는 위치를 나타낸다.
메타 시퀀스(Meta Sequence) | 매칭 될 문자의 종류를 나타낸다.
수량 지정자(Quantifier) | 문자열의 출현 수를 나타낸다.
문자 그룹(Character Class) | 문자 그룹 내에 있는 문자 중 하나를 포함한 부분이 매칭된다.
그룹화 구성체(Group Construct) | 정규표현식의 부분식을 나타낸다. 조건 지정이 가능하며, 저장 기능이 있어 치환과 같이 쓰인다.
치환(Substitution) | 매칭된 부분을 치환 할 때 사용된다.
이스케이프 문자(Escape character) | 특별한 의미를 가지는 문자의 의미를 제거하여 사용하려 할 때 이용된다.

## 앵커(Anchor)

요소 | 설명
----|------
`^` | 문자열의 처음을 나타낸다. 2행 이상의 문자열인 경우, 개행 후 문자열의 처음도 대상이 된다.
`$` | 문자열의 끝을 나타낸다. 2행 이상의 문자열인 경우, 개행 후 문자열의 끝도 대상이 된다.
`\b` | 단어의 경계를 나타낸다. (ex: w1인 경우 해당 단어의 맨 앞과 맨 뒤)
`\B` | 단어의 경계가 아닌 곳을 나타낸다. (ex: w1인 경우 w와 1사이)

## 메타 시퀀스(Meta Sequence)
- 문자는 숫자, 영문자, 여백, 그 외 문자(특수기호, 타 언어)로 나눌 수 있다.
- 메타 시퀀스는 문자의 종류에 따른 표현방법을 제공한다.

요소 | 설명
----|------
`.` | 문자 1개를 나타낸다. (개행 문자(`\n`, `\r`)는 제외)
`\d` | 숫자 1개를 나타낸다. (`[0-9]`와 동일)
`\D` | 숫자가 아닌 문자 1개를 나타낸다. (`[^0-9]`와 동일)
`\w` | 영문자 및 숫자 1개를 나타낸다. (`[a-zA-Z0-9_]`와 동일)
`\W` | 영문자 및 숫자가 아닌 문자 1개를 나타낸다. (`[^a-zA-Z0-9_]`와 동일)
`\s` | 여백 1개를 나타낸다. (`[\r\n\t\f\v ]`와 동일)
`\S` | 여백이 아닌 문자 1개를 나타낸다. (`[^\r\n\t\f\v ]`와 동일)
`\t` | 탭(Tab)을 나타낸다.
`\n` | 개행문자(new line)를 나타낸다.
`\r` | 캐리지 리턴(Carriage Return; CR)을 나타낸다.

## 수량 지정자(Quantifier)
- 문자, 메타 시퀀스, 문자 그룹, 그룹화 구성체의 직후에 사용되며 수량을 나타낸다.
- 수량 지정자를 2개 이상 연속으로 사용 할 수 없다.

요소 | 설명
----|------
`{a}` | a개를 나타낸다. (a == 검색대상의 수)
`{a, b}` | a개부터 b개 사이의 수량을 나타낸다. (a ≤ 검색대상의 수 ≤ b)
`{a,}` | a개 이상의 수량을 나타낸다. (a ≤ 검색대상의 수)
`?` | 0개 또는 1개를 나타낸다.
`+` | 1개 이상을 나타낸다. greedy
`+?` | 1개 이상을 나타낸다. lazy
`*` | 0개 이상을 나타낸다. greedy
`*?` | 0개 이상을 나타낸다. lazy

### greedy와 lazy

탐색조건 | 설명
--------|-----
greedy(탐욕) | 가장 길게 매치. 해당하는 조건의 매칭 가능 대상 중 범위가 큰 조건이 작은 조건을 포함하고 있는 경우, 큰 조건을 매칭대상으로 설정한다.
lazy(게으름) | 가장 짧게 매치. 해당하는 조건의 매칭가능 대상 중 범위가 큰 조건이 작은 조건을 포함하고 있는 경우, 작은 조건을 매칭대상으로 설정한다.

## 문자 그룹(Character Class)

요소 | 설명
----|------
`[abc]` | a 또는 b 또는 c일 경우를 나타낸다.
`[^abc]` | a 또는 b 또는 c가 아닌 문자를 나타낸다.
`[a-z]` | a부터 z까지의 영문 소문자를 나타낸다. (`[]`안 영문 소문자 변경가능)
`[^a-z]` | a부터 z까지의 영문 소문자가 아닌 문자를 나타낸다.
`[a-zA-Z]` | 영문 대소문자를 나타낸다.
`[0-9]` | 숫자를 나타낸다.
`[-az]` | - 또는 a 또는 z일 경우를 나타낸다. (-가 특별한 의미를 가지지 않는다.)

## 그룹화 구성체(Group Construct)

요소 | 설명
----|------
`(...)` | ...에 해당하여 매칭된 부분을 그룹화 하고, 저장 할 것을 나타낸다.
`(a\|b)` | a에 해당하거나 b에 해당하는 경우를 나타낸다. 매칭될 경우 저장된다.
`(?:...)` | 그룹화는 하지만 저장하지 않는 것을 나타낸다.
`a(?=b)` | a가 매칭되는 경우 중 b가 매칭되는 경우만 한정 하는 것을 나타낸다. b는 매칭대상에서 제외된다.
`a(?!b)` | a가 매칭되는 경우 중 b가 매칭되지 않는 경우만 한정 하는 것을 나타낸다.

## 치환(Substitution)
- 치환기능을 이용하면 매칭된 부분을 원하는 문자열로 치환 할 수 있다.
- 이하의 요소를 사용하면 저장 및 매칭된 부분을 치환에 이용이 가능하다.

요소 | 설명
----|-------
`$1` | 저장 한 부분을 나타낸다. $뒤 숫자는 포착 순번을 나타낸다.
<code>$`</code> | 매치된 부분의 앞쪽 내용을 나타낸다.
`$'` | 매치된 부분의 뒤쪽 내용을 나타낸다.
`$&` | 매치된 부분을 나타낸다.

## 이스케이프 문자(Escape character)
- 정규표현식에서 특별한 의미를 가지는 문자를 단순 검색을 위한 문자열로 쓰기 위해서는 역슬러시(`\`)를 붙여주면 된다.  
  (ex: `\\`, `\^`, `\$`, `\*`, `\+`, `\?`, `\.`, `\|`, `\{`, `\}`, `\(`, `\)`, `\[`, `\]`, `\/`)

## 참고
- [regex101.com > quick reference](https://regex101.com/)
- [qiita > 初心者歓迎！手と目で覚える正規表現入門・その１「さまざまな形式の電話番号を検索しよう」](https://qiita.com/jnchito/items/893c887fbf19e17d3ff9)
- [qiita > 初心者歓迎！手と目で覚える正規表現入門・その２「微妙な違いを許容しつつ置換しよう」](https://qiita.com/jnchito/items/64c3fdc53766ac6f2008)
- [qiita > 初心者歓迎！手と目で覚える正規表現入門・その３「空白文字を自由自在に操ろう」](https://qiita.com/jnchito/items/6f0c885c1c4929092578)
- [qiita > 初心者歓迎！手と目で覚える正規表現入門・その４（最終回）「中級者テクニックをマスターしよう」](https://qiita.com/jnchito/items/b0839f4f4651c29da408)
- [Microsoft Docs > 正規表現言語 - クイック リファレンス](https://docs.microsoft.com/ja-jp/dotnet/standard/base-types/regular-expression-language-quick-reference)
