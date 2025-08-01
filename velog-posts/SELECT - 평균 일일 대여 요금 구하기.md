<p>프로그래머스 SQL 고득점 Kit SELECT문 연습 문제 입니다.</p>
<h3 id="📌-문제-설명">📌 문제 설명</h3>
<blockquote>
<p>상세 설명: <a href="https://school.programmers.co.kr/learn/courses/30/lessons/151136">https://school.programmers.co.kr/learn/courses/30/lessons/151136</a></p>
</blockquote>
<ul>
<li>자동차 대여 회사에서 대여중인 자동차의 정보를 담은 테이블 CAR_RENTAL_COMPANY_CAR</li>
<li>CAR_RENTAL_COMPANY_CAR는 CAR_ID, CAR_TYPE, DAILY_FEE, OPTIONS로 구성되어 있다.</li>
<li>자동차 종류(CAR_TYPE)는 'SUV', '세단', '승합차', '트럭', '리무진'으로 구성되어 있다.</li>
<li>이때, 자동차의 종류가 'SUV'인 자동차의 평균 일일 대여 요금을 소수 첫 번째 자리에서 반올림 후 AVERAGE_FEE로 지정하여 출력하는 SQL문을 작성해야한다.</li>
</ul>
<h3 id="📌-문제-풀이">📌 문제 풀이</h3>
<p>SELECT문 중에서도 가장 난이도가 낮고 기본적인 문제이기 때문에 큰 문제는 없었다.
일반적으로 SQL은 대소문자를 구분하지 않기 때문에 모두 대문자로, 모두 소문자로 작성하여도 되나, 나는 집계 함수 부분을 소문자로 처리하였다. </p>
<pre><code class="language-sql">SELECT round(avg(DAILY_FEE)) as AVERAGE_FEE
FROM CAR_RENTAL_COMPANY_CAR
WHERE CAR_TYPE = &quot;SUV&quot;;</code></pre>
<ol>
<li><p>SQL의 가장 기본적인 코드 작성 순서는 <strong>SELECT &gt; FROM &gt; WHERE</strong> 순이다. 나중에 여러 조건을 추가시키면, HAVING, GROUP BY 등 추가적으로 등장하지만, 지금과 같이 단순한 코드에서는 SELECT, FROM, WHERE만으로도 충분히 풀이할 수 있다.</p>
</li>
<li><p><strong>FROM 문</strong>
FROM은 영어 뜻 그대로 ~에서 라는 의미정도로 보면 될 것 같다. CAR_RENTAL_COMPANY_CAR 테이블에서 정보를 가져올 것이기 때문에 위와 같이 작성한다. </p>
</li>
<li><p><strong>WHERE 문</strong>
WHERE에서는 문제가 CAR_TYPE이 'SUV'인 데이터에 대한 정보를 추출하고 싶어하기 때문에 CAR_TYPE = 'SUV'로 지정해 주었다. 여기서 주의해야하는 것은 <strong>SQL에서 비교 연산자는 우리가 흔히 아는 '==' 대신에 '='를 사용해야 한다는 것</strong>이다. 덧붙여 SQL에서의 ';'는 쿼리의 끝을 나타낸다. </p>
</li>
<li><p>*<em>SELECT문 *</em>
우리는 1.(CAR_TYPE이 'SUV'인) DAILY_FEE의 평균을 구해 2. 소수 첫 번째 자리에서 반올림 하여 3. AVERAGE_FEE로 선언할 것이다. 따라서 평균을 계산해주는 SQL의 집계함수 avg를 이용해 해당되는 DAILY_FEE의 평균을 구한 뒤, 소수 첫 번째 자리에서 반올림하는 함수 round를 사용한 뒤 as를 이용해 AVERAGE_FEE로 정의해 준다.</p>
</li>
</ol>