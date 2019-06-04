<div class="labdoc-content markdown-body"><h1 id="-bash-">高级bash脚本编程指南</h1>
<h1 id="bash-">bash介绍与入门</h1>
<h2 id="doc-section-0">一、实验说明</h2>
<h3 id="1-">1. 环境登录</h3>
<p>无需密码自动登录，系统用户名shiyanlou</p>
<p>若不小心登出后，直接刷新页面即可</p>
<h3 id="2-">2. 环境使用</h3>
<p>实验报告可以在个人主页中查看，其中含有每次实验的截图及笔记，以及每次实验的有效学习时间（指的是在实验桌面内操作的时间，如果没有操作，系统会记录为发呆时间）。这些都是您学习的真实性证明。</p>
<h3 id="3-">3. 课程来源</h3>
<p>基于杨春敏与黄毅的ABS译文制作，一本深入学习 shell 脚本艺术的书籍。原版链接：<a href="http://www.tldp.org/LDP/abs/html/" target="_blank">点这里</a></p>
<h3 id="4-">4.学前须知</h3>
<p>本课程将假设你已经完成学习<a href="https://www.shiyanlou.com/courses/1" target="_blank">linux基础入门</a>和<a href="https://www.shiyanlou.com/courses/2" target="_blank">vim编辑器</a>，如果你对学习这门课程的感到困难，你可以先完成前面两门基础课程的学习。</p>
<h2 id="doc-section-1">二、什么是Bash？</h2>
<h3 id="1-">1.简介</h3>
<p>Bash（GNU Bourne-Again Shell）是一个为GNU计划编写的Unix shell，它是许多Linux平台默认使用的shell。</p>
<p>shell是一个命令解释器，是介于操作系统内核与用户之间的一个绝缘层。准确地说，它也是能力很强的计算机语言，被称为解释性语言或脚本语言。它可以通过将系统调用、公共程序、工具和编译过的二进制程序”粘合“在一起来建立应用，这是大多数脚本语言的共同特征，所以有时候脚本语言又叫做“胶水语言”</p>
<p>事实上，所有的UNIX命令和工具再加上公共程序，对于shell脚本来说，都是可调用的。Shell脚本对于管理系统任务和其它的重复工作的例程来说，表现的非常好，根本不需要那些华而不实的成熟紧凑的编译型程序语言。</p>
<h3 id="2-bash-">2.为什么学Bash？</h3>
<p>对于任何想适当精通一些系统管理知识的人来说，掌握shell脚本知识都是最基本的，即使这些人可能并不打算真正的编写一些脚本。</p>
<h2 id="doc-section-2">三、初步练习</h2>
<h3 id="1-hello-world">1.Hello World</h3>
<p>Bash之Hello World</p>
<p><code>$ vim hello.sh</code></p>
<p>使用vim编辑hello.sh ，输入如下代码并保存：</p>
<pre><code class="hljs bash"> <span class="hljs-comment">#!/bin/bash</span>
 <span class="hljs-comment"># This is a comment</span>
 <span class="hljs-built_in">echo</span> Hello World
</code></pre><blockquote>
<ul>
<li><p><code>vim</code>中插入按<code>i</code></p>
</li>
<li><p>保存并退出换行按<code>esc</code>然后输入<code>:wq</code>再<code>enter</code></p>
</li>
<li><p><code>#!</code> 是说明 hello 这个文件的类型的，有点类似于 Windows 系统下用不同文件后缀来表示不同文件类型的意思（但不相同）。</p>
<p>Linux 系统根据 "#!" 及该字串后面的信息确定该文件的类型，可以通过 <code>man magic</code>命令 及 <code>/usr/share/magic</code> 文件来了解这方面的更多内容。</p>
<p>在 BASH 中 第一行的 "#!" 及后面的 <code>/bin/bash</code> 就表明该文件是一个 BASH 程序，需要由 /bin 目录下的 bash 程序来解释执行。BASH 这个程序一般是存放在 /bin 目录下，如果你的 Linux 系统比较特别，bash 也有可能被存放在 /sbin 、/usr/local/bin 、/usr/bin 、/usr/sbin 或 /usr/local/sbin 这样的目录下；如果还找不到，你可以用 <code>locate bash</code> <code>find / -name bash 2/dev/null</code> 或 <code>whereis bash</code> 这三个命令找出 bash 所在的位置；如果仍然找不到，那你可能需要自己动手安装一个 BASH 软件包了。</p>
</li>
</ul>
<ul>
<li>第二行的 "# This is a ..." 就是 BASH 程序的注释，在 BASH 程序中从“#”号（注意：后面紧接着是“!”号的除外）开始到行尾的多有部分均被看作是程序的注释。</li>
</ul>
<ul>
<li>第三行的 <code>echo</code> 语句的功能是把 echo 后面的字符串输出到标准输出中去。由于 echo 后跟的是 "Hello World" 这个字符串，因此 "Hello World"这个字串就被显示在控制台终端的屏幕上了。需要注意的是 BASH 中的绝大多数语句结尾处都<strong>没有分号</strong>。</li>
</ul>
</blockquote>
<p><strong>运行Bash脚本的方式：</strong></p>
<blockquote>
<pre><code class="hljs ruby"><span class="hljs-comment"># 使用shell来执行</span>
$ sh hello.sh
<span class="hljs-comment"># 使用bash来执行</span>
$ bash hello.sh
使用.来执行
$ . ./hello.sh
使用source来执行
$ source hello.sh
还可以让脚本本有者该执行权限，允许该用户执行该脚本
$ chmod u+rx hello.sh
<span class="hljs-comment"># 执行命令，这身就具有可执行权限，通过chmod命令可以修改：</span>
<span class="hljs-comment"># 赋予脚本的所将使用脚本第一行指定的shell来执行，如果指定shell不存在，将使用系统默认shell来执行</span>
$  ./hello.sh
</code></pre></blockquote>
<h3 id="2-">2.使用重定向</h3>
<p>比如我们想要<strong>保存</strong>刚刚的hello world为一个文本，那么该怎么办呢？</p>
<p><code>&gt;</code> 这个符号是重定向,执行以下代码，就会在当前目录下生成一个my.txt。打开看看有没有hello world</p>
<pre><code class="hljs bash"> <span class="hljs-comment">#!/bin/bash</span>
 <span class="hljs-built_in">echo</span> <span class="hljs-string">"Hello World"</span> &gt; my.txt
</code></pre><h3 id="3-var-log-log-">3.使用脚本清除/var/log下的log文件</h3>
<p>首先我们看一看<code>/var/log/messages和/var/log/wtmp</code>里面有啥东西</p>
<pre><code class="hljs bash">cat /var/<span class="hljs-built_in">log</span>/wtmp
</code></pre><p>以上这两个文件中记录了系统的一些信息，现在我们需要写一个脚本把里面的东西清空，但是保留文件</p>
<pre><code class="hljs ruby">$ vim cleanlogs.sh
</code></pre><p>说明：</p>
<blockquote>
<p><code>/dev/null</code>这个东西可以理解为一个黑洞，里面是空的（可以用cat命令看一看），什么东西都可以往里面扔，扔了就没了</p>
</blockquote>
<pre><code class="hljs bash"><span class="hljs-meta">#!/bin/bash
</span>
<span class="hljs-comment"># 初始化一个变量</span>
LOG_DIR=/var/<span class="hljs-built_in">log</span>

<span class="hljs-built_in">cd</span> <span class="hljs-variable">$LOG_DIR</span>

cat /dev/null &gt; wtmp

<span class="hljs-built_in">echo</span> <span class="hljs-string">"Logs cleaned up."</span>

<span class="hljs-built_in">exit</span>
</code></pre><p>运行脚本前，先看看 /var/log/ 下文件内是否有内容。运行此脚本后，文件的内容将被清除。</p>
<p><strong>执行</strong></p>
<blockquote>
<ul>
<li><p>由于脚本中含有对系统日志文件内容的清除操作，这要求要有管理员权限.不然会报<code>permission denide</code>错误</p>
<p>使用sudo命令调用<code>管理员权限</code>才能执行成功：</p>
<p><code>$ sudo ./cleanlogs.sh</code></p>
</li>
<li><code>#!/bin/bash</code>这一行是表示使用<code>/bin/bash</code>作为脚本的解释器，这行要放在脚本的行首并且不要省略</li>
</ul>
<ul>
<li>脚本正文中以<code>#</code>号开头的行都是注释语句，这些行在脚本的实际执行过程中不会被执行。这些注释语句能方便我们在脚本中做一些注释或标记，让脚本更具可读性。</li>
</ul>
</blockquote>
<h2 id="doc-section-3">四、思考练习</h2>
<h3 id="1-">1. 遇到权限不够的提示，为什么，如何解决？</h3>
<p>权限不够加sudo啊，可是你会发现</p>
<p><code>sudo cat /dev/null &gt; messages</code></p>
<p>一样会提示权限不够，为什么呢？因为sudo只能让cat命令以sudo的权限执行，而对于<code>&gt;</code>这个符号并没有<code>sudo</code>的权限，我们可以使用</p>
<p><code>sudo sh -c "cat /dev/null &gt; messages "</code></p>
<p>让整个命令都具有sudo的权限执行</p>
<h3 id="2-cleanlogs-sh-log-">2. 为什么cleanlogs.sh可以将log文件清除？</h3>
<p>因为<code>/dev/null</code> ，里面是空的，什么东西都可以往里面扔，扔了就没了</p>
</div>