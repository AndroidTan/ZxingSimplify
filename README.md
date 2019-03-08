# ZxingSimplify

    一个精简的安卓Zxing扫码库。（A Zxing simplify library for Android）

    去除了ViewfinderView，使用XML布局。

![ZxingSimplify](https://github.com/shenyuanqing/ZxingSimplify/blob/master/images/zxingscan.png)
![ZxingSimplify](https://github.com/shenyuanqing/ZxingSimplify/blob/master/images/zxingsimplify.png)

Gradle
------
```
dependencies {
    compile 'com.github.shenyuanqing.zxing:zxing-simplify:1.0.5'
}
```

Usage
-----

* **1** 讲代码中 zxing-simplify 目录作为module导入到AndroidStudio，并让应用依赖这个module即可。
* **1** 具体调用方法参考MainActivity，只需申请相机使用权限，并启动CaptureActivity即可进行扫描。
        动态权限申请的简单模板代码可参考 https://blog.csdn.net/tctaccount/article/details/84892228 

```
    /**
     * 跳转到扫码页
     */
    private void jumpScanPage() {
        startActivityForResult(new Intent(MainActivity.this, CaptureActivity.class),REQUEST_SCAN);
    }

    @Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);
        if(requestCode == REQUEST_SCAN && resultCode == RESULT_OK) {
            Toast.makeText(mContext,data.getStringExtra(CaptureActivity.SCAN_RESULT),Toast.LENGTH_LONG).show();
        }
    }
```

Changelog
-----
* **1.0.5.1**
    * 并未在maven上发版本，只是进行了代码小改。
    * 扫描结果传递时的 key 改为常量代替，避免硬编码，降低module使用是的犯错率。

* **1.0.5**
    * 增加从相册选取二维码识别功能
    * 增加开关闪光灯功能

* **1.0.4**
    * 增加扫描二维码、条码等功能
