<p>프로그래머스 SQL 고득점 Kit SELECT문 연습 문제 입니다.</p>
<h2 id="📌-문제-설명">📌 문제 설명</h2>
<blockquote>
<p>상세 설명: <a href="https://school.programmers.co.kr/learn/courses/30/lessons/131536">https://school.programmers.co.kr/learn/courses/30/lessons/131536</a></p>
</blockquote>
<ul>
<li>테이블 ONLINE_SALE은 의류 쇼핑몰의 온라인 상품 판매 정보를 담은 테이블이다.</li>
<li>ONLINE_SALE_ID(온라인 상품 판매 ID), USER_ID(회원 ID), PRODUCT_ID(상품 ID), SALES_AMOUNT(판매량), SALES_DATE(판매일)의 칼럼으로 구성되어 있다.</li>
<li>동일한 날짜, 회원 ID, 상품 ID조합에 대해서는 하나의 판매 데이터만 존재한다.</li>
<li>회원이 동일한 상품을 재구매한 데이터를 구하여, 재구매한 회원 ID와 재구매한 상품 ID를 출력해야한다.</li>
<li>결과는 회원 ID를 기준으로 오름차순 정렬하여야하고, 회원 ID가 같으면 상품 ID를 기준으로 내림차순 정렬해야 한다.<br />
## 📌 문제 풀이
```sql
SELECT USER_ID, PRODUCT_ID
FROM ONLINE_SALE
GROUP BY USER_ID, PRODUCT_ID
HAVING count(*) >= 2
ORDER BY USER_ID, PRODUCT_ID DESC;
```</li>
</ul>
<ol>
<li><strong>FROM ONLINE_SALE</strong> : ONLINE_SALE 테이블에서 데이터를 추출한다.</li>
<li><strong>GROUP BY 절</strong>
회원 ID(USER_ID)와 상품 ID(PRODUCT_ID)를 기준으로 그룹을 묶는다. 그래야 재구매한 회원에 대한 데이터 추출이 가능하기 때문이다.</li>
<li><strong>HAVING 절</strong>
재구매한 회원을 찾기 위해서 그룹화되어 있는 데이터들 사이에서 having절을 이용해 중복된 열의 개수를 센다. 이때 count 집계함수를 사용한다. 이때 <strong>count로 행의 개수를 구했을 때 2개 이상인 경우에는 재구매</strong>를 했다고 판단할 수 있다.</li>
<li><strong>SELECT 절</strong>
우리는 최종적으로 회원 ID(USER_ID)와 상품 ID(PRODUCT_ID)를 추출하고 싶기 때문에, USER_ID와 PRODUCT_ID를 SELECT절에 작성해 준다.</li>
<li><strong>ORDER BY 절</strong>
ORDER BY를 통해 오름차순과 내림차순으로 정렬 할 수 있는데, 우선 순위를 생각해 보아야 한다. <strong>1순위는 USER_ID의 오름차순</strong>이다. default가 ASCending(오름차순)이므로 ASC는 생략해도 된다. <strong>2순위는 PRODUCT_ID의 내림차순</strong>이다. 내림차순은 생략해서는 안되므로 PRODUCT_ID DESC이라고 작성을 해준다. 따라서 <strong>'USER_ID, PRODUCT_ID DESC'</strong>으로 작성하면 된다. </li>
</ol>
<br />

<h3 id="💡-sql-구문-순서">💡 SQL 구문 순서</h3>
<ul>
<li>SQL구문의 대표적은 순서는 다음과 같다.</li>
</ul>
<ol>
<li>SELECT 컬럼명 ------ <strong>(5): 추출된 데이터들을 조회한다.</strong></li>
<li>FROM 테이블명 ------ <strong>(1): 테이블을 가장 먼저 확인한다.</strong></li>
<li>WHERE 테이블 조건 -- <strong>(2): 테이블에서 조건에 맞는 데이터를 추출한다.</strong></li>
<li>GROUP BY 컬럼명 --- <strong>(3): 공통적인 데이터들끼리 묶어 그룹을 만든다.</strong></li>
<li>HAVING 그룹 조건 --- <strong>(4): 묶인 그룹 중, 주어진 조건에 맞는 그룹을 추출한다.</strong></li>
<li>ORDER BY 컬럼명 --- <strong>(6): 추출된 데이터들을 정렬한다.</strong></li>
</ol>