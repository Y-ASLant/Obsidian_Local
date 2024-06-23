# 基础属性一览

> [!NOTE] Modifier中属性非常多，学完了Modifier，Compose就学了一半

### Modifier.height(height: Dp)

> `设置自身的高度，单位dp，值可以被覆盖`

![[ASLant_Files/88ee6d51752b9ab3f20b123924778dd6_MD5.webp]]

### - Modifier.height(intrinsicSize: IntrinsicSize)

> `类似于layout_height="wrap_content"`

![[ASLant_Files/f5f8c804e943466acd54b92065a2d09a_MD5.webp]]

### - Modifier.heightIn(min: Dp, max: Dp)

> `min等价于minHeight，max等价于maxHeight，不设置max，效果等价于layout_height="match_parent"`

![[ASLant_Files/31efa6fe992fb44eab30a95095d31083_MD5.webp]]

![[ASLant_Files/3cd95e24ada49e3039982f4535657949_MD5.webp]]

### - Modifier.width(width: Dp)

> `设置自身的宽度度，单位dp，值可以被覆盖`

- Modifier.width(intrinsicSize: IntrinsicSize)

> `类似于layout_width="wrap_content"`

![[ASLant_Files/271c2d988b7b372f3fc7f9446d66afec_MD5.webp]]

- Modifier.widthIn(min: Dp, max: Dp)

> `min等价于minWidth，max等价于maxWidth，不设置max，效果等价于layout_Width="match_parent"`

![[ASLant_Files/d7546efd09d0d1bf945b1055fa6c1929_MD5.webp]]

- Modifier.fillMaxHeight(fraction: Float)

> `layout_height="match_parent"`fraction 百分比

![[ASLant_Files/90825ab23281be76940bc951ffc828b3_MD5.webp]]

- Modifier.fillMaxWidth(fraction: Float)

> `layout_width="match_parent"`fraction 百分比

![[ASLant_Files/5fc6765f5db72099843fc691009de46f_MD5.webp]]

- Modifier.fillMaxSize(fraction: Float)

> `fillMaxHeight+fillMaxWidth`fraction 百分比

![[ASLant_Files/0c6162ccf10b859b10a1a7414a568631_MD5.webp]]

- Modifier.size(size: Dp)

> `设置宽高 width=height=size` ![[ASLant_Files/3c9d04f144facc1c1c941a1b6ed94ab8_MD5.webp]]

- Modifier.size(width: Dp, height: Dp)

> `设置宽高`

![[ASLant_Files/a702ad7f60605a85b195e84ec33663e6_MD5.webp]]

- Modifier.sizeIn(minWidth: Dp, minHeight: Dp, maxWidth: Dp, maxHeight: Dp)

> `Modifier.heightIn,Modifier.widthIn的组合使用`

![[ASLant_Files/3fe3605e36dde1583cf240f06db2135b_MD5.webp]]

![[ASLant_Files/e08d9605d0da3f0fbc171d9c781534bc_MD5.webp]]

- Modifier.defaultMinSize(minWidth: Dp, minHeight: Dp)

> `设置最小宽高`等价于.sizeIn(minWidth: Dp, minHeight: Dp)

- Modifier.shadow(elevation: Dp, shape: Shape, clip: Boolean)

> `设置阴影，阴影大小，形状，是否裁剪`clip = elevation>0

![[ASLant_Files/6d6e1b22aaf55d9ba9feff4e7a2e19be_MD5.webp]]

- Modifier.wrapContentHeight(align: Alignment.Vertical,unbounded: Boolean)

> `设置高度自适应，align 设置对其方式（默认纵向居中）,unbounded设置是否可以“无界”，true可以超越父布局高度`，可以从下图看出越界效果

![[ASLant_Files/abfdd4a7e1b7f4d4664b9693eb3d6be0_MD5.webp]]

![[ASLant_Files/30d639d9227c8a727a6a9055e20f2c76_MD5.webp]]

- Modifier.wrapContentWidth(align: Alignment.Horizontal,unbounded: Boolean)

> `设置宽度自适应，align 设置对其方式（默认横向居中）,unbounded设置是否可以“无界”，true可以超越父布局宽度`

- Modifier.wrapContentSize(align: Alignment, unbounded: Boolean)

> `设置宽高自适应，align 设置对其方式（默认居中）,unbounded设置是否可以“无界”，true可以超越父布局大小`

- Modifier.paddingFrom(alignmentLine: AlignmentLine, before: Dp, after: Dp)

> alignmentLine 为 FirstBaseline，LastBaseline，before为表示文本**第一行/最后一行 Baseline**的位置距离父级 **top/start 的距离**，after为表示文本**第一行/最后一行 Baseline**的位置距离父级 **bottom/end 的距离**

![[ASLant_Files/97cb40e929748a256986bbf523003b39_MD5.webp]]

![[ASLant_Files/9db8011ccfa628298456b94f648728cb_MD5.webp]]

- Modifier.paddingFrom(alignmentLine: AlignmentLine,before: TextUnit,after: TextUnit)

> `同上，before，after可以设置TextUnit，例如sp`

![[ASLant_Files/9decd2a2b2d42bf5b7c57c6ef29d5ae3_MD5.webp]]

- Modifier.paddingFromBaseline(top: Dp, bottom: Dp)

> `top对应FirstBaseline，buttom对应LastBaseline`

![[ASLant_Files/f835866d88707a1d53d0f73ee134ede4_MD5.webp]]

![[ASLant_Files/c73c5d00b87c633a5f241e69326c0b5a_MD5.webp]]

- Modifier.paddingFromBaseline(top: TextUnit, bottom: TextUnit)

> `同上top，bttom可以设置TextUnit，例如sp`

- Modifier.alpha(alpha: Float)

> `设置透明度alpha`

![[ASLant_Files/b760c2a89b5678fece5cfbeb452d3ead_MD5.webp]]

- Modifier.clip(shape: Shape)

> `设置切角shape` ![[ASLant_Files/4eae07c95d025aaa00f761934dfa33c7_MD5.webp]]

- Modifier.clipToBounds()

> `按照指定的边界裁切内容, 类似Android中的子View内容不超过父View`

- Modifier.background(color: Color, shape: Shape)

> `设置背景色Color，切角shape`

![[ASLant_Files/aa74249fb9638b7849b698c3b3e3dd7f_MD5.webp]]

- Modifier.background(brush: Brush, shape: Shape, alpha: Float)

> `设置填充色（渐变）brush，切角shape，透明度alpha`

![[ASLant_Files/4b23bd49d632c139ae3921d14669e018_MD5.webp]]

- Modifier.border(width: Dp, color: Color, shape: Shape)

> `设置设置边框宽度width，颜色color，边框形状shape`

![[ASLant_Files/227dd7884c46b3c56720a4e6a4825fce_MD5.webp]]

- Modifier.border(width: Dp, brush: Brush, shape: Shape)

> `设置设置边框宽度width，边框填充色（渐变）brush，边框形状shape`

![[ASLant_Files/8a2de7bc28af9dd6a6f67e6444bbe65a_MD5.webp]]

- Modifier.border(border: BorderStroke, shape: Shape)

> `BorderStroke(val width: Dp, val brush: Brush)同上`

- Modifier.clickable(interactionSource:MutableInteractionSource, indication: Indication?, enabled: Boolean,onClickLabel: String?,role: Role?, onClick: () -> Unit)

> `设置点击事件onClick，interactionSource交互事件（可自定义），enabled是否可以点击，role 用户界面元素的类型配合interactionSource实现自定义交互事件处理，onClickLabel 无障碍描述`

- Modifier.combinedClickable(interactionSource: MutableInteractionSource, indication: Indication?,enabled: Boolean,onClickLabel: String?,role: Role?, onLongClickLabel: String?, onLongClick: () -> Unit, onDoubleClick: () -> Unit, onClick: () -> Unit )

> `设置组合点击事件包含combinedClickable( onLongClick = { /*....*/ }, onDoubleClick ={ /*....*/ }, onClick = { /*....*/ }),`

![[ASLant_Files/aa74249fb9638b7849b698c3b3e3dd7f_MD5.webp]]

- Modifier.layoutId(layoutId: Any)

> `标记组建id,主要配合measure: MeasureScope使用`

- Modifier.layout( measure: MeasureScope.(Measurable, Constraints) -> MeasureResult )

> `通过 layoutId匹配 measurable.layoutId进行自定义处理`

- Modifier.offset(x: Dp, y: Dp)

> `等效于"android:layout_margin",当布局方向LayoutDirection为LTR时，正x偏移将向右移动内容，当布局方向为RTL时，正x偏移将向左移动内容

![[ASLant_Files/6120f3e7e006f3f8b710663966e63030_MD5.webp]]

![[ASLant_Files/44878e1bb4585b8669723bae35a038f8_MD5.webp]]

![[ASLant_Files/b38eaf6d3fbe21601655731e0f1e0e3f_MD5.webp]]

- Modifier.offset(offset: Density.() -> IntOffset)

> `用于动态更改offset 当布局方向LayoutDirection为LTR时，正x偏移将向右移动内容，当布局方向为RTL时，正x偏移将向左移动内容`

![[ASLant_Files/020b8d96d86377fa8ad1d1f8420e082a_MD5.webp]]

- Modifier.absoluteOffset(x: Dp, y: Dp)

> `absoluteOffset，不考虑布局方向LayoutDirection：正X偏移将总是向右移动内容`

![[ASLant_Files/edfc3a007fd5c7935fa59e9331b6cbb5_MD5.webp]]

![[ASLant_Files/755f7c44381ac49e1ae2701518fab8c7_MD5.webp]]

> `Ltr效果同offset` ![[ASLant_Files/f5788dcb51b50072b319f7c1e99983e6_MD5.webp]]

- Modifier.absoluteOffset(offset: Density.() -> IntOffset)

> `用法同- Modifier.offset(offset: Density.() -> IntOffset)，不考虑布局方向LayoutDirection：正X偏移将总是向右移动内容`

- Modifier.padding(start: Dp, top: Dp, end: Dp, bottom: Dp)

> `等效于"android:padding",偏移出父控件会被裁剪` ![[ASLant_Files/e7b94771a8aaf929c3389ec6f0666a7f_MD5.webp]]

![[ASLant_Files/b43df5c94290b726a19069daec56c3d1_MD5.webp]]

- Modifier.padding(all: Dp)

> `等效于"android:padding",偏移出父控件会被裁剪 all = start = end = top = bottom`

![[ASLant_Files/4bd597384a07eb54c582504d5d2973f9_MD5.webp]]

- Modifier.padding(horizontal: Dp, vertical: Dp)

> `等效于"android:padding",偏移出父控件会被裁剪 horizontal = start = end,vertical = top = bottom` ![[ASLant_Files/2b267dad5726ef34ce9c9d878aaef052_MD5.webp]]

- Modifier.padding(paddingValues: PaddingValues)

> `PaddingValues(horizontal, vertical) &nbsp; PaddingValues(start,top,end,bottom)` ![[ASLant_Files/1e509fc73be456c2137d814af3b0b0f9_MD5.webp]]

- Modifier.absolutePadding(left: Dp, top: Dp, right: Dp, bottom: Dp)

> `区别于Padding的地方是absolutePadding不考虑布局方向LayoutDirection：正X偏移将总是向右移动内容`

![[ASLant_Files/f8e264d48335314d5a42aab8264aef0c_MD5.webp]]

> `LayoutDirection.Rtl时，left和right的值互换`

![[ASLant_Files/7a37caa7a424c9bd6be9e7a23cc7876d_MD5.webp]]

## 总结

  

作者：Yorashe  
链接：https://juejin.cn/post/6999464923822555143  
来源：稀土掘金  
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。