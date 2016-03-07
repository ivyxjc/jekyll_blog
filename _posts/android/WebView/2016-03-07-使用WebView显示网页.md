---
layout: post
title: 使用WebView显示网页
category: Android
tags: [android,androidwebview,keylogic]
keywords:
description:
---

## 访问权限

调用第三方或者系统默认浏览器不需要使用网络访问权限，但是自己写WebView访问网络资源需要配置网络访问权限。

```xml
<uses-permission android:name="android.permission.INTERNET"/>
```


## 使用loadUrl()

web资源： webView.loadUrl("http://www.bing.com");

本地文件：webView.loadUrl("file:///android_assets/xx.html");

本地文件放在 asset文件夹中

//使页面获得焦点
webView.requestFocus();

##　处理页面导航

当用户点击webView中的链接时，通常由默认浏览器打开并加载目标url，需要覆盖该默认处理方法。

```java
webView.setWebViewClient(new WebViewClient(){
            @Override
            public boolean shouldOverrideUrlLoading(WebView view, String url) {
                //返回True的时候控制网页在WebView中打开
                //返回False控制网页在默认浏览器中打开。
                view.loadUrl(url);
                return true;
            }

            //WebViewClient帮助WebView处理一些页面控制和请求通知,还有其它很多方法，如下

            @Override
            public void onPageStarted(WebView view, String url, Bitmap favicon) {
                super.onPageStarted(view, url, favicon);
            }

            @Override
            public void onPageFinished(WebView view, String url) {
                super.onPageFinished(view, url);
            }
        });
```

## WebView使用Javaascript

```java
    WebSettings settings=webView.getSettings();
    settings.setJavaScriptEnabled(true);
```

## 设置返回键逻辑

```java
@Override
public boolean onKeyDown(int keyCode, KeyEvent event) {
    if(keyCode==KeyEvent.KEYCODE_BACK){
        if(webView.canGoBack()){
            Toast.makeText(this,webView.getUrl(),Toast.LENGTH_SHORT).show();
            webView.goBack();//返回上一界面
            return true;
        }
    }else{
        System.exit(0);
    }
    return super.onKeyDown(keyCode, event);
}
```

##判断加载页面过程




