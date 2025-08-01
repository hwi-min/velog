<p>프로그래머스 SQL 고득점 Kit SELECT문 연습 문제입니다.</p>
<h2 id="📌-문제-설명">📌 문제 설명</h2>
<blockquote>
<p>상세 설명: <a href="https://school.programmers.co.kr/learn/courses/30/lessons/131537">https://school.programmers.co.kr/learn/courses/30/lessons/131537</a></p>
</blockquote>
<ul>
<li>ONLINE_SALE은 의류 쇼핑몰의 온라인 상품 판매 정보, OFFLINE_SALE은 의류 쇼핑몰의 오프라인 상품 판매 정보를 담은 테이블이다.</li>
<li>두 테이블은 모두 동일한 날짜, (회원ID), 상품ID 조합에 대해서는 하나의 판매 데이터만 존재한다.</li>
<li>두 테이블에서 2022년 3월의 오프라인/온라인 상품 판매 데이터의 판매 날짜, 상품ID, 유저ID, 판매량을 출력하는 쿼리를 작성해야 한다. </li>
<li>oFFLINE_SALE 테이블의 판매 데이터의 USER_ID값은 NULL로 표시해야하며, 결과는 판매일 기준 오름차순, 2순위 판매일, 3순위 상품ID, 4순위 유저ID 오름차순으로 정렬해야 한다.
<img alt="" src="https://velog.velcdn.com/images/hwi_min/post/8f26d5ae-2089-485e-adf0-522baed13e55/image.png" /></li>
</ul>
<h2 id="📌-문제-풀이">📌 문제 풀이</h2>
<pre><code class="language-sql"># online_sale 테이블
SELECT date_format(SALES_DATE, &quot;%Y-%m-%d&quot;) as SALES_DATE, PRODUCT_ID, USER_ID, SALES_AMOUNT
FROM ONLINE_SALE
WHERE date_format(SALES_DATE, &quot;%Y-%m-%d&quot;) like '2022-03%'
UNION
# offline_sale 테이블
SELECT date_format(SALES_DATE, &quot;%Y-%m-%d&quot;) as SALES_DATE, PRODUCT_ID, null as USER_ID, SALES_AMOUNT
FROM OFFLINE_SALE
WHERE date_format(SALES_DATE, &quot;%Y-%m-%d&quot;) like '2022-03%'

ORDER BY SALES_DATE, PRODUCT_ID, USER_ID;</code></pre>
<ol>
<li>online_sale 테이블</li>
</ol>
<ul>
<li>online_sale테이블에서(FROM) sales_date가 2022-03으로 시작하는 데이터만 추출하여(WHERE) 그것의 sales_date, product_id, user_id, sales_amount를 추출(SELECT)한다.</li>
</ul>
<ol start="2">
<li>offline_sale 테이블</li>
</ol>
<ul>
<li>offline_sale테이블에서(FROM) sales_date가 2022-03으로 시작하는 데이터만 추출하여(WHERE) 그것의 sales_date, product_id, sales_amount를 불러오고, 이 테이블에 없는 user_id의 값들은 null값으로 채워 그것을 user_id로 사용(SELECT)한다.</li>
</ul>
<ol start="3">
<li><p>UNION
오프라인과 온라인 상품 판매 내역에서 원하는 데이터만 각자 가져왔으니, 이 데이터들을 합치기 위해 UNION을 사용한다. </p>
</li>
<li><p>ORDER BY
1순위 판매일 2순위 상품 아이디, 3순위 사용자 아이디이고 모두 오름차순이기 떄문에 디폴트값인 ASC는 위와같이 생략해도 되고, 명시해도 된다. 
<img alt="" src="https://velog.velcdn.com/images/hwi_min/post/49031d6a-7bab-44cf-9f6c-80bf60db287f/image.png" /></p>
</li>
</ol>
<br />

<h3 id="💡-union--union-all">💡 UNION &amp; UNION ALL</h3>
<p><strong>UNION</strong></p>
<ul>
<li>여러 쿼리문을 합쳐서 하나의 쿼리로 만들어준다.</li>
<li>중복된 값이 있으면, 중복된 값을 제거한 뒤 보여준다.</li>
<li>중복된 값을 제거하는 연산이 필요하기 때문에 UNION ALL과 비교했을 때 비교적 속도가 느리다.</li>
</ul>
<p><strong>UNION ALL</strong></p>
<ul>
<li>UNION과 마찬가지로 여러 쿼리문을 합쳐서 하나의 쿼리로 만들어준다.</li>
<li>중복된 값을 제거하는 연산 없이 모두 보여준다.</li>
<li>중복된 값을 제거하는 연산이 없어 UNION보다 비교적 빠르다.</li>
</ul>
<p><strong>유의사항</strong></p>
<ul>
<li>컬럼명 동일</li>
<li>컬럼별 데이터 타입 동일</li>
<li>출력한 컬럼의 개수 동일</li>
</ul>
<p><strong>사용 예시 비교</strong>
다음과 같은 테이블 name_woman이 있다고 가정하자.</p>
<ul>
<li><table>
<thead>
<tr>
<th align="center">ID</th>
<th align="left">NAME</th>
</tr>
</thead>
<tbody><tr>
<td align="center">1</td>
<td align="left">김가영</td>
</tr>
<tr>
<td align="center">2</td>
<td align="left">김다인</td>
</tr>
<tr>
<td align="center">3</td>
<td align="left">김지민</td>
</tr>
<tr>
<td align="center">4</td>
<td align="left">박은정</td>
</tr>
</tbody></table>
</li>
</ul>
<p>name_man이 있다고 가정하자.</p>
<ul>
<li><table>
<thead>
<tr>
<th align="center">ID</th>
<th align="left">NAME</th>
</tr>
</thead>
<tbody><tr>
<td align="center">1</td>
<td align="left">김지민</td>
</tr>
<tr>
<td align="center">2</td>
<td align="left">김민석</td>
</tr>
<tr>
<td align="center">3</td>
<td align="left">박태정</td>
</tr>
<tr>
<td align="center">4</td>
<td align="left">최현석</td>
</tr>
</tbody></table>
</li>
</ul>
<p><strong>남성과 여성의 이름을 중복값은 빼고 추출한다면</strong></p>
<pre><code class="language-sql">SELECT name FROM name_woman
UNION
SELECT name FROM name_man</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/hwi_min/post/84bbb442-3192-46c2-bc8c-467c14df0359/image.png" /></p>
<ul>
<li>중복값인 '김지민'은 한 번만 출력됨<br />

</li>
</ul>
<p><strong>남성과 여성의 이름은 중복값 포함하여 모두 추출한다면</strong></p>
<pre><code class="language-sql">SELECT name FROM name_woman
UNION ALL 
SELECT name FROM name_man</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/hwi_min/post/933c3cc9-570a-46b1-8805-fbee51f4807e/image.png" /></p>
<ul>
<li>중복값인 '김지민'이 두 번 다 출력됨</li>
</ul>