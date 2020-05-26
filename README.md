# phpqrcode base64

输出base64编码的图片字符串，可以直接用于img标签的src中

> [原作者：追逐吾之所求](https://me.csdn.net/jiongxian1)

> [源地址：参考地址](https://blog.csdn.net/jiongxian1/article/details/88980579)

> 1. 在QRcode类中新增方法pngString
> 2. 在QRencode类中新增方法encodePNGString
> 3. 在QRimage类中新增方法pngString
> 4. 引入phpqrcode.php后，调用QRcode类的pngString方法

```php
<?php
require_once 'phpqrcode.php';

public function getQRcode($url){
    ob_start();
    $returnData = QRcode::pngString($url,false, "H", 3, 1);
    $imageString = base64_encode(ob_get_contents());
    ob_end_clean();
    $str = "data:image/png;base64," . $imageString;
    return $str;
}

echo getQRcode('http://example.com');
