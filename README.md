# JS-

  <section class="post-content">
<h3 id="q1">Q0 不通过中间量互换值
     <code>
       var a = 1;       <br/>
       var b = 2;       <br/>
       a = [b, b=a][0]; <br/>
     </code>
<h3 id="q1">Q1 判断一个单词是否是回文？</h3>

<blockquote>
  <p>回文是指把相同的词汇或句子，在下文中调换位置或颠倒过来，产生首尾回环的情趣，叫做回文，也叫回环。比如 mamam redivider .</p>
</blockquote>

<p>很多人拿到这样的题目非常容易想到用for 将字符串颠倒字母顺序然后匹配就行了。其实重要的考察的就是对于reverse的实现。其实我们可以利用现成的函数，将字符串转换成数组，这个思路很重要，我们可以拥有更多的自由度去进行字符串的一些操作。</p>

<pre><code class="language- JS hljs"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">checkPalindrom</span>(<span class="hljs-params">str</span>) </span>{  
    <span class="hljs-keyword">return</span> str == str.split(<span class="hljs-string">''</span>).reverse().join(<span class="hljs-string">''</span>);
}
</code></pre>

<h3 id="q2">Q2 去掉一组整型数组重复的值</h3>

<pre><code class="language- bash hljs">比如输入: [1,13,24,11,11,14,1,2] 
输出: [1,13,24,11,14,2]
需要去掉重复的11 和 1 这两个元素。
</code></pre>

<p>这道问题出现在诸多的前端面试题中，主要考察个人对Object的使用，利用key来进行筛选。</p>

<pre><code class="language- JS hljs"><span class="hljs-comment">/**
* unique an array 
**/</span>
<span class="hljs-keyword">let</span> unique = <span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params">arr</span>) </span>{  
  <span class="hljs-keyword">let</span> hashTable = {};
  <span class="hljs-keyword">let</span> data = [];
  <span class="hljs-keyword">for</span>(<span class="hljs-keyword">let</span> i=<span class="hljs-number">0</span>,l=arr.length;i&lt;l;i++) {
    <span class="hljs-keyword">if</span>(!hashTable[arr[i]]) {
      hashTable[arr[i]] = <span class="hljs-literal">true</span>;
      data.push(arr[i]);
    }
  }
  <span class="hljs-keyword">return</span> data

}

<span class="hljs-built_in">module</span>.exports = unique;  
</code></pre>

<h3 id="q3">Q3 统计一个字符串出现最多的字母</h3>

<p>给出一段英文连续的英文字符窜，找出重复出现次数最多的字母</p>

<pre><code class="language- bash hljs">输入 ： afjghdfraaaasdenas 

输出 ： a
</code></pre>

<p>前面出现过去重的算法，这里需要是统计重复次数。</p>

<pre><code class="language- JS hljs"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">findMaxDuplicateChar</span>(<span class="hljs-params">str</span>) </span>{  
  <span class="hljs-keyword">if</span>(str.length == <span class="hljs-number">1</span>) {
    <span class="hljs-keyword">return</span> str;
  }
  <span class="hljs-keyword">let</span> charObj = {};
  <span class="hljs-keyword">for</span>(<span class="hljs-keyword">let</span> i=<span class="hljs-number">0</span>;i&lt;str.length;i++) {
    <span class="hljs-keyword">if</span>(!charObj[str.charAt(i)]) {
      charObj[str.charAt(i)] = <span class="hljs-number">1</span>;
    }<span class="hljs-keyword">else</span>{
      charObj[str.charAt(i)] += <span class="hljs-number">1</span>;
    }
  }
  <span class="hljs-keyword">let</span> maxChar = <span class="hljs-string">''</span>,
      maxValue = <span class="hljs-number">1</span>;
  <span class="hljs-keyword">for</span>(<span class="hljs-keyword">var</span> k <span class="hljs-keyword">in</span> charObj) {
    <span class="hljs-keyword">if</span>(charObj[k] &gt;= maxValue) {
      maxChar = k;
      maxValue = charObj[k];
    }
  }
  <span class="hljs-keyword">return</span> maxChar;

}

<span class="hljs-built_in">module</span>.exports = findMaxDuplicateChar;  
</code></pre>

<h3 id="q4">Q4 排序算法</h3>

<p>如果抽到算法题目的话，应该大多都是比较开放的题目，不限定算法的实现，但是一定要求掌握其中的几种，所以冒泡排序，这种较为基础并且便于理解记忆的算法一定需要熟记于心。冒泡排序算法就是依次比较大小，小的的大的进行位置上的交换。</p>

<pre><code class="language- JS hljs"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">bubbleSort</span>(<span class="hljs-params">arr</span>) </span>{  
    <span class="hljs-keyword">for</span>(<span class="hljs-keyword">let</span> i = <span class="hljs-number">0</span>,l=arr.length;i&lt;l<span class="hljs-number">-1</span>;i++) {
        <span class="hljs-keyword">for</span>(<span class="hljs-keyword">let</span> j = i+<span class="hljs-number">1</span>;j&lt;l;j++) { 
          <span class="hljs-keyword">if</span>(arr[i]&gt;arr[j]) {
                <span class="hljs-keyword">let</span> tem = arr[i];
                arr[i] = arr[j];
                arr[j] = tem;
            }
        }
    }
    <span class="hljs-keyword">return</span> arr;
}
<span class="hljs-built_in">module</span>.exports = bubbleSort;  
</code></pre>

<p>除了冒泡排序外，其实还有很多诸如 <a href="https://zh.wikipedia.org/wiki/%E6%8F%92%E5%85%A5%E6%8E%92%E5%BA%8F">插入排序</a>,<a href="https://zh.wikipedia.org/wiki/%E5%BF%AB%E9%80%9F%E6%8E%92%E5%BA%8F">快速排序</a>，<a href="https://zh.wikipedia.org/wiki/%E5%B8%8C%E5%B0%94%E6%8E%92%E5%BA%8F">希尔排序</a>等。每一种排序算法都有各自的特点。全部掌握也不需要，但是心底一定要熟悉几种算法。
比如快速排序，其效率很高，而其基本原理如图(来自wiki)：</p>

<p><img src="https://upload.wikimedia.org/wikipedia/commons/6/6a/Sorting_quicksort_anim.gif"></p>

<p>算法参考某个元素值，将小于它的值，放到左数组中，大于它的值的元素就放到右数组中，然后递归进行上一次左右数组的操作，返回合并的数组就是已经排好顺序的数组了。</p>

<pre><code class="language- JS hljs"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">quickSort</span>(<span class="hljs-params">arr</span>) </span>{

    <span class="hljs-keyword">if</span>(arr.length&lt;=<span class="hljs-number">1</span>) {
        <span class="hljs-keyword">return</span> arr;
    }

    <span class="hljs-keyword">let</span> leftArr = [];
    <span class="hljs-keyword">let</span> rightArr = [];
    <span class="hljs-keyword">let</span> q = arr[<span class="hljs-number">0</span>];
    <span class="hljs-keyword">for</span>(<span class="hljs-keyword">let</span> i = <span class="hljs-number">1</span>,l=arr.length; i&lt;l; i++) {
        <span class="hljs-keyword">if</span>(arr[i]&gt;q) {
            rightArr.push(arr[i]);
        }<span class="hljs-keyword">else</span>{
            leftArr.push(arr[i]);
        }
    }

    <span class="hljs-keyword">return</span> [].concat(quickSort(leftArr),[q],quickSort(rightArr));
}

<span class="hljs-built_in">module</span>.exports = quickSort;  
</code></pre>

<p>安利大家一个学习的地址，通过动画演示算法的实现。</p>

<p><a href="http://math.hws.edu/eck/jsdemo/sortlab.html">HTML5 Canvas Demo: Sorting Algorithms</a></p>

<h3 id="q5">Q5 不借助临时变量，进行两个整数的交换</h3>

<pre><code class="language- bash hljs">输入 a = 2, b = 4 输出 a = 4, b =2
</code></pre>

<p>这种问题非常巧妙，需要大家跳出惯有的思维，利用 a , b进行置换。</p>

<p>主要是利用 + - 去进行运算，类似 a = a + ( b - a) 实际上等同于最后 的 a = b;</p>

<pre><code class="language- JS hljs"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">swap</span>(<span class="hljs-params">a , b</span>) </span>{  
  b = b - a;
  a = a + b;
  b = a - b;
  <span class="hljs-keyword">return</span> [a,b];
}

<span class="hljs-built_in">module</span>.exports = swap;  
</code></pre>

<h3 id="q6canvas">Q6 使用canvas 绘制一个有限度的斐波那契数列的曲线？</h3>

<p><img src="http://img1.vued.vanthink.cn/vued90edf7b944ec479ee8b4203cf56e158d.png"></p>

<p>数列长度限定在9.</p>

<p><code>斐波那契数列</code>，又称黄金分割数列，指的是这样一个数列：0、1、1、2、3、5、8、13、21、34、……在数学上，斐波纳契数列主要考察递归的调用。我们一般都知道定义</p>

<pre><code class="language- JS hljs">fibo[i] = fibo[i<span class="hljs-number">-1</span>]+fibo[i<span class="hljs-number">-2</span>];  
</code></pre>

<p>生成斐波那契数组的方法</p>

<pre><code class="language- JS hljs"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">getFibonacci</span>(<span class="hljs-params">n</span>) </span>{  
  <span class="hljs-keyword">var</span> fibarr = [];
  <span class="hljs-keyword">var</span> i = <span class="hljs-number">0</span>;
  <span class="hljs-keyword">while</span>(i&lt;n) {
    <span class="hljs-keyword">if</span>(i&lt;=<span class="hljs-number">1</span>) {
      fibarr.push(i);
    }<span class="hljs-keyword">else</span>{
      fibarr.push(fibarr[i<span class="hljs-number">-1</span>] + fibarr[i<span class="hljs-number">-2</span>])
    }
    i++;
  }

  <span class="hljs-keyword">return</span> fibarr;
}
</code></pre>

<p>剩余的工作就是利用canvas <code>arc</code>方法进行曲线绘制了</p>

<p><a href="http://codepen.io/Jack_Pu/pen/LRaxZB">DEMO</a></p>

<h3 id="q7">Q7 找出下列正数组的最大差值比如:</h3>

<pre><code class="language- bash hljs">输入 [10,5,11,7,8,9]

输出 6
</code></pre>

<p>这是通过一道题目去测试对于基本的数组的最大值的查找，很明显我们知道，最大差值肯定是一个数组中最大值与最小值的差。</p>

<pre><code class="language- JS hljs">  <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">getMaxProfit</span>(<span class="hljs-params">arr</span>) </span>{

    <span class="hljs-keyword">var</span> minPrice = arr[<span class="hljs-number">0</span>];
    <span class="hljs-keyword">var</span> maxProfit = <span class="hljs-number">0</span>;

    <span class="hljs-keyword">for</span> (<span class="hljs-keyword">var</span> i = <span class="hljs-number">0</span>; i &lt; arr.length; i++) {
        <span class="hljs-keyword">var</span> currentPrice = arr[i];

        minPrice = <span class="hljs-built_in">Math</span>.min(minPrice, currentPrice);

        <span class="hljs-keyword">var</span> potentialProfit = currentPrice - minPrice;

        maxProfit = <span class="hljs-built_in">Math</span>.max(maxProfit, potentialProfit);
    }

    <span class="hljs-keyword">return</span> maxProfit;
}
</code></pre>

<h3 id="q8">Q8 随机生成指定长度的字符串</h3>

<p>实现一个算法，随机生成指制定长度的字符窜。</p>

<pre><code class="language- BASH hljs">比如给定 长度 8  输出 4ldkfg9j
</code></pre>

<pre><code class="language- JS hljs"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">randomString</span>(<span class="hljs-params">n</span>) </span>{  
  <span class="hljs-keyword">let</span> str = <span class="hljs-string">'abcdefghijklmnopqrstuvwxyz9876543210'</span>;
  <span class="hljs-keyword">let</span> tmp = <span class="hljs-string">''</span>,
      i = <span class="hljs-number">0</span>,
      l = str.length;
  <span class="hljs-keyword">for</span> (i = <span class="hljs-number">0</span>; i &lt; n; i++) {
    tmp += str.charAt(<span class="hljs-built_in">Math</span>.floor(<span class="hljs-built_in">Math</span>.random() * l));
  }
  <span class="hljs-keyword">return</span> tmp;
}

<span class="hljs-built_in">module</span>.exports = randomString;  
</code></pre>

<h3 id="q9getelementsbyclassname">Q9 实现类似getElementsByClassName 的功能</h3>

<p>自己实现一个函数，查找某个DOM节点下面的包含某个class的所有DOM节点？不允许使用原生提供的 getElementsByClassName querySelectorAll 等原生提供DOM查找函数。</p>

<pre><code class="language- JS hljs"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">queryClassName</span>(<span class="hljs-params">node, name</span>) </span>{  
  <span class="hljs-keyword">var</span> starts = <span class="hljs-string">'(^|[ \n\r\t\f])'</span>,
       ends = <span class="hljs-string">'([ \n\r\t\f]|$)'</span>;
  <span class="hljs-keyword">var</span> array = [],
        regex = <span class="hljs-keyword">new</span> <span class="hljs-built_in">RegExp</span>(starts + name + ends),
        elements = node.getElementsByTagName(<span class="hljs-string">"*"</span>),
        length = elements.length,
        i = <span class="hljs-number">0</span>,
        element;

    <span class="hljs-keyword">while</span> (i &lt; length) {
        element = elements[i];
        <span class="hljs-keyword">if</span> (regex.test(element.className)) {
            array.push(element);
        }

        i += <span class="hljs-number">1</span>;
    }

    <span class="hljs-keyword">return</span> array;
}
</code></pre>

<h3 id="q10jsbinarysearchtree">Q10 使用JS 实现二叉查找树(Binary Search Tree)</h3>

<p>一般叫全部写完的概率比较少，但是重点考察你对它的理解和一些基本特点的实现。
二叉查找树，也称二叉搜索树、有序二叉树（英语：ordered binary tree）是指一棵空树或者具有下列性质的二叉树：</p>

<ul>
<li>任意节点的左子树不空，则左子树上所有结点的值均小于它的根结点的值；</li>
<li>任意节点的右子树不空，则右子树上所有结点的值均大于它的根结点的值；</li>
<li>任意节点的左、右子树也分别为二叉查找树；</li>
<li>没有键值相等的节点。二叉查找树相比于其他数据结构的优势在于查找、插入的时间复杂度较低。为O(log n)。二叉查找树是基础性数据结构，用于构建更为抽象的数据结构，如集合、multiset、关联数组等。</li>
</ul>

<p><img src="http://img1.vued.vanthink.cn/vued95685e8f89199babd6273a93651ecd8b.png"></p>

<p>在写的时候需要足够理解二叉搜素树的特点，需要先设定好每个节点的数据结构</p>

<pre><code class="language- JS hljs"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Node</span> </span>{  
  <span class="hljs-keyword">constructor</span>(data, left, right) {
    <span class="hljs-keyword">this</span>.data = data;
    <span class="hljs-keyword">this</span>.left = left;
    <span class="hljs-keyword">this</span>.right = right;
  }

}
</code></pre>

<p>树是有节点构成，由根节点逐渐延生到各个子节点，因此它具备基本的结构就是具备一个根节点，具备添加，查找和删除节点的方法.</p>

<pre><code class="language- JS hljs"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">BinarySearchTree</span> </span>{

  <span class="hljs-keyword">constructor</span>() {
    <span class="hljs-keyword">this</span>.root = <span class="hljs-literal">null</span>;
  }

  insert(data) {
    <span class="hljs-keyword">let</span> n = <span class="hljs-keyword">new</span> Node(data, <span class="hljs-literal">null</span>, <span class="hljs-literal">null</span>);
    <span class="hljs-keyword">if</span> (!<span class="hljs-keyword">this</span>.root) {
      <span class="hljs-keyword">return</span> <span class="hljs-keyword">this</span>.root = n;
    }
    <span class="hljs-keyword">let</span> currentNode = <span class="hljs-keyword">this</span>.root;
    <span class="hljs-keyword">let</span> parent = <span class="hljs-literal">null</span>;
    <span class="hljs-keyword">while</span> (<span class="hljs-number">1</span>) {
      parent = currentNode;
      <span class="hljs-keyword">if</span> (data &lt; currentNode.data) {
        currentNode = currentNode.left;
        <span class="hljs-keyword">if</span> (currentNode === <span class="hljs-literal">null</span>) {
          parent.left = n;
          <span class="hljs-keyword">break</span>;
        }
      } <span class="hljs-keyword">else</span> {
        currentNode = currentNode.right;
        <span class="hljs-keyword">if</span> (currentNode === <span class="hljs-literal">null</span>) {
          parent.right = n;
          <span class="hljs-keyword">break</span>;
        }
      }
    }
  }

  remove(data) {
    <span class="hljs-keyword">this</span>.root = <span class="hljs-keyword">this</span>.removeNode(<span class="hljs-keyword">this</span>.root, data)
  }

  removeNode(node, data) {
    <span class="hljs-keyword">if</span> (node == <span class="hljs-literal">null</span>) {
      <span class="hljs-keyword">return</span> <span class="hljs-literal">null</span>;
    }

    <span class="hljs-keyword">if</span> (data == node.data) {
      <span class="hljs-comment">// no children node</span>
      <span class="hljs-keyword">if</span> (node.left == <span class="hljs-literal">null</span> &amp;&amp; node.right == <span class="hljs-literal">null</span>) {
        <span class="hljs-keyword">return</span> <span class="hljs-literal">null</span>;
      }
      <span class="hljs-keyword">if</span> (node.left == <span class="hljs-literal">null</span>) {
        <span class="hljs-keyword">return</span> node.right;
      }
      <span class="hljs-keyword">if</span> (node.right == <span class="hljs-literal">null</span>) {
        <span class="hljs-keyword">return</span> node.left;
      }

      <span class="hljs-keyword">let</span> getSmallest = <span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params">node</span>) </span>{
        <span class="hljs-keyword">if</span>(node.left === <span class="hljs-literal">null</span> &amp;&amp; node.right == <span class="hljs-literal">null</span>) {
          <span class="hljs-keyword">return</span> node;
        }
        <span class="hljs-keyword">if</span>(node.left != <span class="hljs-literal">null</span>) {
          <span class="hljs-keyword">return</span> node.left;
        }
        <span class="hljs-keyword">if</span>(node.right !== <span class="hljs-literal">null</span>) {
          <span class="hljs-keyword">return</span> getSmallest(node.right);
        }

      }
      <span class="hljs-keyword">let</span> temNode = getSmallest(node.right);
      node.data = temNode.data;
      node.right = <span class="hljs-keyword">this</span>.removeNode(temNode.right,temNode.data);
      <span class="hljs-keyword">return</span> node;

    } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (data &lt; node.data) {
      node.left = <span class="hljs-keyword">this</span>.removeNode(node.left,data);
      <span class="hljs-keyword">return</span> node;
    } <span class="hljs-keyword">else</span> {
      node.right = <span class="hljs-keyword">this</span>.removeNode(node.right,data);
      <span class="hljs-keyword">return</span> node;
    }
  }

  find(data) {
    <span class="hljs-keyword">var</span> current = <span class="hljs-keyword">this</span>.root;
    <span class="hljs-keyword">while</span> (current != <span class="hljs-literal">null</span>) {
      <span class="hljs-keyword">if</span> (data == current.data) {
        <span class="hljs-keyword">break</span>;
      }
      <span class="hljs-keyword">if</span> (data &lt; current.data) {
        current = current.left;
      } <span class="hljs-keyword">else</span> {
        current = current.right
      }
    }
    <span class="hljs-keyword">return</span> current.data;
  }

}

<span class="hljs-built_in">module</span>.exports = BinarySearchTree;  
</code></pre>


