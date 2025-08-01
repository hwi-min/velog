<p>프로그래머스 SQL 고득점 Kit SELECT문 연습 문제입니다</p>
<h2 id="📌-문제-설명">📌 문제 설명</h2>
<blockquote>
<p>상세 설명: <a href="https://school.programmers.co.kr/learn/courses/30/lessons/131118">https://school.programmers.co.kr/learn/courses/30/lessons/131118</a></p>
</blockquote>
<ul>
<li>REST_INFO는 식당의 정보를 담은 테이블, REST_REVIEW는 식당의 리뷰 정보를 담은 테이블이다.</li>
<li>REST_INFO와 REST_REVIEW 테이블에서 서울에 위치한 식당들의 식당 ID, 식당 이름, 음식 종류, 즐겨찾기수, 주소, 리뷰 평균 점수를 조회하는 쿼리를 작성해야한다.</li>
<li>리뷰 평균 점수는 소수점 세번째 자리에서 반올림해야한다.</li>
<li>결과는 평균점수를 기준으로 내림차순 정렬, 2순위는 즐겨찾기수를 기준으로 정렬해야 한다.
<img alt="" src="https://velog.velcdn.com/images/hwi_min/post/40a20db3-42bf-4373-82b0-f64d00c2e8aa/image.png" /><br />

</li>
</ul>
<h2 id="📌-문제-풀이">📌 문제 풀이</h2>
<pre><code class="language-sql">SELECT i.REST_ID, REST_NAME, FOOD_TYPE, FAVORITES, ADDRESS, ROUND(AVG(REVIEW_SCORE),2) as SCORE
FROM REST_INFO as i, REST_REVIEW as r
WHERE i.REST_ID = r.REST_ID AND ADDRESS like &quot;서울%&quot;
GROUP BY REST_ID
ORDER BY SCORE desc, FAVORITES desc</code></pre>
<ol>
<li><p><strong>FROM</strong>
REST_INFO를 i로, REST_REVIEW를 r로 지칭하기로 하고, 이 두 테이블에서 데이터를 가져온다.</p>
</li>
<li><p><strong>WHERE</strong>
REST_INFO의 REST_ID가 REST_REVEIW의 REST_ID가 같고, 주소가 서울로 시작하는 데이터만 추출해 온다.</p>
</li>
<li><p><strong>GROUP BY</strong>
그 데이터들을 REST_ID를 기준으로 그룹을 만든다.</p>
</li>
<li><p><strong>SELECT</strong>
레스토랑의 ID, 이름, 음식 종류, 즐겨찾기 수, 주소를 가져오고, 리뷰 점수의 평균을 내주기 위해 avg 사용후 round와 ,2를 사용해 소수점 둘째자리까지만 표현할 수 있도록 조정해서 SCORE이라고 표시한다.</p>
</li>
<li><p><strong>ORDER BY</strong>
1순위인 SCORE의 내림차순을 위해 SCORE desc, 2순위인 FAVORITES 기준 내림차순을 위해 FAVORITES desc로 작성한다. </p>
</li>
</ol>
<ul>
<li>출력 결과
<img alt="" src="https://velog.velcdn.com/images/hwi_min/post/10c6e973-26c0-47ac-885d-55e70fd9b104/image.png" /></li>
</ul>