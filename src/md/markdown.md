# 마크다운 문법

> [마크다운 문법 공식 문서](https://daringfireball.net/projects/markdown/syntax)

### | Philosophy

- 글을 쉽게 읽고, 쓰고, 편집할 수 있도록 하는 것

### | Inline HTML

- 블록 수준 HTML 태그는 주변 내용과 빈 줄로 구분해야 함.
- 시작 태그와 종료 태그는 탭이나 공백으로 들여쓰기하지 않아야 함.
- 블록 태그 안에는 마크다운 문법이 적용되지 않음.

### | Automatic Escaping for Special Characters

- HTML에서는 <랑 & 같은 문자를 원래의 의미대로 쓰기 위해서는 &lt;, &amp; 같은 식으로 이스케이프를 해야 함.
- 마크다운에서는 자동으로 처리

```markdown
AT&T → AT&amp;T

4 < 5 → 4 &lt; 5
```

- 코드 블록이나 코드 스팬 안에서는 <와 &를 항상 자동으로 이스케이프하기 때문에 HTML 코드 예시를 적을 때도 편하게 쓸 수 있음.

## **Header**

### | Setext-Style

- 텍스트 아래에 밑줄을 그어서 표현
- =은 H1, -는 H2

```
This is an H1
=============

This is an H2
-------------
```

### | Atx-style

- 줄 맨 앞에 #를 붙여서 표현
- 1~6까지의 헤더 레벨

```markdown
# H1

## H2

###### H6
```

- 선택적으로, Atx-Style에서는 줄 끝에 #를 닫는 용도로 추가 가능하지만 없어도 무방
- 헤더 레벨은 맨 앞의 # 개수로 결정되기 때문에, 닫는 용도의 #는 맨 앞의 # 개수와 달라도 됨.

```
# H1 #

## H2 ##

### H3 ############
```

## **Blockquotes (인용문)**

- email-style의 > 기호 사용
- 보기 좋게 작성하기 위해 문장을 줄바꿈한 후, 각 줄 앞에 >를 붙이는 것이 좋음.

```markdown
> 두개의 문단으로 구성된
> 인용문

> 첫 줄에만
> 붙여도
> 인용문으로 인식

> 인용문
>
> > 중첩은
>
> > > 이런 식으로 작성

> 인용문 안에
>
> # 헤더를 넣거나
>
> 1. 리스트
>    코드 블럭 등 넣을 수 있음.
```

## **Lists**

- 순서 있는 리스트(번호), 순서 없는 리스트(글머리 기호) 사용 가능
- 보통 왼쪽에 붙여 쓰지만, 최대 3칸까지는 들여쓰기가 가능하며, 마커 뒤에는 공백 또는 탭이 반드시 있어야 함.

### | 순서 없는 리스트

- 글머리 기호는 \*, +, - 중 아무거나 사용 가능하며, 동일한 동작함.

```
* 사과

+ 귤

- 바나나
```

### | 순서 있는 리스트(번호)

- 숫자+.을 사용
- 실제로 어떤 숫자를 사용해도 HTML 출력에는 영향 없지만 1번부터 시작하는 것을 권장함.
- 아래의 예시들이 생성하는 HTML은 마지막 예시와 같음.

```markdown
1. 사과
2. 귤
3. 바나나

4. 사과
5. 귤
6. 바나나
```

```html
<ol>
  <li>사과</li>
  <li>귤</li>
  <li>바나나</li>
</ol>
```

### | 보기 좋게 리스트 작성

- 항목을 여러 줄로 작성할 때 보기 좋게 하려면 두 번째 줄부터 들여쓰기를 하면 됨.

```markdown
- 보기 좋게
  리스트 작성하기
```

### | 리스트 항목 사이 빈 줄 있을 경우

- HTML에서는 \<p> 태그로 감싸짐.

```markdown
- Bird

- Magic
```

위의 것이 아래처럼 <p>태그로 감싸짐.

```html
<ul>
  <li><p>Bird</p></li>
  <li><p>Magic</p></li>
</ul>
```

### | 여러 문단으로 구성된 항목

```markdown
1. 한 항목에 여러 문단을 넣고 싶다면?

   space 4번이나 tab 1번 해야한다.
```

```markdown
- 이거는 문단 두개 예시이다.

      이건 두 번째 문단이다. 제일 첫번째

  줄만 들여쓰기를 해도 되긴 한다.
```

### | 리스트 안에 인용문

```markdown
- 리스트 안에
  > 인용문을 넣을 경우 들여쓰기 해야 한다.
```

### | 리스트 안에 코드 블럭

```markdown
- 코드 블럭 포함된 리스트는 space 8번이나 탭 2번을 해야한다
  <코드코드코드>
```

### | 의도치 않게 순서 있는 리스트가 되는 경우

- 숫자 + . + 공백 으로 시작하면 리스트로 인식될 수 있으니, . 앞에 \를 붙여 방지 가능

```markdown
2002. 월드컵 4강
```

## **Code Blocks (코드 블록)**

- 코드 블록은 일반 텍스트와 달리 들여쓰기(공백 4칸 또는 탭 1칸)를 하면 \<pre>\<code> 태그로 감싸진 코드 블록으로 처리

```markdown
This is a normal paragraph:

    This is a code block.
```

->

```html
<p>This is a normal paragraph:</p>

<pre><code>This is a code block.
</code></pre>
```

### | 들여쓰기 제거

- 코드 블록의 각 줄에서 4개의 space 또는 1개의 탭이 제거된다.

```markdown
tell application "Foo"
beep
end tell
```

->

```html
<p>Here is an example of AppleScript:</p>

<pre><code>tell application "Foo"
    beep
end tell
</code></pre>
```

### | 코드 블록 종료

- 코드 블록은 들여쓰기가 없는 줄이 나오거나 문서의 끝에 도달할 때까지 계속됨.

### 코드 블록 내 HTML 엔티티 자동 변환

- 코드 블록 내에서는 &, <, > 등의 특수문자가 자동으로 HTML 엔티티로 변환

```markdown
<div class="footer">&copy; 2004 Foo Corporation</div>
```

```html
<pre><code>&lt;div class="footer"&gt;
    &amp;copy; 2004 Foo Corporation
&lt;/div&gt;
</code></pre>
```

### | 코드 블록 내, 마크다운 문법 비처리

- 코드 블록 내에서는 마크다운 문법이 처리되지 않음.
- 예를 들어, 별표(\*)는 코드 블록 내에서 단순한 별표로 처리됨. 따라서 마크다운 문법에 대해 이야기할 때도 코드 블록을 사용하기가 쉬움.

## **Horizontal Rules (수평선)**

- \*\*\*, ---, \_\_\_ 중 하나를 한 줄에만 작성하면 \<hr /> 태그로 만들 수 있음.
- 원한다면, -이나 \* 사이에 공백 넣어도 됨.

```Markdown
* * *

***

*****

- - -

---------------------
```

---

## **Links (링크)**

### | Inline link (인라인 링크)

```Markdown
This is [an example](http://example.com/ "Title") inline link.
[This link](http://example.net/) has no title attribute.
```

```html
<p>This is <a href="http://example.com/" title="Title">an example</a> inline link.</p>

<p><a href="http://example.net/">This link</a> has no title attribute.</p>
```

### | Reference-style links (참조 스타일 링크)

#### 기본 구조

- 두개의 대괄호 쌍을 사용하며, 그 안에 링크를 식별할 수 있도록 원하는 레이블을 넣음.

```markdown
This is [an example][id] reference-style link.
```

#### 형식 관련 디테일

- [ ]와 [ ] 사이에 space는 선택 사항

```markdown
This is [an example] [id] reference-style link.
```

- 문서 어디서든 다음과 같이 링크 레이블을 정의 가능

```markdown
[id]: http://example.com/ 'Optional Title Here'
```

**즉, 다음과 같은 형식이다.**

- 링크 식별자를 포함한 대괄호(왼쪽 여백에서 최대 세 칸까지 들여쓰기 가능);
- 그 뒤에 콜론(:);
- 그 뒤에 하나 이상의 공백(또는 탭);
- 그 다음엔 링크할 URL;
- 선택적으로, 링크에 대한 제목(title) 속성(큰따옴표, 작은따옴표, 또는 괄호로 둘러쌀 수 있음)을 추가.

- 다음 3가지 링크 정의는 동일함.

```markdown
[foo]: http://example.com/ 'Optional Title Here'
[foo]: http://example.com/ 'Optional Title Here'
[foo]: http://example.com/ 'Optional Title Here'
```

- 참고: Markdown.pl 1.0.1에는 링크 제목을 작은따옴표로 감싸면 작동하지 않는 알려진 버그가 있음.

- 링크 URL은 선택적으로 꺾쇠 괄호로 감쌀 수 있음.

```markdown
[id]: http://example.com/ 'Optional Title Here'
```

- 제목 속성은 다음 줄에 두고, 긴 URL의 경우 보기 좋게 들여쓰기나 여분의 공백 또는 탭 사용 가능

```markdown
[id]: http://example.com/longish/path/to/resource/here 'Optional Title Here'
```

- 링크 정의는 Markdown 처리 중에만 링크를 생성하는 데 사용되며, HTML 출력에서는 문서에서 제거됨.
- 링크 정의 이름은 문자, 숫자, 공백, 구두점으로 구성될 수 있으며, 대소문자를 구분하지 않음.

```markdown
# 이 두 개는 동일한 동작

[link text][a]
[link text][A]
```

```markdown
# 링크는 이렇게 정의함.

[Google]: http://google.com/
```

#### 암시적 링크 이름 (Implicit link names) 가능

- 링크 텍스트 자체가 이름으로 사용

```markdown
[Google][]

# 링크 정의

[Google]: http://google.com/
```

- 링크 이름에 공백이 포함될 수 있기 때문에, 이 단축 기능은 링크 텍스트가 여러 단어인 경우에도 작동

```markdown
Visit [Daring Fireball][] for more information.

# 링크 정의

[Daring Fireball]: http://daringfireball.net/
```

#### 링크 정의 배치

- 어디든 가능
- 각 문단 바로 뒤나 문서 맨 끝에 모든 링크 정의 모아둘 수 있음.

```markdown
# 참조 스타일 링크 예제

I get 10 times more traffic from [Google] [1] than from
[Yahoo] [2] or [MSN] [3].

[1]: http://google.com/ 'Google'
[2]: http://search.yahoo.com/ 'Yahoo Search'
[3]: http://search.msn.com/ 'MSN Search'

# 암시적 링크 이름 단축 문법 사용

I get 10 times more traffic from Google than from
```

```html
<!-- 위 두 예제는 다음과 같은 HTML 출력 생성 -->

<p>
  I get 10 times more traffic from <a href="http://google.com/" title="Google">Google</a> than from
  <a href="http://search.yahoo.com/" title="Yahoo Search">Yahoo</a>
  or <a href="http://search.msn.com/" title="MSN Search">MSN</a>.
</p>
```

```markdown
# 비교 위해 동일한 문단을 인라인 링크 스타일로 작성

I get 10 times more traffic from Google
than from Yahoo or
MSN.
```

#### 참조 스타일 링크 요점

- 참조 스타일 링크를 사용하면, 인라인 스타일, 순수 HTML보다 문서의 소스를 읽기 훨씬 쉬워짐.
- 참조 스타일 링크를 사용하면, 원본 문서가 브라우저에 렌더링된 최종 출력물과 훨씬 비슷해짐.

## **Emphasis (강조)**

- \*와 \_을 강조 표시 기호로 인식
- \*또는 \_ 하나로 감싸면 HTML의 \<em> 태그로 변환 -> 기울임체
- \*\* 또는 \_\_로 감싸면 HTML의 \<strong> 태그로 변환 -> 굵은 글씨

```
*single asterisks*
_single underscores_
**double asterisks**
__double underscores__
```

```html
<em>single asterisks</em>
<em>single underscores</em>
<strong>double asterisks</strong>
<strong>double underscores</strong>
```

- 단어 중간에도 사용 가능

```markdown
un*frigging*believable  
→ un<em>frigging</em>believable
```

- \*또는 \_앞뒤에 공백을 둘 경우, 강조 기호로 인식되지 않고 문자 그대로 출력
- 강조 기호로 인식되는 위치에서 실제 \*또는 \_를 문자 그대로 출력하려면 \\(백슬래시)를 이용해 이스케이프 처리

```
\*this text is surrounded by literal asterisks\*
→ *this text is surrounded by literal asterisks*
```

## **Code**

### | 코드 구문 강조

- 코드 조각을 나타내려면 백틱(backtick, `) 기호로 감싸기
- 일반 단락 안에서 코드 일부를 강조할 때 사용

  - Use the `printf()` function

  ```html
  <p>Use the <code>printf()</code> function.</p>
  ```

### | 실제 백틱 문자 포함

- 여러 개의 백틱 기호로 감싸기

  - ``There is a literal backtick (`) here.``

  ```html
  <p><code>There is a literal backtick (`) here.</code></p>
  ```

### | code span (코드 스팬) 양 끝에 백틱 표시 포함

- 앞쪽 또는 뒤쪽에 공백 포함 가능하기에, 코드 스팬의 시작이나 끝에 리터럴 백틱 표시 가능

  - A single backtick in a code span: `` ` ``

    A backtick-delimited string in a code span: `` `foo` ``

    ```html
    <p>A single backtick in a code span: <code>`</code></p>
    <p>A backtick-delimited string in a code span: <code>`foo`</code></p>
    ```

### | code span(코드 스팬)에서 문자 자동 변환

- 코드 스팬 내부에서는 앰퍼샌드(&)나 꺾쇠 괄호(< >) 등이
  자동으로 HTML 엔티티로 인코딩되어, HTML 태그 예시를 쉽게 포함 가능

  - Please don't use any `<blink>` tags.

  ```html
  <p>Please don't use any <code>&lt;blink&gt;</code> tags.</p>
  ```

### | HTML 엔티티 예시 포함

- HTML 엔티티 자체를 코드 스팬으로 감쌀 수 있음.

```html
`&#8212;` is the decimal-encoded equivalent of `&mdash;`.
```

```html
<p><code>&amp;#8212;</code> is the decimal-encoded equivalent of <code>&amp;mdash;</code>.</p>
```

## **Images**

- 이미지 문법은 링크 문법과 유사
- 인라인 스타일 / 참조 스타일

### | 인라인 스타일 문법

```markdown
![Alt text](/path/to/img.jpg)

![Alt text](/path/to/img.jpg 'Optional title')
```

### | 참조 스타일 문법

```markdown
![Alt text][id]

# 링크 정의

[id]: url/to/image 'Optional title attribute'
```

- 이 시점에서 아직 이미지 크기를 지정하는 마크다운 문법이 없기 때문에, 크기 지정을 하려면 HTML의 \<img> 태그를 사용해야 함.

---

## **Automatic Links (자동 링크)**

- URL과 이메일 주소를 위한 “자동” 링크를 만드는 단축 문법 지원
- URL이나 이메일 주소를 꺾쇠 (< >)로 감싸기

```markdown
<http://example.com/>
```

```html
<!-- 마크다운은 위 코드를 다음과 같이 변환  -->
<a href="http://example.com/">http://example.com</a>
```

- 이메일 주소의 자동 링크도 유사하게 작동하지만, Markdown은 주소 수집 스팸봇으로부터 주소를 어느 정도 숨기기 위해 무작위 십진수 및 16진수 엔티티 인코딩을 수행

```markdown
<address@example.com>
```

```html
<!-- 마크다운은 위를 아래와 비슷하게 변환 -->
<a
  href="&#x6D;&#x61;i&#x6C;&#x74;&#x6F;:&#x61;&#x64;&#x64;&#x72;&#x65;
&#115;&#115;&#64;&#101;&#120;&#x61;&#109;&#x70;&#x6C;e&#x2E;&#99;&#111;
&#109;"
  >&#x61;&#x64;&#x64;&#x72;&#x65;&#115;&#115;&#64;&#101;&#120;&#x61; &#109;&#x70;&#x6C;e&#x2E;&#99;&#111;&#109;</a
>
```

- 위 코드는 브라우저에서 “address@example.com”이라는 클릭 가능한 링크로 렌더링됨.
- (이런 엔티티 인코딩 기법은 많은 주소 수집 봇을 속일 수 있지만, 모든 봇을 속이진 못한다. 아무것도 하지 않는 것보다는 낫지만, 이렇게 게시된 주소도 결국에는 스팸을 받게 될 가능성이 있다.)

## **Backslash Escapes**

- 일반적으로 특별한 의미 갖는 문자를 문자 그대로 출력 위해 사용
- 예를 들어, 단어를 HTML \<em> 태그 대신 실제 별표(\*)로 감싸고 싶다면, 별표 앞에 역슬래시를 붙이면 됨.

```markdown
\*literal asterisks\*
```

```
# Markdown에서 이스케이프할 수 있는 문자

\ backslash
` backtick
- asterisk
_ underscore
{} curly braces
[] square brackets
() parentheses
# hash mark
- plus sign
* minus sign (hyphen)
. dot
! exclamation mark
```
