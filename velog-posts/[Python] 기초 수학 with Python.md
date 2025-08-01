<h3 id="📌-약수와-소수">📌 약수와 소수</h3>
<h4 id="정의">정의</h4>
<p>약수 : 어떤 수를 나누어떨어지게 하는 수
소수 : 1과 자신만을 약수로 가지는 수(단, 1은 제외)
합성수 : 소수의 반대 개념. 1과 자신 외의 다른 약수를 가지는 수</p>
<h4 id="파이썬으로-구현하기">파이썬으로 구현하기</h4>
<ol>
<li><p>파이썬을 이용하여 사용자의 입력을 받아 숫자의 약수를 구해보자.</p>
<pre><code class="language-python">inputNumber = int(input(&quot;0보다 큰 정수 입력: &quot;))

for number in range(1, (inputNumber+1)):
   if inputNumber % number == 0:
       print('{}의 약수: {}'.format(inputNumber, number))</code></pre>
</li>
<li><p>파이썬을 이용하여 사용자가 입력한 숫자까지의 소수를 구해보자.</p>
<pre><code class="language-python">inputNumber = int(input(&quot;0보다 큰 정수 입력: &quot;))

for number in range(2, (inputNumber+1)):
   flag = True
   for n in range(2, number):
       if number % n == 0:
           flag = False
           break

   if (flag):
       print('{} : 소수'.format(number))
   else:
       print('{} : 합성수'.format(number))</code></pre>
</li>
</ol>
<h3 id="📌-소인수와-소인수분해">📌 소인수와 소인수분해</h3>
<h4 id="정의-1">정의</h4>
<p>소인수 : 소수와 인수(약수)를 합친 말로, 약수(인수) 중에서 소수인 숫자
소인수분해 : 1보다 큰 정수를 소인수의 곱으로 나타낸 것. 소인수분해를 통해 약수를 찾을 수 있음.</p>
<h4 id="파이썬으로-구현하기-1">파이썬으로 구현하기</h4>
<ol>
<li><p>파이썬을 이용해서 사용자가 입력한 수를 소인수분해 해보자.</p>
<pre><code class="language-python">inputNumber = int(input('1보다 큰 정수 입력: '))

n = 2
while n &lt;= inputNumber:
   if inputNumber % n == 0:
       print('소인수 : {}'.format(n))
       inputNumber /= n
   else:
       n += 1</code></pre>
<ol start="2">
<li>72에 x를 곱하면 y의 제곱이 된다고 할 때, x에 해당하는 가장 작은 정수를 구해보자.<pre><code class="language-python">inputNumber = int(input('1보다 큰 정수 입력: '))
</code></pre>
</li>
</ol>
<p>n = 2
searchNumbers = []</p>
<p>while n &lt;= inputNumber:
   if inputNumber % n == 0:</p>
<pre><code>   print('소인수 : {}'.format(n))
   if searchNumbers.count(n): #n의 개수 확인
       searchNumbers.append(n)

   elif searchNumbers.count(n) == 1:
       searchNumbers.remove(n) #이미 제곱형태이므로, 무시하기 위해 remove

   inputNumber /= n</code></pre><p>   else:</p>
<pre><code>   n += 1</code></pre><p>print('searchNumbers: {}'.format(searchNumbers))</p>
<pre><code></code></pre></li>
</ol>
<h3 id="📌-공약수와-최대공약수">📌 공약수와 최대공약수</h3>
<h4 id="정의-2">정의</h4>
<p>공약수 : 두 개 이상의 수에서 공통된 약수
최대공약수 : 공약수 중 가장 큰 수. 소수로 나눗셈하여 편리하게 최대공약수를 구할 수 있음.</p>
<h4 id="파이썬으로-구현하기-2">파이썬으로 구현하기</h4>
<ol>
<li><p>두개의 수를 입력하면 공약수와 최대공약수를 출력하는 코드를 작성해보자.
 단, 두 번째 입력하는 숫자가 첫 번째 입력하는 숫자보다 크다고 가정한다.</p>
<pre><code class="language-python">num1 = int(input('1보다 큰 정수 입력: '))
num2 = int(input('1보다 큰 정수 입력: '))
maxNum = 0

for i in range(1, (num1+1)):
   if num1 % i == 0 and num2 % i ==0:
     print('공약수: {}'.format(i))
     maxNum = i
print('최대공약수 : {}'.foramt(maxNum))
</code></pre>
</li>
<li><p>세 개의 수를 입력하면 공약수와 최대공약수를 출력하는 코드를 작성해보자.</p>
<pre><code class="language-python">num1 = int(input('1보다 큰 정수 입력: '))
num2 = int(input('1보다 큰 정수 입력: '))
num3  = int(input('1보다 큰 정수 입력: '))
maxNum = 0

for i in range(1, (num1+1)):
   if num1 % i == 0 and num2 % i ==0 and num3 % i ==0:
       print('공약수: {}'.format(i))
       maxNum = i

print('최대공약수 : {}'.format(maxNum))</code></pre>
</li>
</ol>
<h3 id="📌-공배수와-최소공배수">📌 공배수와 최소공배수</h3>
<h4 id="정의-3">정의</h4>
<p>공배수 : 두 개 이상의 수에서 공통된 배수
최소공배수 : 공배수 중 가장 작은 수</p>
<h4 id="파이썬으로-구현하기-3">파이썬으로 구현하기</h4>
<ol>
<li><p>두 개의 수를 입력하면 최소공배수를 출력하는 코드를 작성해보자.</p>
<pre><code class="language-python">num1 = int(input('1보다 큰 정수 입력: '))
num2 = int(input('1보다 큰 정수 입력: '))
maxNum = 0

for i in range(1, (num1+1)):
if num1 % i == 0 and num2 % i ==0:
   print('공약수: {}'.format(i))
   maxNum = i

print('최대공약수 : {}'.format(maxNum))

minNum = (num1 * num2) // maxNum
print('최소공배수 : {}'.format(minNum))</code></pre>
<ol start="2">
<li>세 개의 수를 입력하면 최소공배수를 출력하는 코드를 작성해보자.<pre><code class="language-python"># 1. 두 개의 수에 대한 최소공배수를 구한다
num1 = int(input('1보다 큰 정수 입력: '))
num2 = int(input('1보다 큰 정수 입력: '))
num3  = int(input('1보다 큰 정수 입력: '))
maxNum = 0
</code></pre>
</li>
</ol>
<p>for i in range(1, (num1+1)):
   if num1 % i == 0 and num2 % i ==0:</p>
<pre><code> print('공약수: {}'.format(i))
 maxNum = i</code></pre><p>print('최대공약수 : {}'.format(maxNum))</p>
<p>minNum = (num1 * num2) // maxNum
print('{}, {}의 최소공배수 : {}'.format(num1, num2, minNum))</p>
<h1 id="2-세-번째-수의-공배수를-구한다">2. 세 번째 수의 공배수를 구한다</h1>
<p>newNum = minNum
for i in range(1, (newNum+1)):
   if newNum % i == 0 and num3 % i == :</p>
<pre><code> maxNum = i</code></pre><p>print('최대공약수 : {}.format(maxNum))</p>
<p>minNum = (newNum * num3) // maxNum
print('{}, {}, {}의 최소공배수 : {}'.format(num1, num2, num3, minNum))</p>
<pre><code></code></pre></li>
<li><p>섬마을에 과일, 생선, 야채를 판매하는 배가 다음 주기로 입항한다고 할 때, 모든 배가 입항하는 날짜를 계산해 보자.</p>
<blockquote>
<p>과일 선박: 3일 주기 / 생선 선박: 4일 주기 / 야채 선박: 5일 주기</p>
</blockquote>
<pre><code class="language-python"> ship1 = 3; ship2 = 4; ship3 = 5;
 maxDay = 0

 for i in range(1, ship1+1)):
     if ship1 % i == 0 and ship2 % i == 0:
         maxDay = i

 print('최대공약수 : {}.format(maxDay))

 minDay = (ship1 * ship2) // maxDay
 print('{}, {}의 최소공배수 : {}'.format(ship1, ship2, minDay))

 newDay = minDay

 for i in range(1, (newDay+1)):
     if newDay %  i == 0 and ship3 % i == 0:
         maxDay = i

 print('최대공약수 : {}.format(maxDay))

 minDay = (newDay * ship3) // maxDay
 print('{}, {}, {}의 최소공배수 : {}'.format(ship1, ship2, ship3, minDay))</code></pre>
</li>
</ol>