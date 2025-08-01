<p>프로그래머스 SQL 고득점 Kit SELECT문 연습 문제입니다.</p>
<h2 id="📌-문제-설명">📌 문제 설명</h2>
<blockquote>
<p>상세 설명: <a href="https://school.programmers.co.kr/learn/courses/30/lessons/164673">https://school.programmers.co.kr/learn/courses/30/lessons/164673</a></p>
</blockquote>
<ul>
<li>USED_GOODS_BOARD는 중고거래 게시판의 정보, USED_GOODS_REPLY는 게시판내 첨부파일의 정보를 담은 테이블이다.</li>
<li>2022년 10월에 작성된 게시글의 제목, 게시글 ID, 댓글 ID, 댓글 작성자 ID, 댓글 내용, 댓글 작성일을 조회하는 SQL문을 조회하는 쿼리를 작성해야 한다.</li>
<li>이때, 결과는 댓글 작성일 기준으로 오름차순으로 정렬하고 만약 댓글 작성일이 같다면 게시글 제목을 기준으로 오름차순 한다.<br />


</li>
</ul>
<h2 id="📌-문제-풀이">📌 문제 풀이</h2>
<pre><code class="language-sql">SELECT b.title as title, b.board_id as board_id, reply_id, r.writer_id as writer_id, r.contents as contents, date_format(r.created_date, &quot;%Y-%m-%d&quot;) as created_date
FROM used_goods_board as b, used_goods_reply as r
WHERE b.board_id = r.board_id AND b.created_date BETWEEN '2022-10-01' AND '2022-10-31'
ORDER BY r.created_date, b.title;</code></pre>
<ol>
<li><p><strong>FROM</strong>
USED_GOODS_BOARD의 이름이 너무 길기때문에 alias를 사용해 b로 지칭한다. USED_GOODS_REPLY역시 r로 지칭한다.</p>
</li>
<li><p><strong>WHERE</strong></p>
</li>
</ol>
<p><strong>USED_GOODS_BOARD의 게시글 아이디와, USED_GOODS_REPLY의 게시글 아이디가 같은 경우</strong>에 데이터를 가져온다. 그리고 동시에 게시글이 생성된 날짜가 2022-10-01부터 2022-10-31일 사이인 게시글을 추출해야하기 때문에 <strong>BETWEEN</strong>을 활용하여 그 기간 내에 생성된 데이터만 추출하는 조건을 작성한다.</p>
<ol start="3">
<li><p><strong>SELECT</strong>
조건에 명시된대로 컬럼을 가져올건데, 두 테이블에 중복되는 컬럼명이 있을시에는 <strong>어떤 테이블의 컬럼인지 정확히 명시</strong>해 주어야하기때문에 r.created_date 같이 <strong>alias.column name</strong>의 형식으로 작성한다. 이때 결과 컬럼 역시 내가 불러온대로 r.created_date로 나오기 때문에 원하는 결과 'created_date'로만 나오게 하기 위해서는 <strong>r.created_date as created_date</strong>로 작성해주어야 한다. 이렇게 작성한 뒤 결과를 출력했더니 결과 값이 '2022-10-02'가 아닌 '2022-10-02 00:00:00'으로 출력되어 오답이 떴다. 그래서 date_format을 사용하여 '2022-10-02'만 출력값이 될 수 있도록 수정했다.</p>
</li>
<li><p><strong>ORDER BY</strong>
가져온 데이터들을 <strong>답글이 생성된 날짜를 기준으로 오름차순 정렬</strong>, 그리고 2순위로 <strong>게시글의 타이틀 기준으로 오름차순 정렬</strong>이기 때문에 r.created_date, b.title; 로 작성하여 준다. 이때, 오름차순은 디폴트 값이므로 생략해도 되고, ASC를 뒤에 명시해 주어도 된다. </p>
<br /></li>
</ol>
<ul>
<li>출력 결과
<img alt="" src="https://velog.velcdn.com/images/hwi_min/post/2d3cc67c-64c1-453a-90e2-64014f12fae4/image.png" /></li>
</ul>