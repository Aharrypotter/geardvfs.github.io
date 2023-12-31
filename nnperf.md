<style>

.markdown-body {    //css总体样式
  padding: 20px;
  font-size: 12px;
}
.markdown-body h2 {
  font-size: 18px;
  margin: 1em 0 15px;
  padding-top: 0.8em;
  padding-bottom: 0.8em;
}
.markdown-body h3 {
  font-size: 14px;
  margin: 22px 0 16px;
}
.markdown-body h4 {
  font-size: 13px;
  margin: 20px 0 16px;
}
.markdown-body h5 {
  font-size: 12px;
  margin: 16px 0 16px;
  font-weight: 700;
}
.markdown-body p {
  font-size: 16px;
  line-height: 24px;
  color: #666666;
  margin-top: 0px;
  margin: 8px 0;
  margin: 14px 0 14px;
}
.markdown-body pre {
  background-color: #eee;
  margin-bottom: 8px;
  margin-top: 8px;
  margin: 12px 0 12px;
}
.markdown-body blockquote {
  margin-bottom: 8px;
  margin-top: 8px;
  margin: 14px 0 14px;
  background-color: #eee;
  padding: 16px 16px;
}
.markdown-body tr {
  background-color: #f5f5f5;
}
.markdown-body code {
  background-color: #eee;
}
.markdown-body ul,
.markdown-body ol,
.markdown-body li {
  list-style: unset;
  font-size: 14px;
  line-height: 20px;
  color: #666666;
  margin-top: 0px;
  margin: 8px 0;
}
.markdown-body blockquote {
  border-color: #48b6e2;
}
.markdown-body table {
  display: table;
  width: 100%;
  max-width: 100%;
  margin-bottom: 20px;
}
body {
    background: #fff; /页面背景颜色/
}
@media (max-width: 767px) {
    .markdown-body {
        padding: 15px;
    }
}
</style>

<head>
    <meta charset="UTF-8">
    <title>nnPerf</title>
    <link rel="stylesheet" href="css/dan.css" />
	<script src="https://cdn.bootcdn.net/ajax/libs/highlight.js/11.2.0/highlight.min.js"></script>
    <script src="js/jquery-3.6.0.min.js"></script>
	<script>hljs.initHighlightingOnLoad();</script> 
    <script>
        function(){
            //给每一串代码元素增加复制代码节点
            let preList = $(".content pre");
            for (let pre of preList) {
                //给每个代码块增加上“复制代码”按钮
                let btn = $("<span class=\"btn-pre-copy\" onclick='preCopy(this)'>Copy</span>");
                btn.prependTo(pre);
            }
        };
        function preCopy(obj) {
            //执行复制
            let btn = $(obj);
            let pre = btn.parent();
            //为了实现复制功能。新增一个临时的textarea节点。使用他来复制内容
            let temp = $("<textarea></textarea>");
            //避免复制内容时把按钮文字也复制进去。先临时置空
            btn.text("");
            temp.text(pre.text());
            temp.appendTo(pre);
            temp.select();
            document.execCommand("Copy");
            temp.remove();
            //修改按钮名
            btn.text("Success!");
            //一定时间后吧按钮名改回来
            setTimeout(()=> {
                btn.text("Copy");
            },1500);
        }
        function selectAll(obj){
            (obj).select();
        }
    </script>
</head>

<body width=650>
    <center>
        <H1>nnPerf: A Real-time On-device Tool Profiling DNN Inference on Mobile Platforms</H1>
        <H4><a href="#overview">Overview</a> |
            <a href="#key_features">Key Features</a> |
            <a href="#installation_instructions">Installation instructions</a> |
            <a href="#online_tool">Visualization tool</a><br> 
            <a href="#citation">Citation</a> |
            <a href="#credits">Credits</a> |
            <a href="">GitHub</a> | <a href="">FAQ</a> | <a href="">Get Help</a>
        </H4>
    </center>
    <H2 id="overview">Overview</H2>
    <p> This webpage contains instructions to use our nnPerf.This is a real-time on-device profiler designed to collect
        and analyze the DNN model run-time inference latency on mobile platforms. nnPerf demystifies the hidden layers
        and metrics used for pursuing DNN optimizations and adaptations at the granularity of operators and kernels,
        ensuring every facet contributing to a DNN model’s runtime efficiency is easily accessible to mobile developers
        via well-defined APIs.</p>
    <p>With nnPerf, the mobile developers can easily identify the bottleneck in model run-time efficiency and optimize
        the model architecture to meet system-level objectives (SLO).</p>
    <p>The figure below compares nnPerf to existing DNN model analyzers designed for mobile platforms.</p>
    <div class="figcontain">
        <img width="600" src="img/The_effectiveness_of_nnPerf.jpg" alt="The effectiveness of nnPerf">
        <div class="figcaption">The effectiveness of nnPerf</div>
    </div>
    <p>To cite this tool, the best reference is the <a href="#citation">SenSys 2023 paper</a> (<a href="">BibTeX</a>).</p>
    <br>
    <H2 id="key_features">Key Features</H2>
    <!-- <p>----</p> -->
    <video poster="" id="steve" autoplay controls muted loop height="100%" width="780">
        <source src="video/nnperf-video.mp4"
                type="video/mp4">
    </video>
    <p><b>1. Plug-and-play design principles</b></p>
    <p class="feature">&#8226; Simplified DNN model latency analysis on mobile platforms, allowing developers to easily identify bottlenecks and optimize model efficiency.</p>
    <p><b>2. Real-time on-device</b></p>
    <p class="feature">&#8226; Provides real-time on-device analytics to ensure accurate latency feedback for inference DNN models on mobile devices.</p>
    <p><b>3. Support GPU Kernel-level fine-grained profiling</b></p>
    <p class="feature">&#8226; The ability to perform in-depth analysis of GPU kernels provides developers with granular insights into the optimization of DNN models.</p>
    <p>For more design details and features, please refer to <a href="">our Sensys 2023 paper</a>.</p>
    <br>
    <H2 id="installation_instructions">Installation instructions</H2>
    <p>Set up nnPerf in just a few steps. You can download <a href="nnPerf-Tool.html"> the latest version of nnPerf here.</a>
    </p>
    <H3><span class="dotted-underline">Quick start with apk</span></H3>
    <p>1. Use adb to connect to smartphones or mobile platforms (Android basic system).</p>
    <p>2. Install the nnPerf_v1.1.apk.</p>
    <div class="content"><pre>adb install -t '.\nnPerfAPKinstaller\nnPerf_v1.1.apk'</pre></div>
    <H3><span class="dotted-underline">Build android project</span></H3>
    <p>1. Install Android Studio 3.6.3 (Runtime version: 1.8.0_212-release-1586-b04 amd64).</p>
    <p>2. Import Project.</p>
    <div class="content"><pre>File -> Open -> Current file directory</pre></div>
    <p>3. Android Studio Setting.</p>
    <div class="content"><pre>Android Gradle Plugin Version:   3.1.3
Gradle Version:                  4.4
NDK Version:                     21.0.6113669
JDK Verison:                     1.8.0_211
Complile Sdk Version:            27
Build Tools Version:             27.0.3
</pre></div>
    <p>4. Run to profile.</p>
    <div class="content"><pre>Update Output path: /storage/emulated/0/</pre></div>
    <p>5. Note: In the case of GPU reasoning, do not directly switch models.</p>
    <p>6. Model support list (Support for adding other .tflite models)</p>
    <div class="content"><pre>mobilenetV3-Large-Float
mobilenetV3-Small-Float
EfficientNet-b0-Float
mobilenetV1-Quant
mobilenetV2-Float
mobilenetV1-Float
Squeezenet-Float
Densenet-Float
MNasNet-1.0
</pre></div>
    <br>
    <H2 id="online_tool">Online timeline visualization tool</H2>
    <p>This is our <a href="http://8.218.49.80:8080/charts/">online timeline visualization tool</a> designed for nnPerf.
    </p>
    <div class="figcontain">
        <img width="750" src="img/tool1.jpg" alt="Channel state information for four 1x1 links">
        <div class="figcaption">Example of visualization tool</div>
    </div>
    <div class="custom-paragraphs">
        <p>Features of our visualization tools:</p>
        <p>1. Easily upload test data files and resize the interface using the scroll wheel.</p>
        <p>2. Utilize the "Sort" button to organize data within the file based on three distinctcategories.</p>
        <p>3. Retrieve and query previously uploaded files conveniently through the History feature.</p>
        <P>4. Selectively hide specific filters through the intuitive legend in the upper right corner of the interface.</P>
    </div>
    <br>
    <H2 id="citation">Citation</H2>
    <p>If you find our work useful in your research, please consider citing:</p>
    <div class="content"><pre>@inproceedings{chu2023nnperf,
    title={nnPerf: Demystifying DNN Runtime Inference Latency on Mobile Platforms},
    author={Haolin Chu, Xiaolong Zheng, Liang Liu, Huadong Ma},
    booktitle={The 21th ACM Conference on Embedded Networked Sensor Systems},
    pages={TBD},
    year={2023}
}</pre></div>
    <br>
    <H2 id="credits">Credits</H2>
    <center>
        <H4>Authors: <a href="">Haolin Chu</a> | <a href="">Xiaolong Zheng</a> | <a href="">Liang Liu</a> | <a
                href="">Huadong Ma</a><br>
            Maintainers: <a href="">Haolin Chu</a> </H4>
    </center>
    <!--- ********************************************************************* -->
    <script type="text/javascript">
        var gaJsHost = (("https:" == document.location.protocol) ?
            "https://ssl." : "http://www.");
        document.write(unescape("%3Cscript src='" + gaJsHost +
            "google-analytics.com/ga.js' type='text/javascript'%3E%3C/script%3E"));
    </script>
    <script type="text/javascript">
        var pageTracker = _gat._getTracker("UA-3907502-1");
        pageTracker._initData();
        pageTracker._trackPageview();
    </script>
    <!-- Default Statcounter code for nnprofiling https://nnprofiling.github.io/ -->
    <script type="text/javascript">
        var sc_project = 12929284;
        var sc_invisible = 1;
        var sc_security = "3e5620fa";
    </script>
    <script type="text/javascript" src="https://www.statcounter.com/counter/counter.js" async></script>
    <noscript>
        <div class="statcounter"><a title="Web Analytics" href="https://statcounter.com/" target="_blank"><img
                    class="statcounter" src="https://c.statcounter.com/12929284/0/3e5620fa/1/" alt="Web Analytics"
                    referrerPolicy="no-referrer-when-downgrade"></a></div>
    </noscript>
    <!-- End of Statcounter Code -->
</body>
