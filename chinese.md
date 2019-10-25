# 中文支持
  1、下载类库语言安装脚本
    https://github.com/dompdf/utils.git

  2、将里面的load_font.php文件拷贝到项目根目录，和verdon同级

  3、下载一个宋体字体 simsun.ttf,也放到项目根目录，这时load_font.php和simsun.ttf应该在同一级目录

  4、开始安装字体，使用命令行进入当前目录,并安装字体
	php load_font.php simsun.ttf simsun

  命令说明 php load_font.php 调用这个文件，并传入字体路径，字体名字
  注意这一步，最后的simsun最好不要添加引号，看有一些例子写了引号，导致后面声明字体使用不上。

  5、在HTML中使用我们安装的字体,你可以在这个HTML任何地方写这个字体样式，不过为了全文显示正常最好还是在这写(也可以卸载style标签内)。
	<body style="font-family:simsun">中文字体</body>

# 中文换行

vendor\dompdf\dompdf\src\FrameReflower\Text.php中

    $words = preg_split('/([\s-]+)/u', $text, -1, PREG_SPLIT_DELIM_CAPTURE);
    $wc = count($words);
    改成
    preg_match_all("/./u", $text, $array);
    $words = $array[0];
    $wc = count($words);
