<div class="markdown-body labdoc-content"><div><h2 id="labdoc-header-0">实验一：写一个hello world小程序</h2>
<h4 id="-c-http-mooc-study-163-com-course-ustc-1000002006-info-mooc-">注：本课程为网易云课堂孟宁老师<a href="http://mooc.study.163.com/course/USTC-1000002006#/info" target="_blank">《软件工程：C编码实践篇》</a> 的配套实验与作业。请配合 MOOC 课程学习使用。</h4>
<h3 id="labdoc-header-1">实验要求</h3>
<p>写一个hello world小程序：</p>
<ul>
<li>在Linux命令行环境（<a href="https://www.shiyanlou.com/courses/122" target="_blank">实验楼</a>）使用C语言编写，编译后执行输出"Hello，World！"；</li>
<li>实验务必在linux命令行环境下完成，课程视频是在本地虚拟机上操作的，除了目录环境和作业提交方式不同外，基本的命令和编辑操作方式是一致的。</li>
</ul>
<h3 id="labdoc-header-2">实验过程参考</h3>
<ul>
<li>需要在<a href="https://github.com" target="_blank">github</a>或<a href="https://coding.net/register?key=db18cac3-5313-4559-b26b-805ec7ef1587" target="_blank">coding</a>(使用实验楼虚拟机的话请使用github版本库)平台上创建一个版本库，比如<a href="https://git.coding.net/mengning/cs122.git" target="_blank">https://git.coding.net/mengning/cs122.git</a> （这里cs122是演示范例用的版本库的名字）， <a href="https://coding.net/help/faq/git/git.html#git--git--codingnet" target="_blank">git参考</a></li>
<li>进入实验目录并创建实验一文件夹lab1</li>
</ul>
<pre><code class="hljs bash">shiyanlou:~/ $ <span class="hljs-built_in">cd</span> Code
shiyanlou:Code/ $ git <span class="hljs-built_in">clone</span> https://github.com/mengning/[your_git_repo].git
shiyanlou:Code/ $ <span class="hljs-built_in">cd</span> [your_git_repo]
shiyanlou:cs122/ (master) $ mkdir lab1
shiyanlou:cs122/ (master) $ <span class="hljs-built_in">cd</span> lab1
shiyanlou:lab1/ (master*) $ vi hello.c
</code></pre><ul>
<li>使用vi编辑hello.c文件</li>
</ul>
<pre><code class="hljs cpp"><span class="hljs-meta">#<span class="hljs-meta-keyword">include</span> <span class="hljs-meta-string">&lt;stdio.h&gt;</span></span>

<span class="hljs-function"><span class="hljs-keyword">int</span> <span class="hljs-title">main</span><span class="hljs-params">()</span>
</span>{
    <span class="hljs-built_in">printf</span>(<span class="hljs-string">"hello world!\n"</span>);
}
</code></pre><ul>
<li>编译执行hello程序</li>
</ul>
<pre><code class="hljs ruby"><span class="hljs-symbol">shiyanlou:</span>lab1/ (master*) $ ls
hello.c
<span class="hljs-symbol">shiyanlou:</span>lab1/ (master*) $ gcc -o hello hello.c
<span class="hljs-symbol">shiyanlou:</span>lab1/ (master*) $ ./hello             
hello world!
<span class="hljs-symbol">shiyanlou:</span>lab1/ (master*) $
</code></pre><ul>
<li>提交代码到版本库（注意不要使用视频中要求的打包文件提交作业）</li>
</ul>
<pre><code class="hljs ruby"><span class="hljs-symbol">shiyanlou:</span>lab1/ (master*) $ git add hello.c
<span class="hljs-symbol">shiyanlou:</span>lab1/ (master*) $ git commit -m <span class="hljs-string">"hello world"</span>
[master <span class="hljs-number">40425</span>fe] hello world
 <span class="hljs-number">1</span> file changed, <span class="hljs-number">7</span> insertions(+)
 create mode <span class="hljs-number">100644</span> lab1/hello.c
<span class="hljs-symbol">shiyanlou:</span>lab1/ (master*) $ git push
......
   <span class="hljs-number">5</span>f24b93..<span class="hljs-number">40425</span>fe  master -&gt; master
<span class="hljs-symbol">shiyanlou:</span>lab1/ (master*) $
</code></pre><h3 id="labdoc-header-3">实验报告要求</h3>
<p>完成实验报告并公开发表（公开可访问博客或实验楼的实验报告），具体要求如下：</p>
<ul>
<li>简述自己的实验的思路和具体过程；</li>
<li>引用实验中自己添加或修改的部分关键代码；</li>
<li>至少有一张实验关键代码截图，至少有一张实验运行结果截图；</li>
<li>将自己在实验中遇到疑惑和困难，以及自己的处理方法，实验心得等写入实验报告；</li>
<li>实验报告的最后做一个简要的实验总结；</li>
<li>重现实验的具体操作指南（参见下面的小节）＊［特别重要，评阅实验报告时要根据您的操作指南进行实验验证］</li>
<li>将实验报告的URL提交到<a href="http://mooc.study.163.com/course/USTC-1000002006" target="_blank">网易云课堂MOOC平台</a>，编辑成一个链接可以直接点击打开。</li>
</ul>
<h3 id="labdoc-header-4">测试自己的实验代码，复审自己的实验报告</h3>
<p>请务必确认您提交的实验报告中的实验代码可以直接进行如下操作,并将如下操作放入实验报告的显著位置便于报告评审</p>
<pre><code class="hljs bash">shiyanlou:~/ $ <span class="hljs-built_in">cd</span> Code
shiyanlou:Code/ $ git <span class="hljs-built_in">clone</span> https://github.com/[your_name]/[your_git_repo].git
shiyanlou:Code/ $ <span class="hljs-built_in">cd</span> [your_git_repo]/lab1
shiyanlou:lab1/ (master) $ gcc -o hello hello.c 
shiyanlou:lab1/ (master*) $ ./hello
hello world!
shiyanlou:lab1/ (master*) $ vi hello.c
</code></pre></div></div>