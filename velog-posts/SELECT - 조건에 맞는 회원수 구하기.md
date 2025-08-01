<p>프로그래머스 SQL 고득점 Kit SELECT문 연습 문제 입니다.</p>
<h2 id="📌-문제-설명">📌 문제 설명</h2>
<blockquote>
<p>상세 설명: <a href="https://school.programmers.co.kr/learn/courses/30/lessons/131535">https://school.programmers.co.kr/learn/courses/30/lessons/131535</a></p>
</blockquote>
<ul>
<li>USER_INFO는 의류 쇼핑물에 가입한 회원정보를 담은 테이블이다.</li>
<li>2021년에 가입한 회원 중 나이가 20세이상 29세 이하인 회원이 몇 명인지 출력해야 한다.
<img alt="" src="https://velog.velcdn.com/images/hwi_min/post/c12491d5-04b7-4316-9dc9-1ce18e2a30a6/image.png" /><br />

</li>
</ul>
<h2 id="📌-문제-풀이">📌 문제 풀이</h2>
<pre><code class="language-sql">SELECT count(*) as USERS
FROM USER_INFO
WHERE (age BETWEEN 20 AND 29) AND date_format(JOINED, &quot;%Y-%m-%d&quot;) like '2021%'</code></pre>
<ol>
<li><p><strong>FROM</strong>
USER_INFO에서 정보를 가져온다.</p>
</li>
<li><p><strong>WHERE</strong>
나이가 20세에서 29세 사이인 데이터만 가져오기 때문에 BETWEEN 20 AND 29로 작성한다. 그리고 동시에 가입일이 2021년이여야하기 때문에 date_format으로 패턴을 맞춰주고 그것이 '2021'으로 시작하면 데이터를 가져오기로 한다.</p>
</li>
<li><p><strong>SELECT</strong>
이때 추출된 데이터들의 개수를 세기 위해 count(*)를 사용하고 이때 *는 모든 로우를 말한다. 이때 그대로 가져오면 컬럼이 'count(*)'로 표시되므로 USERS로 표시될 수 있도록 as USERS를 추가해준다.</p>
</li>
</ol>
<ul>
<li>출력 결과
<img alt="" src="https://velog.velcdn.com/images/hwi_min/post/6f2a3ad9-9874-4bd2-a2c2-8d57b9822aa8/image.png" /></li>
</ul>