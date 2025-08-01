<h2 id="1-가져오고-싶은-소스코드가-담긴-repository를-clone">1. 가져오고 싶은 소스코드가 담긴 Repository를 clone</h2>
<ul>
<li><p>소스코드를 일시적으로 저장할 pc의 로컬 폴더 생성</p>
</li>
<li><p>(Mac기준) Terminal창을 열고 가져오고 싶은 소스코드가 담긴 Repository의 소스코드를 clone</p>
<ul>
<li><p>팀 프로젝트의 깃허브 주소가 <a href="https://github.com/team_prj">https://github.com/team_prj</a>,</p>
</li>
<li><p>소스코드를 일시적으로 저장할 pc의 포컬 폴더의 이름을 localFile이라고 했을 때</p>
<p>git clone --mirror &lt;소스코드가 담긴 repository주소&gt; &lt;생성한 pc 로컬 폴더&gt;
  git clone -- mirror <a href="https://github.com/team_prj">https://github.com/team_prj</a> localFile</p>
</li>
</ul>
</li>
</ul>
<h2 id="2-내-github에-새로운-repository-생성">2. 내 GitHub에 새로운 Repository 생성</h2>
<ul>
<li><p>소스코드를 옮겨 담고 싶은 새로운 Repository를 생성</p>
<ul>
<li>push시 충돌을 피하기 위해 완전히 비어있는 repository로 생성하는 것을 추천한다. (Readme 등의 파일도 없게)</li>
<li>data_team_prj라는 이름으로 생성할 경우 https//github.com/깃허브ID/data_team_prj 로 주소가 생성이 됨</li>
</ul>
</li>
<li><p>(Mac기준) Terminal창을 열고 소스코드를 일시 저장해 둔 로컬 폴더(localFile)로 이동한다.</p>
<pre><code># 로컬 파일의 위치에 따라 해당 멍령어는 달라질 수 있으나, 
# cd 혹은 ..cd를 사용해 해당 폴더로 이동하면 됨

cd localFile</code></pre><p>  git remote set-url origin &lt;내 깃허브 주소&gt;.git
  git remote set-url origin <a href="https://github.com/%EA%B9%83%ED%97%88%EB%B8%8CID/data_team_prj.git">https://github.com/깃허브ID/data_team_prj.git</a>
  git push</p>
</li>
</ul>