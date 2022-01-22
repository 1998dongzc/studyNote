# HTML笔记

#### 1.不使用HTML5规范中不推荐使用的元素如：<basefont><big><blink><center><font><marquee><multicol><nobr><spacer><tt><acronym><applet><bgsound><frame><frameset><noframes><isindex><dir><hgroup><listing><nextid><noembed><plaintext><strike><xmp>

#### 2.非必需情况，不添加强制改变文档模式的 <meta> 标签。

#### 3.不使用HTML5规范中不推荐使用的属性。

#### 4.元素的标签和属性名必须小写, 且属性值使用双引号

#### 5.密码输入框请设置属性autocomplete="off"。

#### 6.<input> <select> <textarea>元素，搭配对应label标签及其“for”属性，提高页面交互。

#### 7.为了兼容js禁用模式的浏览，<a>元素的href属性值不推荐使用“#”或“javascript:void(0)”。

#### 8.通过给元素设置自定义属性来存放与 JavaScript 交互的数据，属性名格式为 data-xx。

#### 9.尽量使用项目中的图片，少在img中引入URLs图片，避免因URL图片不稳定导致的页面不良体验。

#### 10.元素样式，写在css文件夹中，不推荐写“行内样式”。

#### 11.文件名不得含有空格和特殊符号文件名建议只使用小写字母，不使用大写字母。文件名包含多个单词时，单词之间建议使用半角的连词线 ( - ) 分隔。

#### 12.静态资源：icon类单色图标，尽量使用icon-font或SVG技术。若无法使用icon-font和svg，也要使用css sprites技术，合并压缩图片，减少静态资源请求数量。图片作为内容，比如照片等采用jpg格式，且按照实际情况进行压缩。对于带透明部分的图片，如果不考虑ie6采用png格式；如果考虑ie6，则采用gif格式。css、js源文件，建议在上线前进行压缩、添加md5戳修改页面对应引用。

#### 13.属性顺序,HTML 属性应当按照以下给出的顺序依次排列，确保代码的易读性。class,id,namedata-*src,for,type,href,title,alt,aria-*,role。
