### 在线数学公式编辑 
- ### [`Latex`](https://www.latexlive.com/home)  
## 1. 关于 LaTeX 公式编辑 Introduce

**LaTeX**（常被读作/ˈlɑːtɛk/或/ˈleɪtɛk/，正确读音:/ˈlɑːtɛx/音译：拉泰赫，写作 $\LaTeX$），是一种基于 TeX 的排版系统，由美国计算机科学家[莱斯利·兰伯特](https://zh.wikipedia.org/wiki/莱斯利·兰波特)在 20 世纪 80 年代初期开发。 **MathJax**是一个跨浏览器的 JavaScript 库，它使用 MathML、LaTeX 和 ASCIIMathML 标记在 Web 浏览器中显示数学符号。本页面是基于 [MathJax](https://www.mathjax.org/) 实现的便捷 LaTeX 公式编辑器，支持导出 SVG 矢量图、高清 PNG 位图、MathML 代码以及 SVGCode，并且可根据需要自定义加载 TeX 扩展包，实现功能拓展。

#### 1.1 基本使用 Basic

在本页面输入框中输入的公式**不用**放在 `<math>` 与 `</math>`，或 `$` 与 `$` 之间，直接输入相关 LaTeX代码即可。

在输出框您可以看到即时渲染出来效果，方便进行代码修改。

本页面已添加【代码高亮】与【自动补全】功能，默认设置为打开状态。但考虑到性能影响，您可自行在【设置】中关闭相关功能。

本页面现有 4 款颜色主题模式，您可根据自己的喜好，在【设置】中进行主题切换。

本页面已做多平台适配，如您需要，也可以在除 PC 和 Mac 之外的，iPad、ios、Android 平台使用（注：考虑到性能影响，移动端部分功能会受到影响）。

以下字符在 LaTeX 环境中是保留字符，它们具有特殊含义，只可以特定语法中起作用，所以并不能在输入框中直接输入它们（会报错或者不会渲染）

```
# % ^ & _ { } ~ \
```

如您因其他原因需要直接显示它们，请在其前面加入 `\` 反斜杠或其它转义符。

```
\# \% ^\wedge \& \_ \{ \} \sim \backslash
```

$$ \# \% ^\wedge \& \_ \{ \} \sim \backslash $$

关于 LaTeX 代码部分请参考下一章节。

**注意：**本页面不支持文档编辑环境，因此不支持调用 `\begin{document}` 等相关命令，默认即为数学环境，可直接输入数学公式。



#### 1.2 关于渲染 Render

本页面采用 MathJax-tex-svg 显示数学符号，支持五种格式导出。



##### 1.2.1 导出 SVG

SVG 全称**S**calable **V**ector **G**raphics（可缩放矢量图形），是一种基于可扩展标记语言（XML），用于描述二维矢量图形的图形格式，标准由 W 3 C 制定，是一个开放标准。

我们可以简单理解为，SVG 是一种与图像分辨率无关的矢量格式的拓展名，因此 SVG 文件可以直接拖入**AI、PS**等绘图软件中进行相应编辑、修改，以满足任意尺寸需求。



##### 1.2.2 导出 PNG

PNG 全称**P**ortable **N**etwork **G**raphics（便携式网络图形），是一种无损压缩的**位图**图形格式。

因此 PNG 与图像分辨率有关，本页面导出的 PNG 分辨率为 4 K 裁切标准（3840 x 2160），也可以满足绝大部分的文档需求。IOS 端若出现无法保存图片的现象，请手动打开浏览器访问照片的权限。



##### 1.2.3 导出 JPG

JPEG 全称**J**oint **P**hotograghic **E**xperts **G**roup（联合图像专家小组），是一种针对照片影像而广泛使用的**有损压缩**标准方法。**JPG**为使用 JPEG 方法压缩后的图片文件格式。

本页面提供白底 JPG 图片下载，大小为 4 K 裁切标准（3840 x 2160）。IOS 端若出现无法保存图片的现象，请手动打开浏览器访问照片的权限。



##### 1.2.4 导出 MathML

MathML 全称**Math**ematical **M**arkup **L**anguage（数学标记语言），是一种基于可扩展标记语言（XML）的标准，用来描述数学符号和公式。现已获得**HTML 5**和大部分**办公软件**与**数学软件**的支持，例如 Microsoft Office、LibreOffice、Mathematica、Maple 等，这意味着，您只需将**MathML 代码**复制进 Microsoft Word 当中，便会自动转换成 Word 支持的 LaTeX 公式，并可进行相应后续编辑。



##### 1.2.5 导出 SVG Code

SVGCode 是矢量图数据编码，用 svg 标签表示，可以直接粘贴在 html 文档内显示。



##### 1.2.6 导出转义 LaTeX 字符

该功能是将需要转义的字符进行转义，用于 JSON 或其他需要转义的场合。例如将 `\` 转义为 `\\` 等。



##### 1.2.7 ShareURL

通过该功能可以将已经编辑好的公式快速分享给好友，好友只需将获得的 url 地址复制到浏览器的地址栏中访问即可。



#### 1.3 关于图片 OCR 公式识别 OCR

支持 jpg 或 png 格式的公式图片识别，点击工具栏中的【图片识别】标签，再点击【选择图片】，在弹出的对话框中选择想要识别的公式图片，即可在输入栏中获得该公式的 latex 代码。

**注：**上传的公式图片须为正向。方向颠倒的公式会严重影响 OCR 识别的准确度。

 



## 2. 数学公式编辑 Displaying a formula



#### 2.1 符号与字母 Symbol and Alphabet



##### 2.1.1 希腊字母 Greek alphabet

| 序号 |     小写      | LaTeX       | 读音                   | 序号 |    大写    | LaTeX    | 读音        |
| :--: | :-----------: | :---------- | :--------------------- | :--: | :--------: | :------- | :---------- |
|  1   |   $\alpha$    | \alpha      | /ˈælfə/                |  31  |  $\Gamma$  | \Gamma   | /ˈɡæmə/     |
|  2   |    $\beta$    | \beta       | /ˈbiːtə/, US: /ˈbeɪtə/ |  32  |  $\Delta$  | \Delta   | /ˈdɛltə/    |
|  3   |   $\gamma$    | \gamma      | /ˈɡæmə/                |  33  |  $\Theta$  | \Theta   | /ˈθiːtə/    |
|  4   |   $\delta$    | \delta      | /ˈdɛltə/               |  34  | $\Lambda$  | \Lambda  | /ˈlæmdə/    |
|  5   |  $\epsilon$   | \epsilon    | /ˈɛpsɪlɒn/             |  35  |   $\Xi$    | \Xi      | /zaɪ, ksaɪ/ |
|  6   | $\varepsilon$ | \varepsilon | /ˈɛpsɪlɒn/             |  36  |   $\Pi$    | \Pi      | /paɪ/       |
|  7   |    $\zeta$    | \zeta       | /ˈzeɪtə/               |  37  |  $\Sigma$  | \Sigma   | /ˈsɪɡmə/    |
|  8   |    $\eta$     | \eta        | /ˈeɪtə/                |  38  | $\Upsilon$ | \Upsilon | /ˈʌpsɪlɒn/  |
|  9   |   $\theta$    | \theta      | /ˈθiːtə/               |  39  |   $\Phi$   | \Phi     | /faɪ/       |
|  10  |  $\vartheta$  | \vartheta   | /ˈθiːtə/               |  40  |   $\Psi$   | \Psi     | /psaɪ/      |
|  11  |    $\iota$    | \iota       | /aɪˈoʊtə/              |  41  |  $\Omega$  | \Omega   | /oʊˈmeɪɡə/  |
|  12  |   $\kappa$    | \kappa      | /ˈkæpə/                |      |            |          |             |
|  13  |   $\lambda$   | \lambda     | /ˈlæmdə/               |      |            |          |             |
|  14  |     $\mu$     | \mu         | /mjuː/                 |      |            |          |             |
|  15  |     $\nu$     | \nu         | /njuː/                 |      |            |          |             |
|  16  |     $\xi$     | \xi         | /zaɪ, ksaɪ/            |      |            |          |             |
|  17  |      $o$      | o           | /ˈɒmɪkrɒn/             |      |            |          |             |
|  18  |     $\pi$     | \pi         | /paɪ/                  |      |            |          |             |
|  19  |   $\varpi$    | \varpi      | /paɪ/                  |      |            |          |             |
|  20  |    $\rho$     | \rho        | /roʊ/                  |      |            |          |             |
|  21  |   $\varrho$   | \varrho     | /roʊ/                  |      |            |          |             |
|  22  |   $\sigma$    | \sigma      | /ˈsɪɡmə/               |      |            |          |             |
|  23  |  $\varsigma$  | \varsigma   | /ˈsɪɡmə/               |      |            |          |             |
|  24  |    $\tau$     | \tau        | /taʊ, tɔː/             |      |            |          |             |
|  25  |  $\upsilon$   | \upsilon    | /ˈʌpsɪlɒn/             |      |            |          |             |
|  26  |    $\phi$     | \phi        | /faɪ/                  |      |            |          |             |
|  27  |   $\varphi$   | \varphi     | /faɪ/                  |      |            |          |             |
|  28  |    $\chi$     | \chi        | /kaɪ/                  |      |            |          |             |
|  29  |    $\psi$     | \psi        | /psaɪ/                 |      |            |          |             |
|  30  |   $\omega$    | \omega      | /oʊˈmeɪɡə/             |      |            |          |             |

**注意:** MathJax 支持的大写希腊字母有限，如需其他（如大写 Alpha），可使用**罗马体**转换，如 `\mathrm{A}` 表示大写 Alpha：$\mathrm{A}$。



##### 2.1.2 希伯来字母 Hebrew alphabet

| 序号 |   图标    | LaTeX   | 英文   |
| :--: | :-------: | :------ | :----- |
|  1   | $\aleph$  | \aleph  | aleph  |
|  2   |  $\beth$  | \beth   | beth   |
|  3   | $\gimel$  | \gimel  | gimel  |
|  4   | $\daleth$ | \daleth | daleth |



##### 2.1.3 二元运算符 Binary operations

| 序号 |       图标       | LaTeX                            | 序号 |        图标        | LaTeX            |
| :--: | :--------------: | :------------------------------- | :--: | :----------------: | :--------------- |
|  1   |       $+$        | +                                |  20  |     $\bullet$      | \bullet          |
|  2   |       $-$        | -                                |  21  |      $\oplus$      | \oplus           |
|  3   |     $\times$     | \times                           |  22  |     $\ominus$      | \ominus          |
|  4   |                  | \div (在 physics 扩展开启状态下为) |  23  |      $\odot$       | \odot            |
|  5   |      $\pm$       | \pm                              |  24  |     $\oslash$      | \oslash          |
|  6   |      $\mp$       | \mp                              |  25  |     $\otimes$      | \otimes          |
|  7   | $\triangleleft$  | \triangleleft                    |  26  |     $\bigcirc$     | \bigcirc         |
|  8   | $\triangleright$ | \triangleright                   |  27  |     $\diamond$     | \diamond         |
|  9   |     $\cdot$      | \cdot                            |  28  |      $\uplus$      | \uplus           |
|  10  |   $\setminus$    | \setminus                        |  29  |  $\bigtriangleup$  | \bigtriangleup   |
|  11  |     $\star$      | \star                            |  30  | $\bigtriangledown$ | \bigtriangledown |
|  12  |      $\ast$      | \ast                             |  31  |       $\lhd$       | \lhd             |
|  13  |      $\cup$      | \cup                             |  32  |       $\rhd$       | \rhd             |
|  14  |      $\cap$      | \cap                             |  33  |      $\unlhd$      | \unlhd           |
|  15  |     $\sqcup$     | \sqcup                           |  34  |      $\unrhd$      | \unrhd           |
|  16  |     $\sqcap$     | \sqcap                           |  35  |      $\amalg$      | \amalg           |
|  17  |      $\vee$      | \vee                             |  36  |       $\wr$        | \wr              |
|  18  |     $\wedge$     | \wedge                           |  37  |     $\dagger$      | \dagger          |
|  19  |     $\circ$      | \circ                            |  38  |     $\ddagger$     | \ddagger         |

##### 2.1.4 二元关系符 Binary relations

| 序号 |                   图标                   | LaTeX                                  | 序号 |      图标      | LaTeX        |
| :--: | :--------------------------------------: | :------------------------------------- | :--: | :------------: | :----------- |
|  1   |                   $=$                    | =                                      |  49  |    $\gneq$     | \gneq        |
|  2   |                  $\ne$                   | \ne                                    |  50  |    $\geqq$     | \geqq        |
|  3   |                  $\neq$                  | \neq                                   |  51  |    $\ngeq$     | \ngeq        |
|  4   |                 $\equiv$                 | \equiv                                 |  52  |    $\ngeqq$    | \ngeqq       |
|  5   |               $\not\equiv$               | \not\equiv                             |  53  |    $\gneqq$    | \gneqq       |
|  6   |                 $\doteq$                 | \doteq                                 |  54  |  $\gvertneqq$  | \gvertneqq   |
|  7   |               $\doteqdot$                | \doteqdot                              |  55  |   $\lessgtr$   | \lessgtr     |
|  8   | $\overset{\underset{\mathrm{def}}{}}{=}$ | \overset{\underset{\mathrm{def}}{}}{=} |  56  |  $\lesseqgtr$  | \lesseqgtr   |
|  9   |                   $:=$                   | :=                                     |  57  | $\lesseqqgtr$  | \lesseqqgtr  |
|  10  |                  $\sim$                  | \sim                                   |  58  |   $\gtrless$   | \gtrless     |
|  11  |                 $\nsim$                  | \nsim                                  |  59  |  $\gtreqless$  | \gtreqless   |
|  12  |                $\backsim$                | \backsim                               |  60  | $\gtreqqless$  | \gtreqqless  |
|  13  |               $\thicksim$                | \thicksim                              |  61  |  $\leqslant$   | \leqslant    |
|  14  |                 $\simeq$                 | \simeq                                 |  62  |  $\nleqslant$  | \nleqslant   |
|  15  |               $\backsimeq$               | \backsimeq                             |  63  | $\eqslantless$ | \eqslantless |
|  16  |                 $\eqsim$                 | \eqsim                                 |  64  |  $\geqslant$   | \geqslant    |
|  17  |                 $\cong$                  | \cong                                  |  65  |  $\ngeqslant$  | \ngeqslant   |
|  18  |                 $\ncong$                 | \ncong                                 |  66  | $\eqslantgtr$  | \eqslantgtr  |
|  19  |                $\approx$                 | \approx                                |  67  |   $\lesssim$   | \lesssim     |
|  20  |              $\thickapprox$              | \thickapprox                           |  68  |    $\lnsim$    | \lnsim       |
|  21  |               $\approxeq$                | \approxeq                              |  69  | $\lessapprox$  | \lessapprox  |
|  22  |                 $\asymp$                 | \asymp                                 |  70  |  $\lnapprox$   | \lnapprox    |
|  23  |                $\propto$                 | \propto                                |  71  |   $\gtrsim$    | \gtrsim      |
|  24  |               $\varpropto$               | \varpropto                             |  72  |    $\gnsim$    | \gnsim       |
|  25  |                $<$< /td>                 | <                                      |  73  |  $\gtrapprox$  | \gtrapprox   |
|  26  |                 $\nless$                 | \nless                                 |  74  |  $\gnapprox$   | \gnapprox    |
|  27  |                  $\ll$                   | \ll                                    |  75  |    $\prec$     | \prec        |
|  28  |                $\not\ll$                 | \not\ll                                |  76  |    $\nprec$    | \nprec       |
|  29  |                  $\lll$                  | \lll                                   |  77  |   $\preceq$    | \preceq      |
|  30  |                $\not\lll$                | \not\lll                               |  78  |   $\npreceq$   | \npreceq     |
|  31  |                $\lessdot$                | \lessdot                               |  79  |  $\precneqq$   | \precneqq    |
|  32  |                   $>$                    | >                                      |  80  |    $\succ$     | \succ        |
|  33  |                 $\ngtr$                  | \ngtr                                  |  81  |    $\nsucc$    | \nsucc       |
|  34  |                  $\gg$                   | \gg                                    |  82  |   $\succeq$    | \succeq      |
|  35  |                $\not\gg$                 | \not\gg                                |  83  |   $\nsucceq$   | \nsucceq     |
|  36  |                  $\ggg$                  | \ggg                                   |  84  |  $\succneqq$   | \succneqq    |
|  37  |                $\not\ggg$                | \not\ggg                               |  85  | $\preccurlyeq$ | \preccurlyeq |
|  38  |                $\gtrdot$                 | \gtrdot                                |  86  | $\curlyeqprec$ | \curlyeqprec |
|  39  |                  $\le$                   | \le                                    |  87  | $\succcurlyeq$ | \succcurlyeq |
|  40  |                  $\leq$                  | \leq                                   |  88  | $\curlyeqsucc$ | \curlyeqsucc |
|  41  |                 $\lneq$                  | \lneq                                  |  89  |   $\precsim$   | \precsim     |
|  42  |                 $\leqq$                  | \leqq                                  |  90  |  $\precnsim$   | \precnsim    |
|  43  |                 $\nleq$                  | \nleq                                  |  91  | $\precapprox$  | \precapprox  |
|  44  |                 $\nleqq$                 | \nleqq                                 |  92  | $\precnapprox$ | \precnapprox |
|  45  |                 $\lneqq$                 | \lneqq                                 |  93  |   $\succsim$   | \succsim     |
|  46  |               $\lvertneqq$               | \lvertneqq                             |  94  |  $\succnsim$   | \succnsim    |
|  47  |                  $\ge$                   | \ge                                    |  95  | $\succapprox$  | \succapprox  |
|  48  |                  $\geq$                  | \geq                                   |  96  | $\succnapprox$ | \succnapprox |

##### 2.1.5 几何符号 Geometric symbols

| 序号 |       图标        | LaTeX             | 序号 |         图标          | LaTeX               |
| :--: | :---------------: | :---------------- | :--: | :-------------------: | :------------------ |
|  1   |    $\parallel$    | \parallel         |  14  |      $\lozenge$       | \lozenge            |
|  2   |   $\nparallel$    | \nparallel        |  15  |    $\blacklozenge$    | \blacklozenge       |
|  3   | $\shortparallel$  | \shortparallel    |  16  |      $\bigstar$       | \bigstar            |
|  4   | $\nshortparallel$ | \nshortparallel   |  17  |      $\bigcirc$       | \bigcirc            |
|  5   |      $\perp$      | \perp             |  18  |      $\triangle$      | \triangle           |
|  6   |     $\angle$      | \angle            |  19  |   $\bigtriangleup$    | \bigtriangleup      |
|  7   | $\sphericalangle$ | \sphericalangle   |  20  |  $\bigtriangledown$   | \bigtriangledown    |
|  8   | $\measuredangle$  | \measuredangle    |  21  |    $\vartriangle$     | \vartriangle        |
|  9   |    $45^\circ$     | 45^\circ          |  22  |    $\triangledown$    | \triangledown       |
|  10  |      $\Box$       | \Box              |  23  |   $\blacktriangle$    | \blacktriangle      |
|  11  |  $\blacksquare$   | \blacksquare      |  24  | $\blacktriangledown$  | \blacktriangledown  |
|  12  |    $\diamond$     | \diamond          |  25  | $\blacktriangleleft$  | \blacktriangleleft  |
|  13  |    $\Diamond$     | \Diamond \lozenge |  26  | $\blacktriangleright$ | \blacktriangleright |

##### 2.1.6 逻辑符号 Logic symbols

| 序号 |       图标       | LaTeX          | 序号 |          图标          | LaTeX                |
| :--: | :--------------: | :------------- | :--: | :--------------------: | :------------------- |
|  1   |    $\forall$     | \forall        |  20  |         $\neg$         | \neg                 |
|  2   |    $\exists$     | \exists        |  21  | $\not\operatorname{R}$ | \not\operatorname{R} |
|  3   |    $\nexists$    | \nexists       |  22  |         $\bot$         | \bot                 |
|  4   |   $\therefore$   | \therefore     |  23  |         $\top$         | \top                 |
|  5   |    $\because$    | \because       |  24  |        $\vdash$        | \vdash               |
|  6   |      $\And$      | \And           |  25  |        $\dashv$        | \dashv               |
|  7   |      $\lor$      | \lor           |  26  |        $\vDash$        | \vDash               |
|  8   |      $\vee$      | \vee           |  27  |        $\Vdash$        | \Vdash               |
|  9   |   $\curlyvee$    | \curlyvee      |  28  |       $\models$        | \models              |
|  10  |    $\bigvee$     | \bigvee        |  29  |       $\Vvdash$        | \Vvdash              |
|  11  |     $\land$      | \land          |  30  |       $\nvdash$        | \nvdash              |
|  12  |     $\wedge$     | \wedge         |  31  |       $\nVdash$        | \nVdash              |
|  13  |  $\curlywedge$   | \curlywedge    |  32  |       $\nvDash$        | \nvDash              |
|  14  |   $\bigwedge$    | \bigwedge      |  33  |       $\nVDash$        | \nVDash              |
|  15  |    $\bar{q}$     | \bar{q}        |  34  |      $\ulcorner$       | \ulcorner            |
|  16  |   $\bar{abc}$    | \bar{abc}      |  35  |      $\urcorner$       | \urcorner            |
|  17  |  $\overline{q}$  | \overline{q}   |  36  |      $\llcorner$       | \llcorner            |
|  18  | $\overline{abc}$ | \overline{abc} |  37  |      $\lrcorner$       | \lrcorner            |
|  19  |     $\lnot$      | \lnot          |      |                        |                      |



##### 2.1.7 集合 Sets

| 序号 |       图标       | LaTeX          | 序号 |       图标       | LaTeX          |
| :--: | :--------------: | :------------- | :--: | :--------------: | :------------- |
|  1   |      $\{\}$      | {}             |  23  |   $\sqsubset$    | \sqsubset      |
|  2   |   $\emptyset$    | \emptyset      |  24  |    $\supset$     | \supset        |
|  3   |  $\varnothing$   | \varnothing    |  25  |    $\Supset$     | \Supset        |
|  4   |      $\in$       | \in            |  26  |   $\sqsupset$    | \sqsupset      |
|  5   |     $\notin$     | \notin         |  27  |   $\subseteq$    | \subseteq      |
|  6   |      $\ni$       | \ni            |  28  |   $\nsubseteq$   | \nsubseteq     |
|  7   |      $\cap$      | \cap           |  29  |   $\subsetneq$   | \subsetneq     |
|  8   |      $\Cap$      | \Cap           |  30  | $\varsubsetneq$  | \varsubsetneq  |
|  9   |     $\sqcap$     | \sqcap         |  31  |  $\sqsubseteq$   | \sqsubseteq    |
|  10  |    $\bigcap$     | \bigcap        |  32  |   $\supseteq$    | \supseteq      |
|  11  |      $\cup$      | \cup           |  33  |   $\nsupseteq$   | \nsupseteq     |
|  12  |      $\Cup$      | \Cup           |  34  |   $\supsetneq$   | \supsetneq     |
|  13  |     $\sqcup$     | \sqcup         |  35  | $\varsupsetneq$  | \varsupsetneq  |
|  14  |    $\bigcup$     | \bigcup        |  36  |  $\sqsupseteq$   | \sqsupseteq    |
|  15  |   $\bigsqcup$    | \bigsqcup      |  37  |   $\subseteqq$   | \subseteqq     |
|  16  |     $\uplus$     | \uplus         |  38  |  $\nsubseteqq$   | \nsubseteqq    |
|  17  |   $\biguplus$    | \biguplus      |  39  |  $\subsetneqq$   | \subsetneqq    |
|  18  |   $\setminus$    | \setminus      |  40  | $\varsubsetneqq$ | \varsubsetneqq |
|  19  | $\smallsetminus$ | \smallsetminus |  41  |   $\supseteqq$   | \supseteqq     |
|  20  |     $\times$     | \times         |  42  |  $\nsupseteqq$   | \nsupseteqq    |
|  21  |    $\subset$     | \subset        |  43  |  $\supsetneqq$   | \supsetneqq    |
|  22  |    $\Subset$     | \Subset        |  44  | $\varsupsetneqq$ | \varsupsetneqq |

##### 2.1.8 箭头 Arrows

| 序号 |         图标          | LaTeX               | 序号 |          图标          | LaTeX                |
| :--: | :-------------------: | :------------------ | :--: | :--------------------: | :------------------- |
|  1   |    $\Rrightarrow$     | \Rrightarrow        |  36  |     $\longmapsto$      | \longmapsto          |
|  2   |     $\Lleftarrow$     | \Lleftarrow         |  37  |   $\rightharpoonup$    | \rightharpoonup      |
|  3   |     $\Rightarrow$     | \Rightarrow         |  38  |  $\rightharpoondown$   | \rightharpoondown    |
|  4   |    $\nRightarrow$     | \nRightarrow        |  39  |    $\leftharpoonup$    | \leftharpoonup       |
|  5   |   $\Longrightarrow$   | \Longrightarrow     |  40  |   $\leftharpoondown$   | \leftharpoondown     |
|  6   |      $\implies$       | \implies            |  41  |    $\upharpoonleft$    | \upharpoonleft       |
|  7   |     $\Leftarrow$      | \Leftarrow          |  42  |   $\upharpoonright$    | \upharpoonright      |
|  8   |     $\nLeftarrow$     | \nLeftarrow         |  43  |   $\downharpoonleft$   | \downharpoonleft     |
|  9   |   $\Longleftarrow$    | \Longleftarrow      |  44  |  $\downharpoonright$   | \downharpoonright    |
|  10  |   $\Leftrightarrow$   | \Leftrightarrow     |  45  |  $\rightleftharpoons$  | \rightleftharpoons   |
|  11  |  $\nLeftrightarrow$   | \nLeftrightarrow    |  46  |  $\leftrightharpoons$  | \leftrightharpoons   |
|  12  | $\Longleftrightarrow$ | \Longleftrightarrow |  47  |   $\curvearrowleft$    | \curvearrowleft      |
|  13  |        $\iff$         | \iff                |  48  |   $\circlearrowleft$   | \circlearrowleft     |
|  14  |      $\Uparrow$       | \Uparrow            |  49  |         $\Lsh$         | \Lsh                 |
|  15  |     $\Downarrow$      | \Downarrow          |  50  |     $\upuparrows$      | \upuparrows          |
|  16  |    $\Updownarrow$     | \Updownarrow        |  51  |  $\rightrightarrows$   | \rightrightarrows    |
|  17  |     $\rightarrow$     | \rightarrow         |  52  |   $\rightleftarrows$   | \rightleftarrows     |
|  18  |         $\to$         | \to                 |  53  |   $\rightarrowtail$    | \rightarrowtail      |
|  19  |    $\nrightarrow$     | \nrightarrow        |  54  |   $\looparrowright$    | \looparrowright      |
|  20  |   $\longrightarrow$   | \longrightarrow     |  55  |   $\curvearrowright$   | \curvearrowright     |
|  21  |     $\leftarrow$      | \leftarrow          |  56  |  $\circlearrowright$   | \circlearrowright    |
|  22  |        $\gets$        | \gets               |  57  |         $\Rsh$         | \Rsh                 |
|  23  |     $\nleftarrow$     | \nleftarrow         |  58  |   $\downdownarrows$    | \downdownarrows      |
|  24  |   $\longleftarrow$    | \longleftarrow      |  59  |   $\leftleftarrows$    | \leftleftarrows      |
|  25  |   $\leftrightarrow$   | \leftrightarrow     |  60  |   $\leftrightarrows$   | \leftrightarrows     |
|  26  |  $\nleftrightarrow$   | \nleftrightarrow    |  61  |    $\leftarrowtail$    | \leftarrowtail       |
|  27  | $\longleftrightarrow$ | \longleftrightarrow |  62  |    $\looparrowleft$    | \looparrowleft       |
|  28  |      $\uparrow$       | \uparrow            |  63  |   $\hookrightarrow$    | \hookrightarrow      |
|  29  |     $\downarrow$      | \downarrow          |  64  |    $\hookleftarrow$    | \hookleftarrow       |
|  30  |    $\updownarrow$     | \updownarrow        |  65  |      $\multimap$       | \multimap            |
|  31  |      $\nearrow$       | \nearrow            |  66  | $\leftrightsquigarrow$ | \leftrightsquigarrow |
|  32  |      $\swarrow$       | \swarrow            |  67  |   $\rightsquigarrow$   | \rightsquigarrow     |
|  33  |      $\nwarrow$       | \nwarrow            |  68  |  $\twoheadrightarrow$  | \twoheadrightarrow   |
|  34  |      $\searrow$       | \searrow            |  69  |  $\twoheadleftarrow$   | \twoheadleftarrow    |
|  35  |       $\mapsto$       | \mapsto             |      |                        |                      |

##### 2.1.9 特殊 Special

| 序号 |       图标       | LaTeX          | 序号 |        图标         | LaTeX             |
| :--: | :--------------: | :------------- | :--: | :-----------------: | :---------------- |
|  1   |     $\infty$     | \infty         |  33  |       $\flat$       | \flat             |
|  2   |     $\aleph$     | \aleph         |  34  |     $\natural$      | \natural          |
|  3   |  $\complement$   | \complement    |  35  |      $\sharp$       | \sharp            |
|  4   |  $\backepsilon$  | \backepsilon   |  36  |      $\diagup$      | \diagup           |
|  5   |      $\eth$      | \eth           |  37  |     $\diagdown$     | \diagdown         |
|  6   |     $\Finv$      | \Finv          |  38  |    $\centerdot$     | \centerdot        |
|  7   |     $\hbar$      | \hbar          |  39  |      $\ltimes$      | \ltimes           |
|  8   |      $\Im$       | \Im            |  40  |      $\rtimes$      | \rtimes           |
|  9   |     $\imath$     | \imath         |  41  |  $\leftthreetimes$  | \leftthreetimes   |
|  10  |     $\jmath$     | \jmath         |  42  | $\rightthreetimes$  | \rightthreetimes  |
|  11  |     $\Bbbk$      | \Bbbk          |  43  |      $\eqcirc$      | \eqcirc           |
|  12  |      $\ell$      | \ell           |  44  |      $\circeq$      | \circeq           |
|  13  |      $\mho$      | \mho           |  45  |    $\triangleq$     | \triangleq        |
|  14  |      $\wp$       | \wp            |  46  |      $\bumpeq$      | \bumpeq           |
|  15  |      $\Re$       | \Re            |  47  |      $\Bumpeq$      | \Bumpeq           |
|  16  |   $\circledS$    | \circledS      |  48  |     $\doteqdot$     | \doteqdot         |
|  17  |     $\amalg$     | \amalg         |  49  |   $\risingdotseq$   | \risingdotseq     |
|  18  |       $\%$       | \%             |  50  |  $\fallingdotseq$   | \fallingdotseq    |
|  19  |    $\dagger$     | \dagger        |  51  |     $\intercal$     | \intercal         |
|  20  |    $\ddagger$    | \ddagger       |  52  |     $\barwedge$     | \barwedge         |
|  21  |     $\ldots$     | \ldots         |  53  |      $\veebar$      | \veebar           |
|  22  |     $\cdots$     | \cdots         |  54  |  $\doublebarwedge$  | \doublebarwedge   |
|  23  |     $\smile$     | \smile         |  55  |     $\between$      | \between          |
|  24  |     $\frown$     | \frown         |  56  |    $\pitchfork$     | \pitchfork        |
|  25  |      $\wr$       | \wr            |  57  | $\vartriangleleft$  | \vartriangleleft  |
|  26  | $\triangleleft$  | \triangleleft  |  58  |  $\ntriangleleft$   | \ntriangleleft    |
|  27  | $\triangleright$ | \triangleright |  59  | $\vartriangleright$ | \vartriangleright |
|  28  |  $\diamondsuit$  | \diamondsuit   |  60  |  $\ntriangleright$  | \ntriangleright   |
|  29  |   $\heartsuit$   | \heartsuit     |  61  |  $\trianglelefteq$  | \trianglelefteq   |
|  30  |   $\clubsuit$    | \clubsuit      |  62  | $\ntrianglelefteq$  | \ntrianglelefteq  |
|  31  |   $\spadesuit$   | \spadesuit     |  63  | $\trianglerighteq$  | \trianglerighteq  |
|  32  |     $\Game$      | \Game          |  64  | $\ntrianglerighteq$ | \ntrianglerighteq |

#### 2.2 运算与函数 Operations & Functions



##### 2.2.1 分数 Fractions

| 类型                                                         | 样式                                                         | LaTeX                                                        |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| 分数 Fractions                                               | $\frac{2}{4}x=0.5 x$                                          | \frac{2}{4}x=0.5 x or {2 \over 4}x=0.5 x                       |
| 小型分数 Small fractions (force \textstyle)                  | $\tfrac{2}{4}x = 0.5 x$                                       | \tfrac{2}{4}x = 0.5 x                                         |
| 大型分数（不嵌套） Large (normal) fractions (force \displaystyle) | $\dfrac{2}{4} = 0.5 \qquad \dfrac{2}{c + \dfrac{2}{d + \dfrac{2}{4}}} = a$ | \dfrac{2}{4} = 0.5 \qquad \dfrac{2}{c + \dfrac{2}{d + \dfrac{2}{4}}} = a |
| 大型分数（嵌套） Large (nested) fractions                    | $\cfrac{2}{c + \cfrac{2}{d + \cfrac{2}{4}}} = a$             | \cfrac{2}{c + \cfrac{2}{d + \cfrac{2}{4}}} = a               |
| 约分线的使用 Cancellations in fractions                      | $\cfrac{x}{1 + \cfrac{\cancel{y}}{\cancel{y}}} = \cfrac{x}{2}$ | \cfrac{x}{1 + \cfrac{\cancel{y}}{\cancel{y}}} = \cfrac{x}{2} |

**注意：** 其中`\cancel`命令需要**cancel 扩展包**支持，**cancel 扩展包**是一款自定义宏包，如需使用请在公式页面右上角【设置】页面勾选后使用。



##### 2.2.2 标准数值函数 Standard numerical functions

| 样式                                                         | LaTeX                                                        |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| $\exp_a b = a^b, \exp b = e^b, 10^m$                         | \exp_a b = a^b, \exp b = e^b, 10^m                           |
| $\ln c, \lg d = \log e, \log_{10} f$                         | \ln c, \lg d = \log e, \log_{10} f                           |
| $\sin a, \cos b, \tan c, \cot d, \sec e, \csc f$             | \sin a, \cos b, \tan c, \cot d, \sec e, \csc f               |
| $\arcsin a, \arccos b, \arctan c$                            | \arcsin a, \arccos b, \arctan c                              |
| $\operatorname{arccot} d, \operatorname{arcsec} e, \operatorname{arccsc} f$ | \operatorname{arccot} d, \operatorname{arcsec} e, \operatorname{arccsc} f |
| $\sinh a, \cosh b, \tanh c, \coth d$                         | \sinh a, \cosh b, \tanh c, \coth d                           |
| $\operatorname{sh}k, \operatorname{ch}l, \operatorname{th}m, \operatorname{coth}n$ | \operatorname{sh}k, \operatorname{ch}l, \operatorname{th}m, \operatorname{coth}n |
| $\operatorname{argsh}o, \operatorname{argch}p, \operatorname{argth}q$ | \operatorname{argsh}o, \operatorname{argch}p, \operatorname{argth}q |
| $\operatorname{sgn}r, \left\vert s \right\vert$              | \operatorname{sgn}r, \left\vert s \right\vert                |
| $\min (x, y), \max (x, y)$                                       | \min (x, y), \max (x, y)                                         |

**注意：**LaTeX 和 MathJax 支持的操作符有限，如有特殊操作符，可以使用`\operatorname{}` 命令自定义，例如

```
\operatorname{mydefine}x
```

$$ \operatorname{mydefine}x $$

##### 2.2.3 根式 Radicals

| 样式                          | LaTeX                       |
| :---------------------------- | :-------------------------- |
| $\surd$                       | \surd                       |
| $\sqrt{\pi}$                  | \sqrt{\pi}                  |
| $\sqrt[n]{\pi}$               | \sqrt[n]{\pi}               |
| $\sqrt[3]{\frac{x^3+y^3}{2}}$ | \sqrt[3]{\frac{x^3+y^3}{2}} |

##### 2.2.4 微分与导数 Differentials and derivatives

| 样式                                                         | LaTeX                                                        |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| $dt, \mathrm{d}t, \partial t, \nabla\psi$                    | dt, \mathrm{d}t, \partial t, \nabla\psi                      |
| $dy/dx, \mathrm{d}y/\mathrm{d}x, \frac{dy}{dx}, \frac{\mathrm{d}y}{\mathrm{d}x}, \frac{\partial^2}{\partial x_1\partial x_2}y$ | dy/dx, \mathrm{d}y/\mathrm{d}x, \frac{dy}{dx}, \frac{\mathrm{d}y}{\mathrm{d}x}, \frac{\partial^2}{\partial x_1\partial x_2}y |
| $\prime, \backprime, f^\prime, f', f'', f^{(3)}, \dot y, \ddot y$ | \prime, \backprime, f^\prime, f', f'', f^{(3)}, \dot y, \ddot y |

##### 2.2.5 同余与模算术 Modular arithmetic

| 样式                                   | LaTeX                                |
| :------------------------------------- | :----------------------------------- |
| $s_k \equiv 0 \pmod{m}$                | s_k \equiv 0 \pmod{m}                |
| $a \bmod b$                            | a \bmod b                            |
| $\gcd (m, n), \operatorname{lcm}(m, n)$ | \gcd (m, n), \operatorname{lcm}(m, n) |
| $\mid, \nmid, \shortmid, \nshortmid$   | \mid, \nmid, \shortmid, \nshortmid   |

##### 2.2.6 极限 Limits

| 样式                                | LaTeX                             |
| :---------------------------------- | :-------------------------------- |
| $\lim_{n \to \infty}x_n$            | \lim_{n \to \infty}x_n            |
| $\textstyle \lim_{n \to \infty}x_n$ | \textstyle \lim_{n \to \infty}x_n |

##### 2.2.7 界限与投影 Bounds and Projections

| 样式                                     | LaTeX                                  |
| :--------------------------------------- | :------------------------------------- |
| $\min x, \max y, \inf s, \sup t$         | \min x, \max y, \inf s, \sup t         |
| $\lim u, \liminf v, \limsup w$           | \lim u, \liminf v, \limsup w           |
| $\dim p, \deg q, \det m, \ker\phi$       | \dim p, \deg q, \det m, \ker\phi       |
| $\Pr j, \hom l, \lVert z \rVert, \arg z$ | \Pr j, \hom l, \lVert z \rVert, \arg z |

##### 2.2.8 积分 Integral

| 样式                                        | LaTeX                                     |
| :------------------------------------------ | :---------------------------------------- |
| $\int\limits_{1}^{3}\frac{e^3/x}{x^2}\, dx$ | \int\limits_{1}^{3}\frac{e^3/x}{x^2}\, dx |
| $\int_{1}^{3}\frac{e^3/x}{x^2}\, dx$        | \int_{1}^{3}\frac{e^3/x}{x^2}\, dx        |
| $\textstyle \int\limits_{-N}^{N} e^x dx$    | \textstyle \int\limits_{-N}^{N} e^x dx    |
| $\textstyle \int_{-N}^{N} e^x dx$           | \textstyle \int_{-N}^{N} e^x dx           |
| $\iint\limits_D dx\, dy$                     | \iint\limits_D dx\, dy                     |
| $\iiint\limits_E dx\, dy\, dz$                | \iiint\limits_E dx\, dy\, dz                |
| $\iiiint\limits_F dx\, dy\, dz\, dt$           | \iiiint\limits_F dx\, dy\, dz\, dt           |
| $\int_{(x, y)\in C} x^3\, dx + 4 y^2\, dy$    | \int_{(x, y)\in C} x^3\, dx + 4 y^2\, dy    |
| $\oint_{(x, y)\in C} x^3\, dx + 4 y^2\, dy$   | \oint_{(x, y)\in C} x^3\, dx + 4 y^2\, dy   |

**注意：**积分符号可以使用`\int_{}^{}`命令调用，如需双重积分符号只需将`int`替换成`iint`即可，以此类推，最高支持四重。曲线积分可使用`\oint`命令调用，但曲面积分符号在 MathJax 环境中并不支持`\oiint`的用法，但仍可通过`\unicode{}`命令，即 Unicode 代码的方式进行调用（前提是您需要在设置中打开 Unicode 扩展），具体使用方法如下：

```
\unicode{8751} \unicode{x 222 F}_C %曲面积分符号的 Unicode 码十进制为 8751, 十六进制为 x 222 F (注意 x 标识符)
```

$\Large\unicode{8751} \quad \unicode{x 222 F}_C %曲面积分符号的 Unicode 码十进制为 8751, 十六进制为 x 222 F (注意 x 标识符)$

```
\unicode{8752} \unicode{x 2230}_C %三维曲面积分符号的 Unicode 码十进制为 8752, 十六进制为 x 2230
        
```

$\Large\unicode{8752} \quad \unicode{x 2230}_C %三维曲面积分符号的 Unicode 码十进制为 8752, 十六进制为 x 2230$

其他积分符号：

```
\unicode{8753} \unicode{x 2231}_c
          \unicode{8754} \unicode{x 2232}_c
          \unicode{8755} \unicode{x 2233}_c
```

$\Large\unicode{8753} \qquad \unicode{x 2231}_c \qquad \unicode{8754} \qquad \unicode{x 2232}_c \qquad \unicode{8755} \qquad \unicode{x 2233}_c $


##### 2.2.9 其他大型运算 Large operators

| 类别              | 样式                             | LaTeX                        |
| :---------------- | :------------------------------- | :--------------------------- |
| 求和 Summation    | $$\sum_{a}^{b}$$                 | \sum_{a}^{b}                 |
| 求和 Summation    | $$\textstyle \sum_{a}^{b}$$      | \textstyle \sum_{a}^{b}      |
| 连乘积 Product    | $$\prod_{a}^{b}$$                | \prod_{a}^{b}                |
| 连乘积 Product    | $$\textstyle \prod_{a}^{b}$$     | \textstyle \prod_{a}^{b}     |
| 余积 Coproduct    | $$\coprod_{a}^{b}$$              | \coprod_{a}^{b}              |
| 余积 Coproduct    | $$\textstyle \coprod_{a}^{b}$$   | \textstyle \coprod_{a}^{b}   |
| 并集 Union        | $$\bigcup_{a}^{b}$$              | \bigcup_{a}^{b}              |
| 并集 Union        | $$\textstyle \bigcup_{a}^{b}$$   | \textstyle \bigcup_{a}^{b}   |
| 交集 Intersection | $$\bigcap_{a}^{b}$$              | \bigcap_{a}^{b}              |
| 交集 Intersection | $$\textstyle \bigcap_{a}^{b}$$   | \textstyle \bigcap_{a}^{b}   |
| 析取 Disjunction  | $$\bigvee_{a}^{b}$$              | \bigvee_{a}^{b}              |
| 析取 Disjunction  | $$\textstyle \bigvee_{a}^{b}$$   | \textstyle \bigvee_{a}^{b}   |
| 合取 Conjunction  | $$\bigwedge_{a}^{b}$$            | \bigwedge_{a}^{b}            |
| 合取 Conjunction  | $$\textstyle \bigwedge_{a}^{b}$$ | \textstyle \bigwedge_{a}^{b} |

#### 2.3 上下标 Sub & Super

| 类型                                                         | 样式                                                         | 代码                                                 |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :--------------------------------------------------- |
| 上标 Superscript                                             | $a^2, a^{x+3}$                                               | a^2, a^{x+3}                                         |
| 下标 Subscript                                               | $a_2$                                                        | a_2                                                  |
| 组合 Grouping                                                | $10^{30} a^{2+2}$                                            | 10^{30} a^{2+2}                                      |
| $a_{i, j} b_{f'}$                                             | a*{i, j} b*{f'}                                               |                                                      |
| 上下标混合 Combining sub & super                             | $x_2^3$                                                      | x_2^3                                                |
| ${x_2}^3$                                                    | {x_2}^3                                                      |                                                      |
| 上标的上标 Super super                                       | $10^{10^{8}}$                                                | 10^{10^{8}}                                          |
| 混合标识 Preceding and/or additional sub & super             | $\sideset{_1^2}{_3^4}X_a^b$                                  | \sideset{*1^2}{*3^4}X_a^b                            |
| ${}_1^2\!\Omega_3^4$                                         | {}_1^2!\Omega_3^4                                            |                                                      |
| 顶标底标 Stacking                                            | $\overset{\alpha}{\omega}$                                   | \overset{\alpha}{\omega}                             |
| $\underset{\alpha}{\omega}$                                  | \underset{\alpha}{\omega}                                    |                                                      |
| $\overset{\alpha}{\underset{\gamma}{\omega}}$                | \overset{\alpha}{\underset{\gamma}{\omega}}                  |                                                      |
| $\stackrel{\alpha}{\omega}$                                  | \stackrel{\alpha}{\omega}                                    |                                                      |
| 导数 Derivatives                                             | $x', y'', f', f''$                                           | x', y'', f', f''                                     |
| $x^\prime, y^{\prime\prime}$                                 | x^\prime, y^{\prime\prime}                                   |                                                      |
| 导数 Derivative dots                                         | $\dot{x}, \ddot{x}$                                          | \dot{x}, \ddot{x}                                    |
| 下划线、上划线与向量 Underlines, overlines, vectors          | $\hat a \ \bar b \ \vec c$                                   | \hat a \ \bar b \ \vec c                             |
| $\overrightarrow{a b} \ \overleftarrow{c d} \ \widehat{d e f}$ | \overrightarrow{a b} \ \overleftarrow{c d} \ \widehat{d e f} |                                                      |
| $\overline{g h i} \ \underline{j k l}$                       | \overline{g h i} \ \underline{j k l}                         |                                                      |
| 弧度 Arc (workaround)                                        | $\overset{\frown} {AB}$                                      | \overset{\frown} {AB}                                |
| 箭头 Arrows                                                  | $A \xleftarrow{n+\mu-1} B \xrightarrow[T]{n\pm i-1} C$       | A \xleftarrow{n+\mu-1} B \xrightarrow[T]{n\pm i-1} C |
| 大括号 Overbraces                                            | $\overbrace{ 1+2+\cdots+100 }^{5050}$                        | \overbrace{ 1+2+\cdots+100 }^{5050}                  |
| 底部大括号 Underbraces                                       | $\underbrace{ a+b+\cdots+z }_{26}$                           | \underbrace{ a+b+\cdots+z }_{26}                     |
| 求和运算 Sum                                                 | $$\sum_{k=1}^N k^2$$                                         | \sum_{k=1}^N k^2                                     |
| 文本模式下的求和运算 Sum (force \textstyle)                  | $$\textstyle \sum_{k=1}^N k^2$$                              | \textstyle \sum_{k=1}^N k^2                          |
| 分式中的求和运算 Sum in a fraction (default \textstyle)      | $$\frac{\sum_{k=1}^N k^2}{a}$$                               | \frac{\sum_{k=1}^N k^2}{a}                           |
| 分式中的求和运算 Sum in a fraction (force \displaystyle)     | $$\frac{\displaystyle \sum_{k=1}^N k^2}{a}$$                 | \frac{\displaystyle \sum_{k=1}^N k^2}{a}             |
| 分式中的求和运算 Sum in a fraction (alternative limits style) | $$\frac{\sum\limits^{^N}_{k=1} k^2}{a}$$                     | \frac{\sum\limits^{^N}_{k=1} k^2}{a}                 |
| 乘积运算 Product                                             | $$\prod_{i=1}^N x_i$$                                        | \prod_{i=1}^N x_i                                    |
| 乘积运算 Product (force \textstyle)                          | $$\textstyle \prod_{i=1}^N x_i$$                             | \textstyle \prod_{i=1}^N x_i                         |
| 副乘运算 Coproduct                                           | $$\coprod_{i=1}^N x_i$$                                      | \coprod_{i=1}^N x_i                                  |
| 副乘运算 Coproduct (force \textstyle)                        | $$\textstyle \coprod_{i=1}^N x_i$$                           | \textstyle \coprod_{i=1}^N x_i                       |
| 极限 Limit                                                   | $$\lim_{n \to \infty}x_n$$                                   | \lim_{n \to \infty}x_n                               |
| 极限 Limit (force \textstyle)                                | $$\textstyle \lim_{n \to \infty}x_n$$                        | \textstyle \lim_{n \to \infty}x_n                    |
| 积分 Integral                                                | $$\int\limits_{1}^{3}\frac{e^3/x}{x^2}\, dx$$                | \int\limits_{1}^{3}\frac{e^3/x}{x^2}\, dx            |
| 积分 Integral (alternative limits style)                     | $$\int_{1}^{3}\frac{e^3/x}{x^2}\, dx$$                       | \int_{1}^{3}\frac{e^3/x}{x^2}\, dx                   |
| 积分 Integral (force \textstyle)                             | $$\textstyle \int\limits_{-N}^{N} e^x dx$$                   | \textstyle \int\limits_{-N}^{N} e^x dx               |
| 积分 Integral (force \textstyle, alternative limits style)   | $$\textstyle \int_{-N}^{N} e^x dx$$                          | \textstyle \int_{-N}^{N} e^x dx                      |
| 双重积分 Double integral                                     | $$\iint\limits_D dx\, dy$$                                    | \iint\limits_D dx\, dy                                |
| 三重积分 Triple integral                                     | $$\iiint\limits_E dx\, dy\, dz$$                               | \iiint\limits_E dx\, dy\, dz                           |
| 四重积分 Quadruple integral                                  | $$\iiiint\limits_F dx\, dy\, dz\, dt$$                          | \iiiint\limits_F dx\, dy\, dz\, dt                      |
| 路径积分 Line or path integral                               | $$\int_{(x, y)\in C} x^3\, dx + 4 y^2\, dy$$                   | \int_{(x, y)\in C} x^3\, dx + 4 y^2\, dy               |
| 环路积分 Closed line or path integral                        | $$\oint_{(x, y)\in C} x^3\, dx + 4 y^2\, dy$$                  | \oint_{(x, y)\in C} x^3\, dx + 4 y^2\, dy              |
| 交集 Intersections                                           | $$\bigcap_{i=1}^n E_i$$                                      | \bigcap_{i=1}^n E_i                                  |
| 并集 Unions                                                  | $$\bigcup_{i=1}^n E_i$$                                      | \bigcup_{i=1}^n E_i                                  |

#### 2.4 矩阵与多行列式 Matrices & Multilines

| 类型                                                         | 样式                                                         | LaTeX                                                        |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| 二项式系数 Binomial coefficients                             | $\binom{n}{k}$                                               | \binom{n}{k}                                                 |
| 小型二项式系数 Small binomial coefficients (force \textstyle) | $\tbinom{n}{k}$                                              | \tbinom{n}{k}                                                |
| 大型二项式系数 Large (normal) binomial coefficients (force \displaystyle) | $\dbinom{n}{k}$                                              | \dbinom{n}{k}                                                |
| 矩阵 Matrices                                                | $\begin{matrix} x & y \\z & v\end{matrix}$                   | \begin{matrix} x & y \\ z & v \end{matrix}                   |
| $\begin{vmatrix} x & y \\ z & v \end{vmatrix}$               | \begin{vmatrix} x & y \\ z & v \end{vmatrix}                 |                                                              |
| $\begin{Vmatrix} x & y \\ z & v \end{Vmatrix} $              | \begin{Vmatrix} x & y \\ z & v \end{Vmatrix}                 |                                                              |
| $\begin{bmatrix} 0 & \cdots & 0 \\ \vdots & \ddots & \vdots \\ 0 & \cdots & 0 \end{bmatrix}$ | \begin{bmatrix} 0 & \cdots & 0 \\ \vdots & \ddots & \vdots \\ 0 & \cdots & 0 \end{bmatrix} |                                                              |
| $\begin{Bmatrix} x & y \\ z & v \end{Bmatrix}$               | \begin{Bmatrix} x & y \\ z & v \end{Bmatrix}                 |                                                              |
| $\begin{pmatrix} x & y \\ z & v \end{pmatrix}$               | \begin{pmatrix} x & y \\ z & v \end{pmatrix}                 |                                                              |
| $\bigl ( \begin{smallmatrix} a&b\\ c&d \end{smallmatrix} \bigr)$ | \bigl ( \begin{smallmatrix} a&b\\ c&d \end{smallmatrix} \bigr) |                                                              |
| 条件定义 Case distinctions                                   | $f (n) =\begin{cases} n/2, & \text{if }n\text{ is even} \\ 3 n+1, & \text{if }n\text{ is odd} \end{cases}$ | f (n) = \begin{cases} n/2, & \text{if }n\text{ is even} \\ 3 n+1, & \text{if }n\text{ is odd} \end{cases} |
| 多行等式 Multiline equations                                 | $\begin{align} f (x) & = (a+b)^2 \nonumber \\ & = a^2+2 ab+b^2 \nonumber \end{align}$ | \begin{align} f (x) & = (a+b)^2\\ & = a^2+2 ab+b^2 \end{align} |
| $\begin{alignat}{2} f (x) & = (a-b)^2 \nonumber \\ & = a^2-2 ab+b^2 \nonumber \end{alignat}$ | \begin{alignat}{2} f (x) & = (a-b)^2 \\ & = a^2-2 ab+b^2 \end{alignat} |                                                              |
| $\begin{array}{lcl} z & = & a \\ f (x, y, z) & = & x + y + z \end{array}$ | \begin{array}{lcl} z & = & a \\ f (x, y, z) & = & x + y + z \end{array} |                                                              |
| $\begin{array}{lcr} z & = & a \\ f (x, y, z) & = & x + y + z \end{array}$ | \begin{array}{lcr} z & = & a \\ f (x, y, z) & = & x + y + z \end{array} |                                                              |
| 方程组 Simultaneous equations                                | $\begin{cases} 3 x + 5 y + z \\ 7 x - 2 y + 4 z \\ -6 x + 3 y + 2 z \end{cases}$ | \begin{cases} 3 x + 5 y + z \\ 7 x - 2 y + 4 z \\ -6 x + 3 y + 2 z \end{cases} |
| 数组 Arrays                                                  | $\begin{array}{ \| c \| c \| c \| } a & b & S \\ \hline 0&0&1\\ 0&1&1\\ 1&0&1\\ 1&1&0 \end{array}$ | \begin{array}{ \| c \| c \| c \| } a & b & S \\ \hline 0 & 0 & 1 \\ 0 & 1 & 1 \\ 1 & 0 & 1 \\ 1 & 1 & 0 \end{array} |

#### 2.5 括号 Brackets

常用的括号符号例如`( )[ ]{ }……`这些也可以在输入环境中直接使用：

```
2 (x+y)=z
```

$$ 2 (x+y)=z $$

但如果是在较大的表达式中这些符号就显得不合适了

```
( \frac{\pi}{2} )^n
```

$$ ( \frac{\pi}{2} )^n $$

正确用法应配合`\left`和`\right`命令使用。

```
\left ( \frac{\pi}{2} \right )^n
```

$$ \left ( \frac{\pi}{2} \right )^n $$

具体可参考下表。

| 类型                                                         | 样式                                                         | LaTeX                                                        |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| 圆括号、小括号 Parentheses                                   | $\left ( \frac{a}{b} \right )$                               | \left ( \frac{a}{b} \right )                                 |
| 方括号、中括号 Brackets                                      | $\left [ \frac{a}{b} \right ] \quad \left \lbrack \frac{a}{b} \right \rbrack$ | \left [ \frac{a}{b} \right ] \quad \left \lbrack \frac{a}{b} \right \rbrack |
| 花括号、大括号 Braces                                        | $\left \{ \frac{a}{b} \right \} \quad \left \lbrace \frac{a}{b} \right \rbrace$ | \left { \frac{a}{b} \right } \quad \left \lbrace \frac{a}{b} \right \rbrace |
| 角括号 Angle brackets                                        | $\left \langle \frac{a}{b} \right \rangle$                   | \left \langle \frac{a}{b} \right \rangle                     |
| 单竖线和双竖线 Bars and double bars                          | $\left \| \frac{a}{b} \right \vert \quad \left \Vert \frac{c}{d} \right \|$ | \left \| \frac{a}{b} \right \vert \quad \left \Vert \frac{c}{d} \right \| |
| 取整函数与取顶函数 Floor and ceiling functions:              | $\left \lfloor \frac{a}{b} \right \rfloor \quad \left \lceil \frac{c}{d} \right \rceil$ | \left \lfloor \frac{a}{b} \right \rfloor \quad \left \lceil \frac{c}{d} \right \rceil |
| 斜线与反斜线 Slashes and backslashes                         | $\left / \frac{a}{b} \right \backslash$                      | \left / \frac{a}{b} \right \backslash                        |
| 上下箭头 Up, down, and up-down arrows                        | $\left \uparrow \frac{a}{b} \right \downarrow \quad \left \Uparrow \frac{a}{b} \right \Downarrow \quad \left \updownarrow \frac{a}{b} \right \Updownarrow$ | \left \uparrow \frac{a}{b} \right \downarrow \quad \left \Uparrow \frac{a}{b} \right \Downarrow \quad \left \updownarrow \frac{a}{b} \right \Updownarrow |
| 混合括号 Delimiters can be mixed, as long as \left and \right match | $\left [ 0,1 \right ) \left \langle \psi \right \| $         | \left [ 0,1 \right ) \left \langle \psi \right \|            |
| 如果您不希望某一侧括号显示，可以使用\left. 和 \right.（带有英文句号） Use \left. And \right. If you do not want a delimiter to appear | $\left . \frac{A}{B} \right \} \to X$                        | \left . \frac{A}{B} \right } \to X                           |
| 括号的大小 Size of the delimiters (add "l" or "r" to indicate the side for proper spacing) | $( \bigl ( \Bigl ( \biggl ( \Biggl ( \dots \Biggr] \biggr] \Bigr] \bigr] ]$ | ( \bigl ( \Bigl ( \biggl ( \Biggl ( \dots \Biggr] \biggr] \Bigr] \bigr] ] |
| $\{ \bigl\{ \Bigl\{ \biggl\{ \Biggl\{ \dots \Biggr\rangle \biggr\rangle \Bigr\rangle \bigr\rangle \rangle$ | { \bigl{ \Bigl{ \biggl{ \Biggl{ \dots \Biggr\rangle \biggr\rangle \Bigr\rangle \bigr\rangle \rangle |                                                              |
| $\| \big\| \Big\| \bigg\| \Bigg\| \dots \Bigg \| \bigg \| \Big \| \big \| \|$ | \| \big\| \Big\| \bigg\| \Bigg\| \dots \Bigg \| \bigg \| \Big \| \big \| |                                                              |
| $\lfloor \bigl\lfloor \Bigl\lfloor \biggl\lfloor \Biggl\lfloor \dots \Biggr\rceil \biggr\rceil \Bigr\rceil \bigr\rceil \rceil$ | \lfloor \bigl\lfloor \Bigl\lfloor \biggl\lfloor \Biggl\lfloor \dots \Biggr\rceil \biggr\rceil \Bigr\rceil \bigr\rceil \rceil |                                                              |
| $\uparrow \big\uparrow \Big\uparrow \bigg\uparrow \Bigg\uparrow \dots \Bigg\Downarrow \bigg\Downarrow \Big\Downarrow \big\Downarrow \Downarrow$ | \uparrow \big\uparrow \Big\uparrow \bigg\uparrow \Bigg\uparrow \dots \Bigg\Downarrow \bigg\Downarrow \Big\Downarrow \big\Downarrow \Downarrow |                                                              |
| $\updownarrow \big\updownarrow \Big\updownarrow \bigg\updownarrow \Bigg\updownarrow \dots \Bigg\Updownarrow \bigg\Updownarrow \Big\Updownarrow \big\Updownarrow \Updownarrow$ | \updownarrow \big\updownarrow \Big\updownarrow \bigg\updownarrow \Bigg\updownarrow \dots \Bigg\Updownarrow \bigg\Updownarrow \Big\Updownarrow \big\Updownarrow \Updownarrow |                                                              |
| $/ \big/ \Big/ \bigg/ \Bigg/ \dots \Bigg\backslash \bigg\backslash \Big\backslash \big\backslash \backslash$ | / \big/ \Big/ \bigg/ \Bigg/ \dots \Bigg\backslash \bigg\backslash \Big\backslash \big\backslash \backslash |                                                              |
#### 2.6 空格与换行 Spacing & Line breaking

##### 2.6.1 空格 Spacing

MathJax 能够自动处理大多数空格间距的大小，但如果您需要自己控制，可参考下表。

| 序号 |      样式      | LaTeX        | 中文说明英文说明           |
| :--: | :------------: | :----------- | :------------------------- |
|  1   |  $a \qquad b$  | a \qquad b   | 双空格                     |
|  2   |  $a \quad b$   | a \quad b    | 单空格                     |
|  3   |     $a\ b$     | a\ b         | 字符空格                   |
|  4   | $a \text{ } b$ | a \text{ } b | 文本模式中的字符空格       |
|  5   |     $a\; b$     | a\; b         | 大空格                     |
|  6   |     $a\, b$     | a\, b         | 小空格                     |
|  7   |      $ab$      | ab           | 极小空格 (用于乘因子)       |
|  8   |     $a b$      | a b          | 极小空格 (用于区分其它语法) |
|  9   | $\mathit{ab}$  | \mathit{ab}  | 没有空格 (用于多字母变量)   |
|  10  |     $a\! B$     | a! B          | 负空格                     |

##### 2.6.2 换行 Line breaking

在 MathJax 3.0 中取消了使用`\\`进行强制换行的功能，因此本页面也采取同样的逻辑，默认为单行公式环境。`\\`强制换行命令只在支持多行编辑的数学环境中才起作用，如`eqnarray`环境、`align`环境、`array`环境、`matrix`环境等等。如您需要显示多行公式，建议在此类环境中输入公式，具体用法参见章节 [2.10](https://www.latexlive.com/help#d50)。

或者您可直接在`\displaylines{}`显示行命令中使用`\\`强制换行命令，例如：

```
\displaylines{y=1729 x \\ y=1729-x}
```

$$ \displaylines{y=1729 x \\ y=1729-x} $$


#### 2.7 颜色 Colors


##### 2.7.1 字体颜色 Font colors

在公式中可以使用`\color{options}{math}`来调用颜色命令，第一个参数为颜色，第二个参数为公式或文本内容。例如:

```
{\color{Blue}x^2}+{\color{Orange}2 x}-{\color{LimeGreen}1}
```

$$ {\color{Blue}x^2}+{\color{Orange}2 x}-{\color{LimeGreen}1} $$

```
x_{1,2}=\frac {{\color{Blue}-b}\pm\sqrt{\color{Red}b^2-4ac}} {\color{Green}2 a }
```

$$ x_{1,2}=\frac {{\color{Blue}-b}\pm\sqrt{\color{Red}b^2-4ac}} {\color{Green}2 a } $$

**注意：** 使用`\color`命令时，请将需要设置颜色的部分用`{ }`整体扩住，以表明`\color`函数作用范围。


##### 2.7.2 背景颜色 Background color

在文本环境中可以使用`\colorbox{options}{text}`来调用背景颜色命令，第一个参数为颜色，第二个颜色为文本内容。例如：

```
\colorbox{yellow}{Thistext}
```

$$ \colorbox{yellow}{Thistext} $$

**注意：** 若需要在数学环境中使用`\colorbox{}{}`，请在第二个参数内加入`$\displaystyle + 公式$`，例如：

```
\colorbox{yellow}{$\displaystyle \frac{a}{b}$}
```

$$ \colorbox{yellow}{$\displaystyle \frac{a}{b}$} $$

或者您可以使用 **Bbox 扩展** 来替换`\colorbox`命令，详见下条 2.7.3。

##### 2.7.3 用 Bbox 扩展设置背景颜色 Setting background color with Bbox

Bbox 扩展是一款自定义宏包，如需使用请在公式页面右上角【设置】处勾选后使用。具体用法如下：

###### 2.7.3.1 设置背景颜色 Setting Background color

在公式中可以使用`\bbox[options]{math}`来调用背景颜色命令，第一个参数为颜色或大小，需注意用`[ ]`包围，第二个参数为公式。例如:

```
\bbox[red]{x+y}
```

$\bbox[red]{x+y}$

###### 2.7.3.2 调整背景大小 Setting Background Size

默认情况下，背景大小为作用范围的最大边界，如需扩大背景，可在第一个参数中加入大小信息，例如：

```
\bbox[2 pt]{x+y} %设置透明背景，并增加 2 pt 额外距离
```

$\bbox[2 pt]{x+y} %设置透明背景，并增加 2 pt 额外距离$

```
\bbox[red, 5 pt]{x+y} %设置红色背景，并增加 5 pt 额外距离
        
```

$\bbox[red, 5 pt]{x+y} %设置红色背景，并增加 5 pt 额外距离$

##### 2.7.4 默认支持颜色 Colors supported

|                   支持颜色                   |                                      |                                    |                                          |
| :--------------------------------------: | ------------------------------------ | ---------------------------------- | ---------------------------------------- |
|        ${\color{Apricot}Apricot}$        | ${\color{Emerald}Emerald}$           | ${\color{OliveGreen}OliveGreen}$   | ${\color{RubineRed}RubineRed}$           |
|     ${\color{Aquamarine}Aquamarine}$     | ${\color{ForestGreen}ForestGreen}$   | ${\color{Orange}Orange}$           | ${\color{Salmon}Salmon}$                 |
|    ${\color{Bittersweet}Bittersweet}$    | ${\color{Fuchsia}Fuchsia}$           | ${\color{OrangeRed}OrangeRed}$     | ${\color{SeaGreen}SeaGreen}$             |
|          ${\color{Black}Black}$          | ${\color{Goldenrod}Goldenrod}$       | ${\color{Orchid}Orchid}$           | ${\color{Sepia}Sepia}$                   |
|           ${\color{Blue}Blue}$           | ${\color{Gray}Gray}$                 | ${\color{Peach}Peach}$             | ${\color{SkyBlue}SkyBlue}$               |
|      ${\color{BlueGreen}BlueGreen}$      | ${\color{Green}Green}$               | ${\color{Periwinkle}Periwinkle}$   | ${\color{SpringGreen}SpringGreen}$       |
|     ${\color{BlueViolet}BlueViolet}$     | ${\color{GreenYellow}GreenYellow}$   | ${\color{PineGreen}PineGreen}$     | ${\color{Tan}Tan}$                       |
|       ${\color{BrickRed}BrickRed}$       | ${\color{JungleGreen}JungleGreen}$   | ${\color{Plum}Plum}$               | ${\color{TealBlue}TealBlue}$             |
|          ${\color{Brown}Brown}$          | ${\color{Lavender}Lavender}$         | ${\color{ProcessBlue}ProcessBlue}$ | ${\color{Thistle}Thistle}$               |
|    ${\color{BurntOrange}BurntOrange}$    | ${\color{LimeGreen}LimeGreen}$       | ${\color{Purple}Purple}$           | ${\color{Turquoise}Turquoise}$           |
|      ${\color{CadetBlue}CadetBlue}$      | ${\color{Magenta}Magenta}$           | ${\color{RawSienna}RawSienna}$     | ${\color{Violet}Violet}$                 |
|  ${\color{CarnationPink}CarnationPink}$  | ${\color{Mahogany}Mahogany}$         | ${\color{Red}Red}$                 | ${\color{VioletRed}VioletRed}$           |
|       ${\color{Cerulean}Cerulean}$       | ${\color{Maroon}Maroon}$             | ${\color{RedOrange}RedOrange}$     | ${\color{White}White}$                   |
| ${\color{CornflowerBlue}CornflowerBlue}$ | ${\color{Melon}Melon}$               | ${\color{RedViolet}RedViolet}$     | ${\color{WildStrawberry}WildStrawberry}$ |
|           ${\color{Cyan}Cyan}$           | ${\color{MidnightBlue}MidnightBlue}$ | ${\color{Rhodamine}Rhodamine}$     | ${\color{Yellow}Yellow}$                 |
|      ${\color{Dandelion}Dandelion}$      | ${\color{Mulberry}Mulberry}$         | ${\color{RoyalBlue}RoyalBlue}$     | ${\color{YellowGreen}YellowGreen}$       |
|     ${\color{DarkOrchid}DarkOrchid}$     | ${\color{NavyBlue}NavyBlue}$         | ${\color{RoyalPurple}RoyalPurple}$ | ${\color{YellowOrange}YellowOrange}$     |

##### 2.7.5 使用 RGB 颜色 Use RGB color

如需在`\color`命令中使用自选 RGB 颜色，可使用`{\color[RGB]{0,0,0} }`命令，例如：

```
{\color[RGB]{0,200,0} e^{i \pi} + 1 = 0}
```

$$ {\color[RGB]{0,200,0} e^{i \pi} + 1 = 0} $$

##### 2.7.6 自定义颜色 Custom colors

可使用`\definecolor`命令进行自定义颜色，例如：

```
\definecolor{mygreen}{RGB}{0,200,0} {\color{mygreen}e^{i \pi} + 1 = 0 }
```

$$ \definecolor{mygreen}{RGB}{0,200,0} {\color{mygreen}e^{i \pi} + 1 = 0 } $$

#### 2.8 字体字号 Fonts & Size

##### 2.8.1 字体 Fonts

如您需要替换公式内容的字体，可以点击工具栏下方的**【字体】**按钮进行相关操作。因有一些特定代码 Mathjax 3.0 并没有相关支持，所以下表仅做参考。

| 样式                                                                                               | LaTeX                                                                                          |
| :----------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------- |
| 希腊字母 Greek alphabet                                                                              |                                                                                                |
| $\mathrm{A} \mathrm{B} \Gamma \Delta \mathrm{E} \mathrm{Z} \mathrm{H} \Theta$                    | \mathrm{A} \mathrm{B} \Gamma \Delta \mathrm{E} \mathrm{Z} \mathrm{H} \Theta                    |
| $\mathrm{I} \mathrm{K} \Lambda \mathrm{M} \mathrm{N} \Xi \mathrm{O} \Pi$                         | \mathrm{I} \mathrm{K} \Lambda \mathrm{M} \mathrm{N} \Xi \mathrm{O} \Pi                         |
| $\mathrm{R} \Sigma \mathrm{T} \Upsilon \Phi \mathrm{X} \Psi \Omega$                              | \mathrm{R} \Sigma \mathrm{T} \Upsilon \Phi \mathrm{X} \Psi \Omega                              |
| $\alpha \beta \gamma \delta \epsilon \zeta \eta \theta$                                          | \alpha \beta \gamma \delta \epsilon \zeta \eta \theta                                          |
| $\iota \kappa \lambda \mu \nu \xi \omicron \pi$                                                  | \iota \kappa \lambda \mu \nu \xi \omicron \pi                                                  |
| $\rho \sigma \tau \upsilon \phi \chi \psi \omega$                                                | \rho \sigma \tau \upsilon \phi \chi \psi \omega                                                |
| $\varGamma \varDelta \varTheta \varLambda \varXi \varPi \varSigma \varPhi \varUpsilon \varOmega$ | \varGamma \varDelta \varTheta \varLambda \varXi \varPi \varSigma \varPhi \varUpsilon \varOmega |
| $\varepsilon \digamma \varkappa \varpi \varrho \varsigma \vartheta \varphi$                      | \varepsilon \digamma \varkappa \varpi \varrho \varsigma \vartheta \varphi                      |
| 希伯来字母 Hebrew symbols                                                                             |                                                                                                |
| $\aleph \beth \gimel \daleth$                                                                    | \aleph \beth \gimel \daleth                                                                    |
| 黑板报体 Blackboard bold/scripts                                                                     |                                                                                                |
| $\mathbb{ABCDEFGHI}$                                                                             | \mathbb{ABCDEFGHI}                                                                             |
| $\mathbb{JKLMNOPQR}$                                                                             | \mathbb{JKLMNOPQR}                                                                             |
| $\mathbb{STUVWXYZ}$                                                                              | \mathbb{STUVWXYZ}                                                                              |
| 粗体 Boldface                                                                                      |                                                                                                |
| $\mathbf{ABCDEFGHI}$                                                                             | \mathbf{ABCDEFGHI}                                                                             |
| $\mathbf{JKLMNOPQR}$                                                                             | \mathbf{JKLMNOPQR}                                                                             |
| $\mathbf{STUVWXYZ}$                                                                              | \mathbf{STUVWXYZ}                                                                              |
| $\mathbf{abcdefghijklm}$                                                                         | \mathbf{abcdefghijklm}                                                                         |
| $\mathbf{nopqrstuvwxyz}$                                                                         | \mathbf{nopqrstuvwxyz}                                                                         |
| $\mathbf{0123456789}$                                                                            | \mathbf{0123456789}                                                                            |
| 粗体希腊字母 Boldface (Greek)                                                                          |                                                                                                |
| $\boldsymbol{\mathrm{A} \mathrm{B} \Gamma \Delta \mathrm{E} \mathrm{Z} \mathrm{H} \Theta}$       | \boldsymbol{\mathrm{A} \mathrm{B} \Gamma \Delta \mathrm{E} \mathrm{Z} \mathrm{H} \Theta}       |
| $\boldsymbol{\mathrm{I} \mathrm{K} \Lambda \mathrm{M} \mathrm{N} \Xi \mathrm{O} \Pi}$            | \boldsymbol{\mathrm{I} \mathrm{K} \Lambda \mathrm{M} \mathrm{N} \Xi \mathrm{O} \Pi}            |
| $\boldsymbol{\mathrm{R} \Sigma \mathrm{T} \Upsilon \Phi \mathrm{X} \Psi \Omega}$                 | \boldsymbol{\mathrm{R} \Sigma \mathrm{T} \Upsilon \Phi \mathrm{X} \Psi \Omega}                 |
| $\boldsymbol{\alpha \beta \gamma \delta \epsilon \zeta \eta \theta}$                             | \boldsymbol{\alpha \beta \gamma \delta \epsilon \zeta \eta \theta}                             |
| $\boldsymbol{\iota \kappa \lambda \mu \nu \xi \omicron \pi}$                                     | \boldsymbol{\iota \kappa \lambda \mu \nu \xi \omicron \pi}                                     |
| $\boldsymbol{\rho \sigma \tau \upsilon \phi \chi \psi \omega}$                                   | \boldsymbol{\rho \sigma \tau \upsilon \phi \chi \psi \omega}                                   |
| $\boldsymbol{\varepsilon\digamma\varkappa\varpi}$                                                | \boldsymbol{\varepsilon\digamma\varkappa\varpi}                                                |
| $\boldsymbol{\varrho\varsigma\vartheta\varphi}$                                                  | \boldsymbol{\varrho\varsigma\vartheta\varphi}                                                  |
| 斜体 Italics (拉丁字母默认 default for Latin alphabet)                                                   |                                                                                                |
| $\mathit{0123456789}$                                                                            | \mathit{0123456789}                                                                            |
| 罗马体 Roman typeface                                                                               |                                                                                                |
| $\mathrm{ABCDEFGHI}$                                                                             | \mathrm{ABCDEFGHI}                                                                             |
| $\mathrm{JKLMNOPQR}$                                                                             | \mathrm{JKLMNOPQR}                                                                             |
| $\mathrm{STUVWXYZ}$                                                                              | \mathrm{STUVWXYZ}                                                                              |
| $\mathrm{abcdefghijklm}$                                                                         | \mathrm{abcdefghijklm}                                                                         |
| $\mathrm{nopqrstuvwxyz}$                                                                         | \mathrm{nopqrstuvwxyz}                                                                         |
| $\mathrm{0123456789}$                                                                            | \mathrm{0123456789}                                                                            |
| 无衬线体 Sans serif                                                                                  |                                                                                                |
| $\mathsf{ABCDEFGHI}$                                                                             | \mathsf{ABCDEFGHI}                                                                             |
| $\mathsf{JKLMNOPQR}$                                                                             | \mathsf{JKLMNOPQR}                                                                             |
| $\mathsf{STUVWXYZ}$                                                                              | \mathsf{STUVWXYZ}                                                                              |
| $\mathsf{abcdefghijklm}$                                                                         | \mathsf{abcdefghijklm}                                                                         |
| $\mathsf{nopqrstuvwxyz}$                                                                         | \mathsf{nopqrstuvwxyz}                                                                         |
| $\mathsf{0123456789}$                                                                            | \mathsf{0123456789}                                                                            |
| 手写体 Calligraphy/花体 script                                                                        |                                                                                                |
| $\mathcal{ABCDEFGHI}$                                                                            | \mathcal{ABCDEFGHI}                                                                            |
| $\mathcal{JKLMNOPQR}$                                                                            | \mathcal{JKLMNOPQR}                                                                            |
| $\mathcal{STUVWXYZ}$                                                                             | \mathcal{STUVWXYZ}                                                                             |
| 德文尖角体 Fraktur typeface                                                                           |                                                                                                |
| $\mathfrak{ABCDEFGHI}$                                                                           | \mathfrak{ABCDEFGHI}                                                                           |
| $\mathfrak{JKLMNOPQR}$                                                                           | \mathfrak{JKLMNOPQR}                                                                           |
| $\mathfrak{STUVWXYZ}$                                                                            | \mathfrak{STUVWXYZ}                                                                            |
| $\mathfrak{abcdefghijklm}$                                                                       | \mathfrak{abcdefghijklm}                                                                       |
| $\mathfrak{nopqrstuvwxyz}$                                                                       | \mathfrak{nopqrstuvwxyz}                                                                       |
| $\mathfrak{0123456789}$                                                                          | \mathfrak{0123456789}                                                                          |
| 小型手写体 Small scriptstyle text                                                                     |                                                                                                |
| ${\scriptstyle\text{abcdefghijklm}}$                                                             | {\scriptstyle\text{abcdefghijklm}}                                                             |

##### 2.8.2 字号 Size

| 样式                              | LaTeX                           |
| :-------------------------------- | :------------------------------ |
| ${\tiny abc 巨小 tiny}$             | {\tiny abc 巨小 tiny}             |
| ${\scriptsize abc 超小 scriptsize}$ | {\scriptsize abc 超小 scriptsize} |
| ${\small abc 小 small}$             | {\small abc 小 small}             |
| ${\normalsize abc 正常 normal}$     | {\normalsize abc 正常 normal}     |
| ${\large abc 大 large}$             | {\large abc 大 large}             |
| ${\Large abc 超大 Large}$           | {\Large abc 超大 Large}           |
| ${\LARGE abc 特大 LARGE}$           | {\LARGE abc 特大 LARGE}           |
| ${\huge abc 巨大 huge}$             | {\huge abc 巨大 huge}             |
| ${\Huge abc 巨无霸 Huge}$           | {\Huge abc 巨无霸 Huge}           |

**注意：**如您导出**SVG 格式**，理论上字体的整体大小并无用处，因为**SVG**为矢量图，所以大可不必担心图片不清晰的问题，即便是您选择下载**PNG 格式**的公式图片，图片整体尺寸也被默认设定为**4 K**。所以此处的字号命令只为设置公式**相对大小**时使用，例如：

```
{\tiny x+y=z}x+y=z{\Huge x+y=z}
```

$$ {\tiny x+y=z}x+y=z{\Huge x+y=z} $$
 



#### 2.9 方程式编号 Equation numbering

本页面可采用开启 AMS 宏包的方式获得方程自动编号，AMS 拓展包的具体开启方式请参考 [2.11.4](https://www.latexlive.com/help#d59)。

默认自动编号只在部分环境中起作用，如{equation}、{eqnarray}等，例如：

在 AMS 包开启状态下，会在公式后进行自动编号：

```
\begin{eqnarray}
          E = mc^2 \\
          E^{i\pi}+1=0
          \end{eqnarray}
```

$$ \begin{eqnarray} E = mc^2 \tag{1}\\ e^{i\pi}+1=0 \tag{2} \end{eqnarray} $$

如您在开启了 AMS 包状态下，整个公式均不希望出现编号，可使用{equation*}、或者{eqnarray*}环境；或单个方程不希望出现编号，可以在指定方程后面添加`\nonumber`命令，如：

```
\begin{eqnarray*}
          E = mc^2 \\
          E^{i\pi}+1=0
          \end{eqnarray*}
```

$$ \begin{eqnarray*} E = mc^2 \\ e^{i\pi}+1=0 \end{eqnarray*} $$

```
\begin{eqnarray}
          E = mc^2 \\
          E^{i\pi}+1=0 \nonumber
          \end{eqnarray}
```

$$ \begin{eqnarray} E = mc^2 \tag{1} \\ e^{i\pi}+1=0 \nonumber \end{eqnarray} $$

如您在开启了 AMS 包状态下，个别公式不希望出现编号，或者个别公式希望出现特有编号，可在公式后面使用`\tag{}`或者`\notag`命令，如：

```
\begin{eqnarray}
          E = mc^2 \notag\\
          E^{i\pi}+1=0 \tag{b}
          \end{eqnarray}
```

$$ \begin{eqnarray} E = mc^2 \notag\\ e^{i\pi}+1=0 \tag{b} \end{eqnarray} $$
#### 2.10 LaTeX 环境 LaTeX environments

环境通常是对代码段的整体描述，用于表达此段代码的角色，如，是矩阵？单行公式？多行公式？还是对齐公式等（本页面不支持文档环境），不同的环境起到的作用不同。以`\begin{environments}`开始，`\end{environments}`结束。如最常用的矩阵命令，也是环境的一种，用法如下：

```
\begin{bmatrix}
          1 & 0 \\
          0 & 1
          \end{bmatrix}
```

$$ \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix} $$

具体矩阵用法可参考章节 [2.4](https://www.latexlive.com/help#d34)，下面给出几种其它常用环境的具体用法：

##### 2.10.1 equation 环境

`\begin{equation}`是单行公式环境，这意味着在此环境中只可以输入单行公式，同时`\\`等强制换行命令失效。如需对单行长公式进行强制换行，可使用`\begin{split}`环境进行嵌套，并用`&`字符表示对齐位置，如：

```
\begin{equation}
          \begin{split}
          E ^ { x } = & 1 + \frac { x } { 1 ! } + \frac { x ^ { 2 } } { 2 ! } + \frac { x ^ { 3 } } { 3 ! } + \cdots
          \\
          & - \infty < x < \infty
          \end{split}
          \end{equation}
```

$$ \begin{equation*} \begin{split} e ^ { x } = & 1 + \frac { x } { 1 ! } + \frac { x ^ { 2 } } { 2 ! } + \frac { x ^ { 3 } } { 3 ! } + \cdots \\ & - \infty < x < \infty \end{split} \end{equation*} $$

```
\begin{equation}`环境在排版时可能会出现重影错误，可通过对整体添加`{ }`解决，如`{\begin{equation}……\end{equation}}.
```

##### 2.10.2 eqnarray 环境

`\begin{eqnarray}`是多行公式环境，环境内的所有公式默认右对齐，由 LaTeX 内核提供。
##### 2.10.3 align 环境

`\begin{align}`是多行公式环境，环境内的所有公式默认右对齐，由 amsmath 提供，排版较为灵活，如需表示多行公式推荐使用此环境。

```
\begin{align}
          Y = x \\
          Y = 3 x^2 + 5 x + 2
          \end{align}
```

$$ \begin{align*} y = x \\ y = 3 x^2 + 5 x + 2 \end{align*} $$

可使用`&`字符调整对齐位置。

```
\begin{align}
          Y & = x \\
          Y & = 3 x^2 + 5 x + 2
          \end{align}
```

$$ \begin{align*} y & = x \\ y & = 3 x^2 + 5 x + 2 \end{align*} $$

 



##### 2.10.4 array 环境

`\begin{array}{}`是数组环境，需手动输入对齐参数：

```
\begin{array}{|c|l|r|}
          A & b & S \\
          \hline
          0 & 0 & 1 \\
          0 & 1 & 1 \\
          1 & 0 & 1 \\
          1 & 1 & 0 \\
          \end{array}
```

$$ \begin{array}{|c|l|r|} a & b & S \\ \hline 00 & 00 & 10 \\ 0 & 1 & 1 \\ 1 & 0 & 1 \\ 1 & 1 & 0 \\ \end{array} $$

对齐参数使用`c l r`分别表示居中、居左和居右，如需竖线边框可直接在对齐参数区域输入`|`即可，如需横线边框可使用`\hline`命令。

更多环境使用可参考章节 [2.4](https://www.latexlive.com/help#d31)。
#### 2.11 TeX 扩展包使用 TeX and LaTeX extensions

##### 2.11.1 physics 扩展包

Physics 是一款便携输入物理符号、矩阵及方程的拓展包，使用前需要在设置中手动勾选。

目前已知问题：

LaTeX 默认除号命令`\div`在 physics 包中有新的含义，表示。但直接输入`\div`可能会出现排版错误问题，此时可用`{\div}`替换，来解决排版问题。若需在 physics 包开启状态下显示默认除号，在其他 LaTeX 环境下可使用`\divisionsmybol`表示，但 MathJax 似乎并不支持此用法。替代解决办法为：①直接在输入框中输入`÷`字符。②在 unicode 扩展开启状态下，输入`\unicode{x 00 f 7}`。

以下参考样式请**手动打开 physics 扩展查看**。

| 样式（需开启 physics 扩展查看）                                | LaTeX                                                       |
| :----------------------------------------------------------- | :---------------------------------------------------------- |
| 括号 Automatic Bracing                                       |                                                             |
| $ \quantity{ \frac{1}{1+\frac{1}{2}} }$                      | \quantity{ }                                                |
| $\qty{ \frac{1}{1+\frac{1}{2}} }$                            | \qty{ }                                                     |
| $\pqty{ \frac{1}{1+\frac{1}{2}} }$                           | \pqty{ }                                                    |
| $\bqty{ \frac{1}{1+\frac{1}{2}} }$                           | \bqty{ }                                                    |
| $\vqty{ \frac{1}{1+\frac{1}{2}} }$                           | \vqty{ }                                                    |
| $\absolutevalue{ \frac{1}{1+\frac{1}{2}} }$                  | \absolutevalue{ }                                           |
| $\abs{ \frac{1}{1+\frac{1}{2}} }$                            | \abs{ }                                                     |
| $\norm{ \frac{1}{1+\frac{1}{2}} }$                           | \norm{ }                                                    |
| $\evaluated{ \frac{1}{1+\frac{1}{2}} }_1^2$                  | \evaluated{ }_1^2                                           |
| $\eval{ \frac{1}{1+\frac{1}{2}} }_1^2$                       | \eval{ }_1^2                                                |
| $\order{ \frac{x}{2} }$                                      | \order{ }                                                   |
| $\commutator{A} {B}$                                         | \commutator{A} {B}                                          |
| $\comm{A} {B}$                                               | \comm{A} {B}                                                |
| $\anticommutator{A} {B}$                                     | \anticommutator{A} {B}                                      |
| $\acomm{A} {B}$                                              | \acomm{A} {B}                                               |
| $\poissonbracket{A} {B}$                                     | \poissonbracket{A} {B}                                      |
| $\pb{A} {B}$                                                 | \pb{A} {B}                                                  |
| 矢量符号 Vector Notation                                     |                                                             |
| $\vectorbold{ a }$                                           | \vectorbold{ }                                              |
| $\vb{ a }$                                                   | \vb{ }                                                      |
| $\vb{ \psi }$                                                | \vb{ }                                                      |
| $\vb*{ a }$                                                  | \vb*{ }                                                     |
| $\vb*{ \psi }$                                               | \vb*{ }                                                     |
| $\vectorarrow{ a }$                                          | \vectorarrow{ }                                             |
| $\va{ a }$                                                   | \va{ }                                                      |
| $\va{ \psi }$                                                | \va{ }                                                      |
| $\va*{ a }$                                                  | \va*{ }                                                     |
| $\va*{ \psi }$                                               | \va*{ }                                                     |
| $\vectorunit{ a }$                                           | \vectorunit{ }                                              |
| $\vu{ a }$                                                   | \vu{ }                                                      |
| $\vu{ \psi }$                                                | \vu{ }                                                      |
| $\vu*{ a }$                                                  | \vu*{ }                                                     |
| $\vu*{ \psi }$                                               | \vu*{ }                                                     |
| $\dotproduct$                                                | \dotproduct                                                 |
| $\vdot$                                                      | \vdot                                                       |
| $\crossproduct$                                              | \crossproduct                                               |
| $\cross$                                                     | \cross                                                      |
| $\cp$                                                        | \cp                                                         |
| $\gradient ( \psi )$                                          | \gradient ( )                                                |
| $\grad ( \psi )$                                              | \grad ( )                                                    |
| $\grad[ \psi ]$                                              | \grad[ ]                                                    |
| $\grad{ \psi }$                                              | \grad{ }                                                    |
| $\divergence ( \psi )$                                        | \divergence ( )                                              |
| $\div ( \psi )$                                               | \div ( )                                                     |
| $\div[ \psi ]$                                               | \div[ ]                                                     |
| $\div{ \psi }$                                               | \div{ }                                                     |
| $\curl ( \psi )$                                              | \curl ( )                                                    |
| $\curl[ \psi ]$                                              | \curl[ ]                                                    |
| $\curl{ \psi }$                                              | \curl{ }                                                    |
| $\laplacian ( \psi )$                                         | \laplacian ( )                                               |
| $\laplacian[ \psi ]$                                         | \laplacian[ ]                                               |
| $\laplacian{ \psi }$                                         | \laplacian{ }                                               |
| 运算符 Operators                                             |                                                             |
| $\sin x$                                                     | \sin                                                        |
| $\sin ( x )$                                                  | \sin ( )                                                     |
| $\sin[2]( x )$                                               | \sin[2]( )                                                  |
| $\tr \rho$                                                   | \tr                                                         |
| $\Tr \rho$                                                   | \Tr                                                         |
| $\rank M$                                                    | \rank                                                       |
| $\erf ( x )$                                                  | \erf ( )                                                     |
| $\Res[ f (z) ]$                                               | \Res[ ]                                                     |
| $\principalvalue{ \int f (z) \dd{z} }$                        | \principalvalue{ }                                          |
| $\pv{ \int f (z) \dd{z} }$                                    | \pv{ }                                                      |
| $\PV{ \int f (z) \dd{z} }$                                    | \PV{ }                                                      |
| $\Re{ \frac{1}{1+\frac{i}{2}} }$                             | \Re{ }                                                      |
| $\Im{ \frac{1}{1+\frac{i}{2}} }$                             | \Im{ }                                                      |
| 快速文本 Quick Quad Text                                     |                                                             |
| $\qqtext{ some texts }$                                      | \qqtext{ }                                                  |
| $\qq{ some texts }$                                          | \qq{ }                                                      |
| $\qq*{ some texts }$                                         | \qq*{ }                                                     |
| $\qcomma$                                                    | \qcomma                                                     |
| $\qc$                                                        | \qc                                                         |
| $\qcc $                                                      | \qcc                                                        |
| $\qif $                                                      | \qif                                                        |
| $\qthen$                                                     | \qthen                                                      |
| $\qelse$                                                     | \qelse                                                      |
| $\qotherwise$                                                | \qotherwise                                                 |
| $\qunless $                                                  | \qunless                                                    |
| $\qgiven$                                                    | \qgiven                                                     |
| $\qusing$                                                    | \qusing                                                     |
| $\qassume $                                                  | \qassume                                                    |
| $\qlet$                                                      | \qlet                                                       |
| $\qfor$                                                      | \qfor                                                       |
| $\qall$                                                      | \qall                                                       |
| $\qeven$                                                     | \qeven                                                      |
| $\qodd$                                                      | \qodd                                                       |
| $\qinteger$                                                  | \qinteger                                                   |
| $\qand$                                                      | \qand                                                       |
| $\qor $                                                      | \qor                                                        |
| $\qas $                                                      | \qas                                                        |
| $\qin $                                                      | \qin                                                        |
| 导数 Derivatives                                             |                                                             |
| $\differential{ x }$                                         | \differential{ }                                            |
| $\dd{ x }$                                                   | \dd{ }                                                      |
| $\dd[3] {x}$                                                 | \dd[3] {x}                                                  |
| $\dd ( \cos\theta )$                                          | \dd ( )                                                      |
| $\dv{ x }$                                                   | \dv{ }                                                      |
| $\derivative{ f }{x}$                                        | \derivative{ }{x}                                           |
| $\dv{ f }{x}$                                                | \dv{ }{x}                                                   |
| $\dv[ n ]{f}{x}$                                             | \dv[ ]{f}{x}                                                |
| $\dv{x}( x^2+x^3 )$                                          | \dv{x}( )                                                   |
| $\dv*{ f }{x}$                                               | \dv*{ }{x}                                                  |
| $\pdv{ x }$                                                  | \pdv{ }                                                     |
| $\partialderivative{ f }{x}$                                 | \partialderivative{ }{x}                                    |
| $\pdv{ f }{x}$                                               | \pdv{ }{x}                                                  |
| $\pdv[ n ]{f}{x}$                                            | \pdv[ ]{f}{x}                                               |
| $\pdv{x}( x^2+x^3 )$                                         | \pdv{x}( )                                                  |
| $\pdv{ f }{x}{y}$                                            | \pdv{ }{x}{y}                                               |
| $\variation{ F[g (x)] }$                                      | \variation{ }                                               |
| $\var{ F[g (x)] }$                                            | \var{ }                                                     |
| $\var ( E-TS )$                                               | \var ( )                                                     |
| $\fdv{ g }$                                                  | \fdv{ }                                                     |
| $\functionalderivative{ F }{g}$                              | \functionalderivative{ }{g}                                 |
| $\fdv{ F }{g}$                                               | \fdv{ }{g}                                                  |
| $\fdv{V}( E-TS )$                                            | \fdv{V}( )                                                  |
| $\fdv*{ F }{x}$                                              | \fdv*{ }{x}                                                 |
| 狄拉克符号 Dirac Bracket Notation                            |                                                             |
| $\ket{ \frac{\psi + \phi}{2} }$                              | \ket{ }                                                     |
| $\ket*{ \frac{\psi + \phi}{2} }$                             | \ket*{ }                                                    |
| $\bra{ \frac{\psi + \phi}{2} }$                              | \bra{ }                                                     |
| $\bra*{ \frac{\psi + \phi}{2} }$                             | \bra*{ }                                                    |
| $\innerproduct{\frac{\psi + \phi}{2}}{\frac{\psi + \phi}{2}}$ | \innerproduct{\frac{\psi + \phi}{2}}{\frac{\psi + \phi}{2}} |
| $\braket{\frac{\psi + \phi}{2}}{\frac{\psi + \phi}{2}}$      | \braket{\frac{\psi + \phi}{2}}{\frac{\psi + \phi}{2}}       |
| $\braket*{\frac{\psi + \phi}{2}}{\frac{\psi + \phi}{2}}$     | \braket*{\frac{\psi + \phi}{2}}{\frac{\psi + \phi}{2}}      |
| $\braket{ \frac{\psi + \phi}{2} }$                           | \braket{ }                                                  |
| $\outerproduct{\frac{\psi + \phi}{2}}{\frac{\psi + \phi}{2}}$ | \outerproduct{\frac{\psi + \phi}{2}}{\frac{\psi + \phi}{2}} |
| $\dyad{\frac{\psi + \phi}{2}}{\frac{\psi + \phi}{2}}$        | \dyad{\frac{\psi + \phi}{2}}{\frac{\psi + \phi}{2}}         |
| $\ketbra{\frac{\psi + \phi}{2}}{\frac{\psi + \phi}{2}}$      | \ketbra{\frac{\psi + \phi}{2}}{\frac{\psi + \phi}{2}}       |
| $\op{\frac{\psi + \phi}{2}}{\frac{\psi + \phi}{2}}$          | \op{\frac{\psi + \phi}{2}}{\frac{\psi + \phi}{2}}           |
| $\ketbra*{\frac{\psi + \phi}{2}}{\frac{\psi + \phi}{2}}$     | \ketbra*{\frac{\psi + \phi}{2}}{\frac{\psi + \phi}{2}}      |
| $\ketbra{ \frac{\psi + \phi}{2} }$                           | \ketbra{ }                                                  |
| $\expectationvalue{ \frac{\psi + \phi}{2} }$                 | \expectationvalue{ }                                        |
| $\expval{ \frac{\psi + \phi}{2} }$                           | \expval{ }                                                  |
| $\ev{ \frac{\psi + \phi}{2} }$                               | \ev{ }                                                      |
| $\ev{ \frac{A+B}{2} }{\psi}$                                 | \ev{ }{\psi}                                                |
| $\ev*{ \frac{\psi + \phi}{2} }$                              | \ev*{ }                                                     |
| $\ev**{ \frac{\psi + \phi}{2} }$                             | \ev**{ }                                                    |
| $\matrixelement{m}{ \frac{A+B}{2} }{n}$                      | \matrixelement{m}{ }{n}                                     |
| $\matrixel{m}{ \frac{A+B}{2} }{n}$                           | \matrixel{m}{ }{n}                                          |
| $\mel{m}{ \frac{A+B}{2} }{n}$                                | \mel{m}{ }{n}                                               |
| $\mel*{m}{ \frac{A+B}{2} }{n}$                               | \mel*{m}{ }{n}                                              |
| $\mel**{m}{ \frac{A+B}{2} }{n}$                              | \mel**{m}{ }{n}                                             |
| 矩阵宏 Matrix macros                                         |                                                             |
| $\mqty{a & b \\ c & d}$                                      | \mqty{a & b \\ c & d}                                       |
| $\mqty (a & b \\ c & d)$                                      | \mqty (a & b \\ c & d)                                       |
| $\mqty*(a & b \\ c & d)$                                     | \mqty*(a & b \\ c & d)                                      |
| $\mqty[a & b \\ c & d]$                                      | \mqty[a & b \\ c & d]                                       |
| $\mqty\|a & b \\ c & d\|$                                    | \mqty\|a & b \\ c & d\|                                     |
| $\smqty{a & b \\ c & d}$                                     | \smqty{a & b \\ c & d}                                      |
| $\smqty (\imat{3})$                                           | \smqty (\imat{3})                                            |
| $\smqty (\xmat{1}{2}{3})$                                     | \smqty (\xmat{1}{2}{3})                                      |
| $\smqty (\xmat*{a}{3}{3})$                                    | \smqty (\xmat*{a}{3}{3})                                     |
| $\smqty (\xmat*{a}{3}{1})$                                    | \smqty (\xmat*{a}{3}{1})                                     |
| $\smqty (\xmat*{a}{1}{3})$                                    | \smqty (\xmat*{a}{1}{3})                                     |
| $\smqty (\zmat{2}{2})$                                        | \smqty (\zmat{2}{2})                                         |
| $\smqty (\pmat{0})$                                           | \smqty (\pmat{0})                                            |
| $\smqty (\pmat{1})$                                           | \smqty (\pmat{1})                                            |
| $\smqty (\pmat{2})$                                           | \smqty (\pmat{2})                                            |
| $\smqty (\pmat{3})$                                           | \smqty (\pmat{3})                                            |
| $\mqty (\dmat{1,2,3})$                                        | \mqty (\dmat{1,2,3})                                         |
| $\mqty (\dmat{1,2&3\\4&5})$                                   | \mqty (\dmat{1,2&3\\4&5})                                    |
| $\mqty (\admat{1,2,3})$                                       | \mqty (\admat{1,2,3})                                        |

其它具体用法可参考 [physics扩展官方文档](http://mirrors.ibiblio.org/CTAN/macros/latex/contrib/physics/physics.pdf)。

##### 2.11.2 mhchem 扩展包

Mhchem 是一款便捷输入化学方程式的扩展包，使用前需要在设置中手动勾选。其具体用法如下：

###### 2.11.2.1 引用

基本命令为`\ce{}`，可在`{}`中输入化学相关符号。

###### 2.11.2.2 化学式

在化学环境中，数字`0123456789`默认为下标，`+-`默认为上标，如需强制上标可使用`^`符号，例如

```
\ce{H 2 O} \ce{Sb 2 O 3} \ce{H+} \ce{CrO 4^2-} \ce{[AgCl 2]-} \ce{Y^99+} \ce{Y^{99+}}
```

$\ce{H 2 O} \quad \ce{Sb 2 O 3} \quad \ce{H+} \quad \ce{CrO 4^2-} \quad \ce{[AgCl 2]-} \quad \ce{Y^99+} \quad \ce{Y^{99+}}$

###### 2.11.2.3 化学计量数

在化学环境中，计量数应与前面的大写字母使用**空格**分割，对于分数计量数，只需输入`1/2`即可显示$\frac{1}{2}$的效果，如特殊情况需要显示`1/2`格式，请用`( )`扩起。

```
\ce{2 H 2 O} \ce{0.5 H 2 O} \ce{1/2 H 2 O} \ce{(1/2) H 2 O} \ce{$n$ H 2 O}
```

$\ce{2 H 2 O} \quad \ce{0.5 H 2 O} \quad \ce{1/2 H 2 O} \quad \ce{(1/2) H 2 O} \quad \ce{n H 2 O}$

###### 2.11.2.4 同位素

```
\ce{^{227}_{90}Th+} \ce{^227_90 Th+} \ce{^{0}_{-1}n^{-}} \ce{^0_-1 n-}
```

$\ce{^{227}_{90}Th+} \quad \ce{^227_90 Th+} \quad \ce{^{0}_{-1}n^{-}} \quad \ce{^0_-1 n-}$

在一个复杂的化学式中，上标属于左侧元素还是右侧元素可能并不会明显的体现出来，但为了规范输入，建议使用`{}`分隔符作为区分：

```
\ce{H{}^3 HO} \ce{H^3 HO}
```

$\ce{H{}^3 HO} \quad \ce{H^3 HO}$

###### 2.11.2.5 反应箭头

Mhchem 提供了方便的反应箭头输入模式

```
\ce{A -> B} \ce{A <- B} \ce{A <-> B}
```

$\ce{A -> B} \ce{A <- B} \ce{A <-> B} $

```
\ce{A <--> B} \ce{A <=> B} \ce{A <=>> B} \ce{A <<=> B}
```

$\ce{A <--> B} \ce{A <=> B} \ce{A <=>> B} \ce{A <<=> B}$

箭头可以带有两个参数，即`->[][]`，第一个`[]`表示上方参数，第二个`[]`表示下方参数

```
\ce{A ->[H 2 O] B} \ce{A ->[{上方文字}][{下方文字}] B}
```

$\ce{A ->[H 2 O] B} \ce{A ->[{上方文字}][{下方文字}] B}$

###### 2.11.2.6 气体和沉淀

在化学环境中可使用独立的`^`表示气体$\uparrow$，使用独立的`v`(小写字母 v) 表示沉淀$\downarrow$

```
\ce{SO 4^2- + Ba^2+ -> BaSO 4 v}
```

$\ce{SO 4^2- + Ba^2+ -> BaSO 4 v}$

```
\ce{A v B (v) -> B ^ B (^)}
```

$\ce{A v B (v) -> B ^ B (^)}$

###### 2.11.2.7 一些复杂的例子

```
\ce{Zn^2+ <=>[+ 2 OH-][+ 2 H+] $\underset{\text{amphoteres Hydroxid}}{\ce{Zn (OH) 2 v}}$ <=>[+
          2 OH-][+ 2 H+] $\underset{\text{Hydroxozikat}}{\ce{[Zn (OH) 4]^2-}}$}
```

$\ce{Zn^2+ <=>[+ 2 OH-][+ 2 H+] $\underset{\text{amphoteres Hydroxid}}{\ce{Zn (OH) 2 v}}$ <=>[+ 2 OH-][+ 2 H+] $\underset{\text{Hydroxozikat}}{\ce{[Zn (OH) 4]^2-}}$}$

```
\ce{$K = \frac{[\ce{Hg^2+}][\ce{Hg}]}{[\ce{Hg 2^2+}]}$}
```

$\ce{$K = \frac{[\ce{Hg^2+}][\ce{Hg}]}{[\ce{Hg 2^2+}]}$}$

```
\ce{$K = \ce{\frac{[Hg^2+][Hg]}{[Hg 2^2+]}}$}
```

$\ce{$K = \ce{\frac{[Hg^2+][Hg]}{[Hg 2^2+]}}$}$

```
\ce{Hg^2+ ->[I-] $\underset{\mathrm{red}}{\ce{HgI 2}}$ ->[I-]
          $\underset{\mathrm{red}}{\ce{[Hg^{II}I 4]^2-}}$}
```

$\ce{Hg^2+ ->[I-] $\underset{\mathrm{red}}{\ce{HgI 2}}$ ->[I-] $\underset{\mathrm{red}}{\ce{[Hg^{II}I 4]^2-}}$}$

 



##### 2.11.3 cancel 扩展包

Cancel 扩展包为显示分数中**约分线**的 TeX 宏包，或显示其他划除效果，基本命令为`\cancel{}`，例如：

```
\cfrac{x}{1 + \cfrac{\cancel{y}}{\cancel{y}}} = \cfrac{x}{2}
```

$\cfrac{x}{1 + \cfrac{\cancel{y}}{\cancel{y}}} = \cfrac{x}{2}$

```
\cancel{e^{i \pi} + 1 =0}
```

$\cancel{e^{i \pi} + 1 =0}$

##### 2.11.4 Ams 扩展包

本页面集成了大部分 ams 命令，即默认已打开。本拓展只为自动显示公式序号使用。

如，以下代码：

```
\begin{equation}
          E = mc^2
          \end{equation}
        
```

 

在 ams 包未开启状态下：

$$ \begin{equation*} E = mc^2 \end{equation*} $$

在 ams 包开启状态下：

$$ \begin{equation} E = mc^2 \tag{1} \end{equation} $$

具体自动编号用法请参考章节 [2.9](https://www.latexlive.com/help#d49)。



##### 2.11.5 AmsCd 扩展包

AmsCd 扩展包是一款生成矩阵图的 TeX 宏包环境，基本环境命令为`\begin{CD}` `\end{CD}`，基本用法如下：

`@<<<`表示左箭头；

`@>>>`表示右箭头；

`@AAA`表示上箭头；

`@VVV`表示下箭头；

`@=`表示水平等号；

`@|`表示竖直等号；

`@.`表示空箭头（占位）。

以`@`表示箭头开始，以`<、>、A、V`等表示箭头方向。如需在箭头上或下插入变量，直接在第一和第二，或第二和第三个箭头方向符号中插入即可，用法实例如下：

```
\begin{CD}
          A @>a>> B\\
          @VVbV @VVcV\\
          C @>d>> D
          \end{CD}
        
```

$\begin{CD} A @>a>> B\\ @VVbV @VVcV\\ C @>d>> D \end{CD}$

```
\begin{CD}
          A @>a>b> B\\
          @VlVrV @AlArA\\
          C @<a<b< D
          \end{CD}
        
```

$\begin{CD} A @>a>b> B\\ @VlVrV @AlArA\\ C @<a<b< D \end{CD}$

 



##### 2.11.6 Unicode 扩展包

Unicode 扩展包一款显示 Unicode 字符的 TeX 宏包，基本命令为`\unicode{}`，`{}`中参数应输入指定字符的**十进制**或**十六进制**Unicode 代码，注意十六进制编码需在前面添加标识位`x`，例如：

```
\unicode{8751} \unicode{x 220 f}
        
```

$\unicode{8751} \quad \unicode{x 220 f}$

 



##### 2.11.7 Bbox 扩展包

Bbox 扩展包一款用于设置公式背景颜色的 TeX 宏包，具体用法参见 [2.7.3](https://www.latexlive.com/help#d42)



##### 2.11.8 NoErrors 扩展包

NoErrors 扩展包是一款阻止显示 TeX 错误消息的宏包，使用后将不会显示代码具体错误，而只会显示原始 TeX 代码。



##### 2.11.9 NewCommand 扩展包

Newcommand 扩展包提供了`\def, \newcommand，\renewcommand，\let，\newenvironment`和`\renewenvironment`宏命令，用于在 TeX 中创建新的宏和环境。例如：

```
\def\RR {{\bf R}} %将{\bf R}（加粗的 R）定义为\RR
\RR %调用\RR 命令
```

$\def\RR {{\bf R}} \RR$





