# Textual里遇到的容器(Container)内Static或Label等控件带有边框导致双层边框问题的探究

# 过程

今天在做Agent的时候发现一个事情，就是由于在控制面板的主题选项卡这里Static控件无法添加`overflow-y`，并且使用`with VerticalScroll():`会导致`yield Static("", id="available-themes", classes="theme-info-available")`里的内容消失，所以我决定使用下面的方式来为Static添加滚动条：
```Python
with Container(id="themes-container", classes="themes-scroll-container"):
     yield Static("", id="available-themes", classes="theme-info-available")
```

可结果这个用容器的方式给Static添加滚动条时，不知道为什么，其老是外部父容器和内部子容器同时显示边框，请看下面截图：
<div>
<svg class="rich-terminal" viewBox="0 0 1922 1074.8" xmlns="http://www.w3.org/2000/svg">
    <!-- Generated with Rich https://www.textualize.io -->
    <style>

    @font-face {
        font-family: "Fira Code";
        src: local("FiraCode-Regular"),
                url("https://cdnjs.cloudflare.com/ajax/libs/firacode/6.2.0/woff2/FiraCode-Regular.woff2") format("woff2"),
                url("https://cdnjs.cloudflare.com/ajax/libs/firacode/6.2.0/woff/FiraCode-Regular.woff") format("woff");
        font-style: normal;
        font-weight: 400;
    }
    @font-face {
        font-family: "Fira Code";
        src: local("FiraCode-Bold"),
                url("https://cdnjs.cloudflare.com/ajax/libs/firacode/6.2.0/woff2/FiraCode-Bold.woff2") format("woff2"),
                url("https://cdnjs.cloudflare.com/ajax/libs/firacode/6.2.0/woff/FiraCode-Bold.woff") format("woff");
        font-style: bold;
        font-weight: 700;
    }

    .terminal-800550482-matrix {
        font-family: Fira Code, monospace;
        font-size: 20px;
        line-height: 24.4px;
        font-variant-east-asian: full-width;
    }

    .terminal-800550482-title {
        font-size: 18px;
        font-weight: bold;
        font-family: arial;
    }

    .terminal-800550482-r1 { fill: #c5c8c6 }
.terminal-800550482-r2 { fill: #e0e0e0 }
.terminal-800550482-r3 { fill: #7f7f7f }
.terminal-800550482-r4 { fill: #ddedf9;font-weight: bold }
.terminal-800550482-r5 { fill: #585858 }
.terminal-800550482-r6 { fill: #0178d4 }
.terminal-800550482-r7 { fill: #0178d4;font-weight: bold }
.terminal-800550482-r8 { fill: #e0e0e0;font-weight: bold }
.terminal-800550482-r9 { fill: #004578 }
.terminal-800550482-r10 { fill: #1e1e1e }
.terminal-800550482-r11 { fill: #000000 }
.terminal-800550482-r12 { fill: #6db2ff }
.terminal-800550482-r13 { fill: #2d2d2d }
.terminal-800550482-r14 { fill: #004295 }
.terminal-800550482-r15 { fill: #0d0d0d }
.terminal-800550482-r16 { fill: #a5a5a5;font-style: italic; }
.terminal-800550482-r17 { fill: #ffa62b;font-weight: bold }
.terminal-800550482-r18 { fill: #495259 }
    </style>

    <defs>
    <clipPath id="terminal-800550482-clip-terminal">
      <rect x="0" y="0" width="1902.1999999999998" height="1023.8" />
    </clipPath>
    <clipPath id="terminal-800550482-line-0">
    <rect x="0" y="1.5" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-1">
    <rect x="0" y="25.9" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-2">
    <rect x="0" y="50.3" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-3">
    <rect x="0" y="74.7" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-4">
    <rect x="0" y="99.1" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-5">
    <rect x="0" y="123.5" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-6">
    <rect x="0" y="147.9" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-7">
    <rect x="0" y="172.3" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-8">
    <rect x="0" y="196.7" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-9">
    <rect x="0" y="221.1" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-10">
    <rect x="0" y="245.5" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-11">
    <rect x="0" y="269.9" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-12">
    <rect x="0" y="294.3" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-13">
    <rect x="0" y="318.7" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-14">
    <rect x="0" y="343.1" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-15">
    <rect x="0" y="367.5" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-16">
    <rect x="0" y="391.9" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-17">
    <rect x="0" y="416.3" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-18">
    <rect x="0" y="440.7" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-19">
    <rect x="0" y="465.1" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-20">
    <rect x="0" y="489.5" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-21">
    <rect x="0" y="513.9" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-22">
    <rect x="0" y="538.3" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-23">
    <rect x="0" y="562.7" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-24">
    <rect x="0" y="587.1" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-25">
    <rect x="0" y="611.5" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-26">
    <rect x="0" y="635.9" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-27">
    <rect x="0" y="660.3" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-28">
    <rect x="0" y="684.7" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-29">
    <rect x="0" y="709.1" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-30">
    <rect x="0" y="733.5" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-31">
    <rect x="0" y="757.9" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-32">
    <rect x="0" y="782.3" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-33">
    <rect x="0" y="806.7" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-34">
    <rect x="0" y="831.1" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-35">
    <rect x="0" y="855.5" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-36">
    <rect x="0" y="879.9" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-37">
    <rect x="0" y="904.3" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-38">
    <rect x="0" y="928.7" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-39">
    <rect x="0" y="953.1" width="1903.2" height="24.65"/>
            </clipPath>
<clipPath id="terminal-800550482-line-40">
    <rect x="0" y="977.5" width="1903.2" height="24.65"/>
            </clipPath>
    </defs>

    <rect fill="#292929" stroke="rgba(255,255,255,0.35)" stroke-width="1" x="1" y="1" width="1920" height="1072.8" rx="8"/><text class="terminal-800550482-title" fill="#c5c8c6" text-anchor="middle" x="960" y="27">Nothing</text>
            <g transform="translate(26,22)">
            <circle cx="0" cy="0" r="7" fill="#ff5f57"/>
            <circle cx="22" cy="0" r="7" fill="#febc2e"/>
            <circle cx="44" cy="0" r="7" fill="#28c840"/>
            </g>
        
    <g transform="translate(9, 41)" clip-path="url(#terminal-800550482-clip-terminal)">
    <rect fill="#242f38" x="0" y="1.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="12.2" y="1.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="24.4" y="1.5" width="61" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="85.4" y="1.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="97.6" y="1.5" width="793" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="890.6" y="1.5" width="85.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="976" y="1.5" width="805.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="1781.2" y="1.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="1793.4" y="1.5" width="0" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="1793.4" y="1.5" width="97.6" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="1891" y="1.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="25.9" width="1903.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="50.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="50.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="50.3" width="48.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="73.2" y="50.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="85.4" y="50.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="97.6" y="50.3" width="73.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="170.8" y="50.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#0178d4" x="183" y="50.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#0178d4" x="195.2" y="50.3" width="48.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#0178d4" x="244" y="50.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="256.2" y="50.3" width="1634.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="50.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="74.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="74.7" width="170.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="183" y="74.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="195.2" y="74.7" width="48.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="244" y="74.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="256.2" y="74.7" width="1634.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="74.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="99.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="99.1" width="97.6" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="109.8" y="99.1" width="1781.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="99.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="123.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="123.5" width="1878.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="123.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="147.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="147.9" width="109.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="122" y="147.9" width="1769" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="147.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="172.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="172.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="172.3" width="1854.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="172.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="172.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="196.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="196.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="196.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="36.6" y="196.7" width="268.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="305" y="196.7" width="1561.6" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1866.6" y="196.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="196.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="196.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="221.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="221.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="221.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="36.6" y="221.1" width="268.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="305" y="221.1" width="1561.6" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1866.6" y="221.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="221.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="221.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="245.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="245.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="245.5" width="1854.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="245.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="245.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="269.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="269.9" width="1878.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="269.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="294.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="294.3" width="158.6" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="170.8" y="294.3" width="1720.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="294.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="318.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="318.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="318.7" width="1854.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="318.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="318.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="343.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="343.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="343.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="36.6" y="343.1" width="1805.6" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1842.2" y="343.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#003054" x="1854.4" y="343.1" width="24.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="343.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="343.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="367.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="367.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="367.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="36.6" y="367.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="48.8" y="367.5" width="109.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="158.6" y="367.5" width="1671.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1830" y="367.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1842.2" y="367.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#003054" x="1854.4" y="367.5" width="24.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="367.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="367.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="391.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="391.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="391.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="36.6" y="391.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="48.8" y="391.9" width="195.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="244" y="391.9" width="1586" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1830" y="391.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1842.2" y="391.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#003054" x="1854.4" y="391.9" width="24.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="391.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="391.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="416.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="416.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="416.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="36.6" y="416.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="48.8" y="416.3" width="207.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="256.2" y="416.3" width="1573.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1830" y="416.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1842.2" y="416.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#003054" x="1854.4" y="416.3" width="24.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="416.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="416.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="440.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="440.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="440.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="36.6" y="440.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="48.8" y="440.7" width="97.6" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="146.4" y="440.7" width="1683.6" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1830" y="440.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1842.2" y="440.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#003054" x="1854.4" y="440.7" width="24.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="440.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="440.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="465.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="465.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="465.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="36.6" y="465.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="48.8" y="465.1" width="134.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="183" y="465.1" width="1647" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1830" y="465.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1842.2" y="465.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#003054" x="1854.4" y="465.1" width="24.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="465.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="465.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="489.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="489.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="489.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="36.6" y="489.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="48.8" y="489.5" width="244" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="292.8" y="489.5" width="1537.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1830" y="489.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1842.2" y="489.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#003054" x="1854.4" y="489.5" width="24.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="489.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="489.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="513.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="513.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="513.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="36.6" y="513.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="48.8" y="513.9" width="195.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="244" y="513.9" width="1586" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1830" y="513.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1842.2" y="513.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#003054" x="1854.4" y="513.9" width="24.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="513.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="513.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="538.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="538.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="538.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="36.6" y="538.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="48.8" y="538.3" width="134.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="183" y="538.3" width="1647" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1830" y="538.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1842.2" y="538.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#003054" x="1854.4" y="538.3" width="24.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="538.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="538.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="562.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="562.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="562.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="36.6" y="562.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="48.8" y="562.7" width="183" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="231.8" y="562.7" width="1598.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1830" y="562.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1842.2" y="562.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#003054" x="1854.4" y="562.7" width="24.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="562.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="562.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="587.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="587.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="587.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="36.6" y="587.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="48.8" y="587.1" width="134.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="183" y="587.1" width="1647" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1830" y="587.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1842.2" y="587.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#003054" x="1854.4" y="587.1" width="24.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="587.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="587.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="611.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="611.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="611.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="36.6" y="611.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="48.8" y="611.5" width="134.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="183" y="611.5" width="1647" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1830" y="611.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1842.2" y="611.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#000000" x="1854.4" y="611.5" width="24.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="611.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="611.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="635.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="635.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="635.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="36.6" y="635.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="48.8" y="635.9" width="244" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="292.8" y="635.9" width="1537.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1830" y="635.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1842.2" y="635.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#000000" x="1854.4" y="635.9" width="24.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="635.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="635.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="660.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="660.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="660.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="36.6" y="660.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="48.8" y="660.3" width="231.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="280.6" y="660.3" width="1549.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1830" y="660.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1842.2" y="660.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#000000" x="1854.4" y="660.3" width="24.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="660.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="660.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="684.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="684.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="684.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="36.6" y="684.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="48.8" y="684.7" width="219.6" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="268.4" y="684.7" width="1561.6" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1830" y="684.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1842.2" y="684.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#000000" x="1854.4" y="684.7" width="24.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="684.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="684.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="709.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="709.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="24.4" y="709.1" width="1854.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1878.8" y="709.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="709.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="733.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="733.5" width="1878.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="733.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="757.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="757.9" width="1878.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="757.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="782.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="782.3" width="1878.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="782.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="806.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="806.7" width="695.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#0178d4" x="707.6" y="806.7" width="195.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="902.8" y="806.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="915" y="806.7" width="268.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1183.4" y="806.7" width="707.6" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="806.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="831.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="831.1" width="695.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#0178d4" x="707.6" y="831.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#0178d4" x="719.8" y="831.1" width="170.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#0178d4" x="890.6" y="831.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="902.8" y="831.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="915" y="831.1" width="268.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1183.4" y="831.1" width="707.6" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="831.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="855.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="855.5" width="695.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#0178d4" x="707.6" y="855.5" width="195.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="902.8" y="855.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="915" y="855.5" width="268.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1183.4" y="855.5" width="707.6" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="855.5" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="879.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="879.9" width="1878.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="879.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="904.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="904.3" width="1878.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="904.3" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="928.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="928.7" width="1878.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="928.7" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="953.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="12.2" y="953.1" width="585.6" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="597.8" y="953.1" width="1293.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="1891" y="953.1" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#1e1e1e" x="0" y="977.5" width="1903.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="0" y="1001.9" width="48.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="48.8" y="1001.9" width="61" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="109.8" y="1001.9" width="48.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="158.6" y="1001.9" width="158.6" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="317.2" y="1001.9" width="48.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="366" y="1001.9" width="109.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="475.8" y="1001.9" width="48.8" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="524.6" y="1001.9" width="61" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="585.6" y="1001.9" width="1171.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="1756.8" y="1001.9" width="12.2" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="1769" y="1001.9" width="24.4" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="1793.4" y="1001.9" width="97.6" height="24.65" shape-rendering="crispEdges"/><rect fill="#242f38" x="1891" y="1001.9" width="12.2" height="24.65" shape-rendering="crispEdges"/>
    <g class="terminal-800550482-matrix">
    <text class="terminal-800550482-r2" x="12.2" y="20" textLength="12.2" clip-path="url(#terminal-800550482-line-0)">⭘</text><text class="terminal-800550482-r2" x="890.6" y="20" textLength="85.4" clip-path="url(#terminal-800550482-line-0)">Nothing</text><text class="terminal-800550482-r1" x="1903.2" y="20" textLength="12.2" clip-path="url(#terminal-800550482-line-0)">
</text><text class="terminal-800550482-r1" x="1903.2" y="44.4" textLength="12.2" clip-path="url(#terminal-800550482-line-1)">
</text><text class="terminal-800550482-r3" x="24.4" y="68.8" textLength="24.4" clip-path="url(#terminal-800550482-line-2)">配置</text><text class="terminal-800550482-r3" x="97.6" y="68.8" textLength="36.6" clip-path="url(#terminal-800550482-line-2)">提示词</text><text class="terminal-800550482-r4" x="195.2" y="68.8" textLength="24.4" clip-path="url(#terminal-800550482-line-2)">主题</text><text class="terminal-800550482-r1" x="1903.2" y="68.8" textLength="12.2" clip-path="url(#terminal-800550482-line-2)">
</text><text class="terminal-800550482-r5" x="12.2" y="93.2" textLength="170.8" clip-path="url(#terminal-800550482-line-3)">━━━━━━━━━━━━━━</text><text class="terminal-800550482-r5" x="183" y="93.2" textLength="12.2" clip-path="url(#terminal-800550482-line-3)">╸</text><text class="terminal-800550482-r6" x="195.2" y="93.2" textLength="48.8" clip-path="url(#terminal-800550482-line-3)">━━━━</text><text class="terminal-800550482-r5" x="244" y="93.2" textLength="12.2" clip-path="url(#terminal-800550482-line-3)">╺</text><text class="terminal-800550482-r5" x="256.2" y="93.2" textLength="1634.8" clip-path="url(#terminal-800550482-line-3)">━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━</text><text class="terminal-800550482-r1" x="1903.2" y="93.2" textLength="12.2" clip-path="url(#terminal-800550482-line-3)">
</text><text class="terminal-800550482-r7" x="12.2" y="117.6" textLength="48.8" clip-path="url(#terminal-800550482-line-4)">主题管理</text><text class="terminal-800550482-r1" x="1903.2" y="117.6" textLength="12.2" clip-path="url(#terminal-800550482-line-4)">
</text><text class="terminal-800550482-r1" x="1903.2" y="142" textLength="12.2" clip-path="url(#terminal-800550482-line-5)">
</text><text class="terminal-800550482-r8" x="12.2" y="166.4" textLength="61" clip-path="url(#terminal-800550482-line-6)">当前主题:</text><text class="terminal-800550482-r1" x="1903.2" y="166.4" textLength="12.2" clip-path="url(#terminal-800550482-line-6)">
</text><text class="terminal-800550482-r9" x="12.2" y="190.8" textLength="12.2" clip-path="url(#terminal-800550482-line-7)">┌</text><text class="terminal-800550482-r9" x="24.4" y="190.8" textLength="1854.4" clip-path="url(#terminal-800550482-line-7)">────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────</text><text class="terminal-800550482-r9" x="1878.8" y="190.8" textLength="12.2" clip-path="url(#terminal-800550482-line-7)">┐</text><text class="terminal-800550482-r1" x="1903.2" y="190.8" textLength="12.2" clip-path="url(#terminal-800550482-line-7)">
</text><text class="terminal-800550482-r9" x="12.2" y="215.2" textLength="12.2" clip-path="url(#terminal-800550482-line-8)">│</text><text class="terminal-800550482-r2" x="36.6" y="215.2" textLength="219.6" clip-path="url(#terminal-800550482-line-8)">当前使用:&#160;textual-dark</text><text class="terminal-800550482-r9" x="1878.8" y="215.2" textLength="12.2" clip-path="url(#terminal-800550482-line-8)">│</text><text class="terminal-800550482-r1" x="1903.2" y="215.2" textLength="12.2" clip-path="url(#terminal-800550482-line-8)">
</text><text class="terminal-800550482-r9" x="12.2" y="239.6" textLength="12.2" clip-path="url(#terminal-800550482-line-9)">│</text><text class="terminal-800550482-r2" x="36.6" y="239.6" textLength="146.4" clip-path="url(#terminal-800550482-line-9)">配置保存:&#160;使用默认主题</text><text class="terminal-800550482-r9" x="1878.8" y="239.6" textLength="12.2" clip-path="url(#terminal-800550482-line-9)">│</text><text class="terminal-800550482-r1" x="1903.2" y="239.6" textLength="12.2" clip-path="url(#terminal-800550482-line-9)">
</text><text class="terminal-800550482-r9" x="12.2" y="264" textLength="12.2" clip-path="url(#terminal-800550482-line-10)">└</text><text class="terminal-800550482-r9" x="24.4" y="264" textLength="1854.4" clip-path="url(#terminal-800550482-line-10)">────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────</text><text class="terminal-800550482-r9" x="1878.8" y="264" textLength="12.2" clip-path="url(#terminal-800550482-line-10)">┘</text><text class="terminal-800550482-r1" x="1903.2" y="264" textLength="12.2" clip-path="url(#terminal-800550482-line-10)">
</text><text class="terminal-800550482-r1" x="1903.2" y="288.4" textLength="12.2" clip-path="url(#terminal-800550482-line-11)">
</text><text class="terminal-800550482-r8" x="12.2" y="312.8" textLength="85.4" clip-path="url(#terminal-800550482-line-12)">可用主题列表:</text><text class="terminal-800550482-r1" x="1903.2" y="312.8" textLength="12.2" clip-path="url(#terminal-800550482-line-12)">
</text><text class="terminal-800550482-r9" x="12.2" y="337.2" textLength="12.2" clip-path="url(#terminal-800550482-line-13)">┌</text><text class="terminal-800550482-r9" x="24.4" y="337.2" textLength="1854.4" clip-path="url(#terminal-800550482-line-13)">────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────</text><text class="terminal-800550482-r9" x="1878.8" y="337.2" textLength="12.2" clip-path="url(#terminal-800550482-line-13)">┐</text><text class="terminal-800550482-r1" x="1903.2" y="337.2" textLength="12.2" clip-path="url(#terminal-800550482-line-13)">
</text><text class="terminal-800550482-r9" x="12.2" y="361.6" textLength="12.2" clip-path="url(#terminal-800550482-line-14)">│</text><text class="terminal-800550482-r9" x="24.4" y="361.6" textLength="12.2" clip-path="url(#terminal-800550482-line-14)">┌</text><text class="terminal-800550482-r9" x="36.6" y="361.6" textLength="1805.6" clip-path="url(#terminal-800550482-line-14)">────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────</text><text class="terminal-800550482-r9" x="1842.2" y="361.6" textLength="12.2" clip-path="url(#terminal-800550482-line-14)">┐</text><text class="terminal-800550482-r9" x="1878.8" y="361.6" textLength="12.2" clip-path="url(#terminal-800550482-line-14)">│</text><text class="terminal-800550482-r1" x="1903.2" y="361.6" textLength="12.2" clip-path="url(#terminal-800550482-line-14)">
</text><text class="terminal-800550482-r9" x="12.2" y="386" textLength="12.2" clip-path="url(#terminal-800550482-line-15)">│</text><text class="terminal-800550482-r9" x="24.4" y="386" textLength="12.2" clip-path="url(#terminal-800550482-line-15)">│</text><text class="terminal-800550482-r2" x="48.8" y="386" textLength="61" clip-path="url(#terminal-800550482-line-15)">可用主题:</text><text class="terminal-800550482-r9" x="1842.2" y="386" textLength="12.2" clip-path="url(#terminal-800550482-line-15)">│</text><text class="terminal-800550482-r9" x="1878.8" y="386" textLength="12.2" clip-path="url(#terminal-800550482-line-15)">│</text><text class="terminal-800550482-r1" x="1903.2" y="386" textLength="12.2" clip-path="url(#terminal-800550482-line-15)">
</text><text class="terminal-800550482-r9" x="12.2" y="410.4" textLength="12.2" clip-path="url(#terminal-800550482-line-16)">│</text><text class="terminal-800550482-r9" x="24.4" y="410.4" textLength="12.2" clip-path="url(#terminal-800550482-line-16)">│</text><text class="terminal-800550482-r2" x="48.8" y="410.4" textLength="195.2" clip-path="url(#terminal-800550482-line-16)">&#160;&#160;•&#160;textual-dark</text><text class="terminal-800550482-r9" x="1842.2" y="410.4" textLength="12.2" clip-path="url(#terminal-800550482-line-16)">│</text><text class="terminal-800550482-r9" x="1878.8" y="410.4" textLength="12.2" clip-path="url(#terminal-800550482-line-16)">│</text><text class="terminal-800550482-r1" x="1903.2" y="410.4" textLength="12.2" clip-path="url(#terminal-800550482-line-16)">
</text><text class="terminal-800550482-r9" x="12.2" y="434.8" textLength="12.2" clip-path="url(#terminal-800550482-line-17)">│</text><text class="terminal-800550482-r9" x="24.4" y="434.8" textLength="12.2" clip-path="url(#terminal-800550482-line-17)">│</text><text class="terminal-800550482-r2" x="48.8" y="434.8" textLength="207.4" clip-path="url(#terminal-800550482-line-17)">&#160;&#160;•&#160;textual-light</text><text class="terminal-800550482-r9" x="1842.2" y="434.8" textLength="12.2" clip-path="url(#terminal-800550482-line-17)">│</text><text class="terminal-800550482-r9" x="1878.8" y="434.8" textLength="12.2" clip-path="url(#terminal-800550482-line-17)">│</text><text class="terminal-800550482-r1" x="1903.2" y="434.8" textLength="12.2" clip-path="url(#terminal-800550482-line-17)">
</text><text class="terminal-800550482-r9" x="12.2" y="459.2" textLength="12.2" clip-path="url(#terminal-800550482-line-18)">│</text><text class="terminal-800550482-r9" x="24.4" y="459.2" textLength="12.2" clip-path="url(#terminal-800550482-line-18)">│</text><text class="terminal-800550482-r2" x="48.8" y="459.2" textLength="97.6" clip-path="url(#terminal-800550482-line-18)">&#160;&#160;•&#160;nord</text><text class="terminal-800550482-r9" x="1842.2" y="459.2" textLength="12.2" clip-path="url(#terminal-800550482-line-18)">│</text><text class="terminal-800550482-r9" x="1878.8" y="459.2" textLength="12.2" clip-path="url(#terminal-800550482-line-18)">│</text><text class="terminal-800550482-r1" x="1903.2" y="459.2" textLength="12.2" clip-path="url(#terminal-800550482-line-18)">
</text><text class="terminal-800550482-r9" x="12.2" y="483.6" textLength="12.2" clip-path="url(#terminal-800550482-line-19)">│</text><text class="terminal-800550482-r9" x="24.4" y="483.6" textLength="12.2" clip-path="url(#terminal-800550482-line-19)">│</text><text class="terminal-800550482-r2" x="48.8" y="483.6" textLength="134.2" clip-path="url(#terminal-800550482-line-19)">&#160;&#160;•&#160;gruvbox</text><text class="terminal-800550482-r9" x="1842.2" y="483.6" textLength="12.2" clip-path="url(#terminal-800550482-line-19)">│</text><text class="terminal-800550482-r9" x="1878.8" y="483.6" textLength="12.2" clip-path="url(#terminal-800550482-line-19)">│</text><text class="terminal-800550482-r1" x="1903.2" y="483.6" textLength="12.2" clip-path="url(#terminal-800550482-line-19)">
</text><text class="terminal-800550482-r9" x="12.2" y="508" textLength="12.2" clip-path="url(#terminal-800550482-line-20)">│</text><text class="terminal-800550482-r9" x="24.4" y="508" textLength="12.2" clip-path="url(#terminal-800550482-line-20)">│</text><text class="terminal-800550482-r2" x="48.8" y="508" textLength="244" clip-path="url(#terminal-800550482-line-20)">&#160;&#160;•&#160;catppuccin-mocha</text><text class="terminal-800550482-r9" x="1842.2" y="508" textLength="12.2" clip-path="url(#terminal-800550482-line-20)">│</text><text class="terminal-800550482-r9" x="1878.8" y="508" textLength="12.2" clip-path="url(#terminal-800550482-line-20)">│</text><text class="terminal-800550482-r1" x="1903.2" y="508" textLength="12.2" clip-path="url(#terminal-800550482-line-20)">
</text><text class="terminal-800550482-r9" x="12.2" y="532.4" textLength="12.2" clip-path="url(#terminal-800550482-line-21)">│</text><text class="terminal-800550482-r9" x="24.4" y="532.4" textLength="12.2" clip-path="url(#terminal-800550482-line-21)">│</text><text class="terminal-800550482-r2" x="48.8" y="532.4" textLength="195.2" clip-path="url(#terminal-800550482-line-21)">&#160;&#160;•&#160;textual-ansi</text><text class="terminal-800550482-r9" x="1842.2" y="532.4" textLength="12.2" clip-path="url(#terminal-800550482-line-21)">│</text><text class="terminal-800550482-r9" x="1878.8" y="532.4" textLength="12.2" clip-path="url(#terminal-800550482-line-21)">│</text><text class="terminal-800550482-r1" x="1903.2" y="532.4" textLength="12.2" clip-path="url(#terminal-800550482-line-21)">
</text><text class="terminal-800550482-r9" x="12.2" y="556.8" textLength="12.2" clip-path="url(#terminal-800550482-line-22)">│</text><text class="terminal-800550482-r9" x="24.4" y="556.8" textLength="12.2" clip-path="url(#terminal-800550482-line-22)">│</text><text class="terminal-800550482-r2" x="48.8" y="556.8" textLength="134.2" clip-path="url(#terminal-800550482-line-22)">&#160;&#160;•&#160;dracula</text><text class="terminal-800550482-r9" x="1842.2" y="556.8" textLength="12.2" clip-path="url(#terminal-800550482-line-22)">│</text><text class="terminal-800550482-r9" x="1878.8" y="556.8" textLength="12.2" clip-path="url(#terminal-800550482-line-22)">│</text><text class="terminal-800550482-r1" x="1903.2" y="556.8" textLength="12.2" clip-path="url(#terminal-800550482-line-22)">
</text><text class="terminal-800550482-r9" x="12.2" y="581.2" textLength="12.2" clip-path="url(#terminal-800550482-line-23)">│</text><text class="terminal-800550482-r9" x="24.4" y="581.2" textLength="12.2" clip-path="url(#terminal-800550482-line-23)">│</text><text class="terminal-800550482-r2" x="48.8" y="581.2" textLength="183" clip-path="url(#terminal-800550482-line-23)">&#160;&#160;•&#160;tokyo-night</text><text class="terminal-800550482-r9" x="1842.2" y="581.2" textLength="12.2" clip-path="url(#terminal-800550482-line-23)">│</text><text class="terminal-800550482-r9" x="1878.8" y="581.2" textLength="12.2" clip-path="url(#terminal-800550482-line-23)">│</text><text class="terminal-800550482-r1" x="1903.2" y="581.2" textLength="12.2" clip-path="url(#terminal-800550482-line-23)">
</text><text class="terminal-800550482-r9" x="12.2" y="605.6" textLength="12.2" clip-path="url(#terminal-800550482-line-24)">│</text><text class="terminal-800550482-r9" x="24.4" y="605.6" textLength="12.2" clip-path="url(#terminal-800550482-line-24)">│</text><text class="terminal-800550482-r2" x="48.8" y="605.6" textLength="134.2" clip-path="url(#terminal-800550482-line-24)">&#160;&#160;•&#160;monokai</text><text class="terminal-800550482-r9" x="1842.2" y="605.6" textLength="12.2" clip-path="url(#terminal-800550482-line-24)">│</text><text class="terminal-800550482-r11" x="1854.4" y="605.6" textLength="24.4" clip-path="url(#terminal-800550482-line-24)">▆▆</text><text class="terminal-800550482-r9" x="1878.8" y="605.6" textLength="12.2" clip-path="url(#terminal-800550482-line-24)">│</text><text class="terminal-800550482-r1" x="1903.2" y="605.6" textLength="12.2" clip-path="url(#terminal-800550482-line-24)">
</text><text class="terminal-800550482-r9" x="12.2" y="630" textLength="12.2" clip-path="url(#terminal-800550482-line-25)">│</text><text class="terminal-800550482-r9" x="24.4" y="630" textLength="12.2" clip-path="url(#terminal-800550482-line-25)">│</text><text class="terminal-800550482-r2" x="48.8" y="630" textLength="134.2" clip-path="url(#terminal-800550482-line-25)">&#160;&#160;•&#160;flexoki</text><text class="terminal-800550482-r9" x="1842.2" y="630" textLength="12.2" clip-path="url(#terminal-800550482-line-25)">│</text><text class="terminal-800550482-r9" x="1878.8" y="630" textLength="12.2" clip-path="url(#terminal-800550482-line-25)">│</text><text class="terminal-800550482-r1" x="1903.2" y="630" textLength="12.2" clip-path="url(#terminal-800550482-line-25)">
</text><text class="terminal-800550482-r9" x="12.2" y="654.4" textLength="12.2" clip-path="url(#terminal-800550482-line-26)">│</text><text class="terminal-800550482-r9" x="24.4" y="654.4" textLength="12.2" clip-path="url(#terminal-800550482-line-26)">│</text><text class="terminal-800550482-r2" x="48.8" y="654.4" textLength="244" clip-path="url(#terminal-800550482-line-26)">&#160;&#160;•&#160;catppuccin-latte</text><text class="terminal-800550482-r9" x="1842.2" y="654.4" textLength="12.2" clip-path="url(#terminal-800550482-line-26)">│</text><text class="terminal-800550482-r9" x="1878.8" y="654.4" textLength="12.2" clip-path="url(#terminal-800550482-line-26)">│</text><text class="terminal-800550482-r1" x="1903.2" y="654.4" textLength="12.2" clip-path="url(#terminal-800550482-line-26)">
</text><text class="terminal-800550482-r9" x="12.2" y="678.8" textLength="12.2" clip-path="url(#terminal-800550482-line-27)">│</text><text class="terminal-800550482-r9" x="24.4" y="678.8" textLength="12.2" clip-path="url(#terminal-800550482-line-27)">│</text><text class="terminal-800550482-r2" x="48.8" y="678.8" textLength="231.8" clip-path="url(#terminal-800550482-line-27)">&#160;&#160;•&#160;solarized-light</text><text class="terminal-800550482-r9" x="1842.2" y="678.8" textLength="12.2" clip-path="url(#terminal-800550482-line-27)">│</text><text class="terminal-800550482-r9" x="1878.8" y="678.8" textLength="12.2" clip-path="url(#terminal-800550482-line-27)">│</text><text class="terminal-800550482-r1" x="1903.2" y="678.8" textLength="12.2" clip-path="url(#terminal-800550482-line-27)">
</text><text class="terminal-800550482-r9" x="12.2" y="703.2" textLength="12.2" clip-path="url(#terminal-800550482-line-28)">│</text><text class="terminal-800550482-r9" x="24.4" y="703.2" textLength="12.2" clip-path="url(#terminal-800550482-line-28)">│</text><text class="terminal-800550482-r2" x="48.8" y="703.2" textLength="219.6" clip-path="url(#terminal-800550482-line-28)">&#160;&#160;•&#160;solarized-dark</text><text class="terminal-800550482-r9" x="1842.2" y="703.2" textLength="12.2" clip-path="url(#terminal-800550482-line-28)">│</text><text class="terminal-800550482-r9" x="1878.8" y="703.2" textLength="12.2" clip-path="url(#terminal-800550482-line-28)">│</text><text class="terminal-800550482-r1" x="1903.2" y="703.2" textLength="12.2" clip-path="url(#terminal-800550482-line-28)">
</text><text class="terminal-800550482-r9" x="12.2" y="727.6" textLength="12.2" clip-path="url(#terminal-800550482-line-29)">└</text><text class="terminal-800550482-r9" x="24.4" y="727.6" textLength="1854.4" clip-path="url(#terminal-800550482-line-29)">────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────</text><text class="terminal-800550482-r9" x="1878.8" y="727.6" textLength="12.2" clip-path="url(#terminal-800550482-line-29)">┘</text><text class="terminal-800550482-r1" x="1903.2" y="727.6" textLength="12.2" clip-path="url(#terminal-800550482-line-29)">
</text><text class="terminal-800550482-r1" x="1903.2" y="752" textLength="12.2" clip-path="url(#terminal-800550482-line-30)">
</text><text class="terminal-800550482-r1" x="1903.2" y="776.4" textLength="12.2" clip-path="url(#terminal-800550482-line-31)">
</text><text class="terminal-800550482-r1" x="1903.2" y="800.8" textLength="12.2" clip-path="url(#terminal-800550482-line-32)">
</text><text class="terminal-800550482-r12" x="707.6" y="825.2" textLength="195.2" clip-path="url(#terminal-800550482-line-33)">▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔</text><text class="terminal-800550482-r13" x="915" y="825.2" textLength="268.4" clip-path="url(#terminal-800550482-line-33)">▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔</text><text class="terminal-800550482-r1" x="1903.2" y="825.2" textLength="12.2" clip-path="url(#terminal-800550482-line-33)">
</text><text class="terminal-800550482-r4" x="719.8" y="849.6" textLength="97.6" clip-path="url(#terminal-800550482-line-34)">&#160;保存当前主题&#160;</text><text class="terminal-800550482-r8" x="915" y="849.6" textLength="146.4" clip-path="url(#terminal-800550482-line-34)">&#160;重置主题（使用默认）&#160;</text><text class="terminal-800550482-r1" x="1903.2" y="849.6" textLength="12.2" clip-path="url(#terminal-800550482-line-34)">
</text><text class="terminal-800550482-r14" x="707.6" y="874" textLength="195.2" clip-path="url(#terminal-800550482-line-35)">▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁</text><text class="terminal-800550482-r15" x="915" y="874" textLength="268.4" clip-path="url(#terminal-800550482-line-35)">▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁</text><text class="terminal-800550482-r1" x="1903.2" y="874" textLength="12.2" clip-path="url(#terminal-800550482-line-35)">
</text><text class="terminal-800550482-r1" x="1903.2" y="898.4" textLength="12.2" clip-path="url(#terminal-800550482-line-36)">
</text><text class="terminal-800550482-r1" x="1903.2" y="922.8" textLength="12.2" clip-path="url(#terminal-800550482-line-37)">
</text><text class="terminal-800550482-r1" x="1903.2" y="947.2" textLength="12.2" clip-path="url(#terminal-800550482-line-38)">
</text><text class="terminal-800550482-r16" x="12.2" y="971.6" textLength="353.8" clip-path="url(#terminal-800550482-line-39)">提示：使用内置的&#160;&#x27;:theme&#x27;&#160;命令可以预览和切换主题</text><text class="terminal-800550482-r1" x="1903.2" y="971.6" textLength="12.2" clip-path="url(#terminal-800550482-line-39)">
</text><text class="terminal-800550482-r1" x="1903.2" y="996" textLength="12.2" clip-path="url(#terminal-800550482-line-40)">
</text><text class="terminal-800550482-r17" x="0" y="1020.4" textLength="48.8" clip-path="url(#terminal-800550482-line-41)">&#160;^q&#160;</text><text class="terminal-800550482-r2" x="48.8" y="1020.4" textLength="36.6" clip-path="url(#terminal-800550482-line-41)">退出&#160;</text><text class="terminal-800550482-r17" x="109.8" y="1020.4" textLength="48.8" clip-path="url(#terminal-800550482-line-41)">&#160;^t&#160;</text><text class="terminal-800550482-r2" x="158.6" y="1020.4" textLength="85.4" clip-path="url(#terminal-800550482-line-41)">切换输入模式&#160;</text><text class="terminal-800550482-r17" x="317.2" y="1020.4" textLength="48.8" clip-path="url(#terminal-800550482-line-41)">&#160;^s&#160;</text><text class="terminal-800550482-r2" x="366" y="1020.4" textLength="61" clip-path="url(#terminal-800550482-line-41)">发送消息&#160;</text><text class="terminal-800550482-r17" x="475.8" y="1020.4" textLength="48.8" clip-path="url(#terminal-800550482-line-41)">&#160;^v&#160;</text><text class="terminal-800550482-r2" x="524.6" y="1020.4" textLength="36.6" clip-path="url(#terminal-800550482-line-41)">粘贴&#160;</text><text class="terminal-800550482-r18" x="1756.8" y="1020.4" textLength="12.2" clip-path="url(#terminal-800550482-line-41)">▏</text><text class="terminal-800550482-r17" x="1769" y="1020.4" textLength="24.4" clip-path="url(#terminal-800550482-line-41)">^p</text><text class="terminal-800550482-r2" x="1793.4" y="1020.4" textLength="97.6" clip-path="url(#terminal-800550482-line-41)">&#160;palette</text>
    </g>
    </g>
</svg>
</div>

一开始以为是子容器的问题，于是使用了下面这些方法来去除子容器边框：
```
.theme-info-available * {
    border: none !important;
    outline: none !important;
}

.themes-scroll-container .theme-info-available {
    border: none;
}

.themes-scroll-container .theme-info-available * {
    border: none !important;
}
```

但是这些方案并没有任何左右，直到我注释了父容器的before部分，发现父容器的边框消失了，但子容器边框还在，这说明子边框很可能是父容器搞的鬼。
```
/*父容器边框消失，子容器边框还在*/
    .themes-scroll-container {
        height: 50%;
        min-height: 10;
        margin: 0 0 1 0;
        /*border: solid $secondary;*/
        overflow-y: auto;  /* 关键属性 */
    }
```

于是我又尝试了下面的css，结果父容器和子容器边框全部消失。
```
    .themes-scroll-container * {
        height: 50%;
        min-height: 10;
        margin: 0 0 1 0;
        border: none !important;
        /*border: solid $secondary;*/
        overflow-y: auto;  /* 关键属性 */
    }
```

我在研究期间一直和ai一直找各种原因，在发现强制禁用父容器边框会导致子容器边框消失后我把这一信息发给了ai，ai给了我下面的css：
```
    .themes-scroll-container {
        height: 50%;
        min-height: 10;
        margin: 0 0 1 0;
        border: solid $secondary;
        overflow-y: auto;  /* 关键属性 */
    }

    .themes-scroll-container * {
        border: none !important;
    }
    
    .theme-info-available {
    }
```
结果真的达到效果，Static的边框真的被去除了。

# 原理和解释
后面我也是意想不到，居然要两个`.themes-scroll-container`，只不过一个又通配符，一个没有。
## 两个样式的原因
AI对写两次的解释是这样的：
> 第一个 .themes-scroll-container → 移除容器自己的边框
> 第二个 .themes-scroll-container * → 移除所有后代元素的边框
## 我对父容器会让子容器的边框渲染的原因
后面我又问了AI`为什么这个父容器会让子容器带上边框`，但是我觉得AI的解释有些存疑，所有我先来阐述一下我自己的理解，我觉得就是因为一些未知原因，父容器的带有边框的属性会导致子容器有一个“边框属性”，但这个“边框属性”实际是父容器的，所以在对`.themes-scroll-container`的样式设定好后再使用`.themes-scroll-container * {border: none !important;}`就会导致子容器的父容器边框属性被去除从而导致其没有边框。

为什么我认为AI的解释存疑，是因为再去除`.themes-scroll-container`里`border: solid $secondary;`的`$secondary`后，容器边框颜色变成了绿色，但里面的Static还是蓝色，但AI说的验证方法有给父容器加上颜色，但是在刚才说的情况容器边框和子控件边框颜色不一致，所以我认为存疑。

## AI对我对父容器会让子容器的边框渲染的原因
下面是AI对这个问题的解释：

> 这是个很好的问题！父容器本身**不会**让子容器带上边框，但 Textual 的渲染机制导致了这个**视觉错觉**。
> 
> ## 真正的原因
> 
> ### 1. 父容器的边框"包裹"了子容器
> 
> ```
> ┌─────────────────────────────┐ ← 父容器的边框
> │  ┌─────────────────────┐    │
> │  │ 子容器的内容区域     │    │
> │  └─────────────────────┘    │
> └─────────────────────────────┘
> ```
> 
> 父容器的边框是画在**最外层**的，它会包围所有子元素。从视觉上看，边框好像"属于"子容器，实际上是父容器在包围它。
> 
> ### 2. Textual 的盒模型
> 
> 在 Textual 中，每个组件都可能有自己的 `border`。当你看到子容器有边框时，可能是：
> 
> - **父容器的边框**（最常见）
> - **子容器自己的边框**
> - **兄弟元素的边框**（相邻 margin 合并）
> 
> ### 3. 你遇到的问题特殊在哪
> 
> 你的 `.theme-info-available` **本身没有边框**，但：
> - 它的父容器 `.themes-scroll-container` 有边框
> - 父容器的边框加上背景色、内边距等效果，看起来像是子容器的边框
> 
> ## 验证方法
> 
> ```css
> /* 临时给父容器一个明显的不同颜色 */
> .themes-scroll-container {
>     border: solid red;  /* 红色边框 */
> }
> 
> /* 子容器无边框 */
> .theme-info-available {
>     border: none;
> }
> ```
> 
> 你会看到红色边框画在**最外面**，包裹着整个子容器区域。
> 
> ## 为什么 `*` 通配符解决了问题？
> 
> ```css
> .themes-scroll-container * {
>     border: none !important;
> }
> ```
> 
> 这个选择器移除了**所有后代元素**的边框，但**不包括父容器自身**。如果你还看到边框，说明：
> 1. 要么父容器还有边框
> 2. 要么还有更深层的隐藏元素有边框
> 
> ## 总结
> 
> | 你以为是 | 实际上是 |
> |---------|---------|
> | 子容器有边框 | 父容器包围子容器 |
> | 给子容器设 `border: none` 无效 | 你看到的是父容器的边框 |
> | 给父容器也设 `border: none` | 父容器边框消失 |
> 
> 所以最终你需要**同时处理父容器和所有后代**：
> 
> ```css
> .themes-scroll-container,
> .themes-scroll-container * {
>     border: none !important;
> }
> ```
> 
> 这样才能**彻底清除**这个视觉上的"边框效果"。
