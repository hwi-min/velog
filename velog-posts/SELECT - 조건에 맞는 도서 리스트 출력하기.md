<p>프로그래머스 SQL 고득점 Kit SELECT문 연습 문제 입니다.</p>
<h2 id="📌-문제-설명">📌 문제 설명</h2>
<blockquote>
<p>상세 설명: <a href="https://school.programmers.co.kr/learn/courses/30/lessons/144853">https://school.programmers.co.kr/learn/courses/30/lessons/144853</a></p>
</blockquote>
<ul>
<li>BOOK테이블은 한 서점에서 판매중인 도서들의 도서 정보를 담은 테이블이다.</li>
<li>BOOK테이블에서 CATEGORY가 '인문'이고 PUBLISHED_DATE가 2021년인 도서 리스트를 찾아야 한다.</li>
<li>해당하는 책의 BOOK_ID, PUBLISHED_DATE를 출력해야 한다.</li>
<li>결과는 출판일을 기준으로 오름차순 정렬한다.<br />

</li>
</ul>
<h2 id="📌-문제-풀이">📌 문제 풀이</h2>
<p>기본 SELECT &gt; FROM &gt; WHERE에 ORDER BY가 추가된 문제이다. 일반적으로 SQL은 대소문자를 구분하지 않기 때문에 모두 대문자로, 모두 소문자로 작성하여도 되나,집계함수 및 연산자(like) 등을 소문자로 처리하였다.</p>
<pre><code class="language-sql">SELECT BOOK_ID, date_format(PUBLISHED_DATE, &quot;%Y-%m-%d&quot;) AS PUBLISHED_DATE
FROM BOOK
WHERE PUBLISHED_DATE like '2021%' AND CATEGORY like '인문'
ORDER BY PUBLISHED_DATE ASC;</code></pre>
<ol>
<li><strong>FROM BOOK</strong>: 말 그대로 BOOK 테이블에서 데이터를 추출한다.</li>
<li><strong>WHERE 문</strong>
CATEGORY는 모든 요소들이 '인문', '경제' ... 등으로 작성되어 있기 때문에 '인문'과 문자열이 일치하는 경우에 추출하겠다는 의미로 GATEGORY like '인문'이라고 작성하면 된다. 하지만 PUBLISHED_DATE는 '2021-01-01'과 같이 작성이 되어 있기 때문에, 2021이 가장 앞에 작성되어 있는 것을 2021년에 출판된 도서로 판단하고 이것을 추출해야한다. 이때 사용되는 것이 like 연산자와, %, _ 이다.</li>
</ol>
<ul>
<li>포스팅 뒷부분 💡 like 연산자 에서 추가적으로 설명한다.</li>
</ul>
<ol start="3">
<li><strong>ORDER BY 문</strong>
출판일을 기준으로 오름차순 정렬해야 하기 때문에 ORDER BY문에 PUBLISHED_DATE를 기준으로 오름차순 정리한다는 의미의 ASC를 작성해 준다.</li>
<li>SELECT 문
BOOK_ID, PUBLISHED_DATE를 출력해야하므로 BOOK_ID를 가져오고, PUBLISHED_DATE를 '년-월-일'의 형식으로 추출해야 하므로 date_format을 사용하여 PUBLISHED_DATE라는 이름으로 추출한다는 의미로 위와 같이 작성해야한다.</li>
</ol>
<ul>
<li>포스팅 뒤부분 💡 date_format 에서 추가적으로 설명한다. <br />

</li>
</ul>
<h3 id="💡-like-연산자">💡 like 연산자</h3>
<p>like 연산자는 문자열의 패턴을 검색하는 데 사용된다.
기본적인 공식은 다음과 같다.</p>
<pre><code class="language-sql">SELECT * 
FROM TABLE
WHERE COLUMN like 'PATTERN';</code></pre>
<p>이때, 패턴에서 활용되는 것이 <strong>%</strong>와 <strong>_</strong>이다. %는 모든 문자라는 의미이고, _는 한 글자라는 의미이다. 예시로 다음 패턴들을 활용해 보겠다.</p>
<pre><code class="language-sql">SELECT * 
FROM TABLE
WHERE COLUMN like '%2021%';</code></pre>
<ul>
<li>다음 코드에서는 시작이 2021의 앞 뒤에 어떤 문자가 와도 상관이 없고, 단지 2021이라는 문자열이 전체 문자열중에 포함되어 있으면 된다. 따라서 0002021abb도 추출되고, year2021-도 추출되는 것이다.<pre><code class="language-sql">SELECT *
FROM TABLE
WHERE COLUMN like '_2021_';</code></pre>
</li>
<li>다음 코드에서는 2021의 각 앞과 뒤에 한 글자가 존재한다는 의미이다. 따라서 120213, y20211도 추출되는 것이다.<pre><code class="language-sql">SELECT *
FROM TABLE
WHERE COLUMN like '_2021%';</code></pre>
</li>
<li>당연히 두가지를 혼용하여 사용해도 된다. 다음 코드는 앞에 한글자, 뒤에는 상관 없으므로 y2021-01-20, 22021year22 와 같은 문자열이 추출될 것이다.<br />

</li>
</ul>
<p><strong>우리는 시작이 2021이기만 하면 되기 때문에 where문을 다음과 같이 코드를 작성할 수 있다. 그리고 category는 '인문', '과학' 처럼 정확히 문자열과 일치해야 하므로 다음과 같이 패턴에 사용되는 %, _없이 표현할 수 있다. AND는 앞 뒤의 모든 조건을 만족해야 한다는 의미이다.</strong></p>
<pre><code class="language-sql">WHERE COLUMN like '2021%' AND CATEGORY like '인문';</code></pre>
<br />

<h3 id="💡-date_format">💡 date_format</h3>
<p>date_format(날짜, 형식)은 날짜를 지정한 형식으로 출력하게 한다. date_format에 사용되는 구분 기호를 다음과 같다.</p>
<ul>
<li>%Y : 4자리 년도</li>
<li>%y : 2자리 년도</li>
<li>%M : 영문, 긴 월 (ex.January)</li>
<li>%b : 영문, 짧은 월 (ex.Jan)</li>
<li>%W : 영문, 긴 요일 이름 (ex.Monday)</li>
<li>%a : 영문, 짧은 요일 이름 (ex.Mon)</li>
<li>%i : 분</li>
<li>%T : hh:mm:SS</li>
<li>%m : 숫자 월 (두 자리)</li>
<li>%c : 숫자 월 (한 자리는 한 자리)</li>
<li>%d : 일자 (두 자리)</li>
<li>%e : 일자 (한 자리는 한자리)</li>
<li>%I : 시간 (12시간)</li>
<li>%H : 시간 (24시간)</li>
<li>%r : hh:mm:SS AM, PM</li>
<li>%S : 초</li>
</ul>
<p>우리는 원래 형태인 '2021-01-01'과 같인 4자리 년도-두자리 숫자 월-두자리 일로 표현하는 것이 목표이므로 '%Y-%m-%d'로 패턴을 지정해주면 된다. 따라서 다음과 같이 코드를 작성할 수 있다.</p>
<pre><code class="language-sql">date_format(PUBLISHED_DATE, &quot;%Y-%m-%d&quot;)</code></pre>