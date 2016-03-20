---
layout: post
title: 广播机制初步
category: Android
tags: [android,androidfragment,fragment]
keywords:
description:
---

# 分类

标准广播(Normal broadcasts)是一种完全异步执行的广播，在广播发出后，所有的广播接收器都在同一时刻受到这条广播消息，没有先后顺序。效率高，无法被截断。

有序广播(Ordered broadcasts)是一种同步执行的广播，同一时刻，只有一个广播接收器能受到这条广播消息，当这个广播接收器中的逻辑执行完毕后，广播才会继续传递。
有先后顺序，优先级高的会先收到广播消息，并且前面的广播接收器可以截断正在传递的广播。

接受广播：广播接收器(Broadcast Receiver)

# 系统广播


# 注册广播

动态注册的广播接收器一定要取消注册，一般是在**onDestroy()**方法中通过调用**unregisterReceiver()**方法来实现的。

##　动态注册

```java
public class MainActivity extends AppCompatActivity {

    private IntentFilter mIntentFilter;
    // Whether there is a Wi-Fi connection.
    private static boolean wifiConnected = false;
    // Whether there is a mobile connection.
    private static boolean mobileConnected = false;

    private TextView mWifiTextView;
    private TextView mMobileTextView;

    private NetworkChangeReceiver mNetworkChangeReceiver;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        mWifiTextView=(TextView)findViewById(R.id.wifi);
        mMobileTextView=(TextView)findViewById(R.id.mobile_network);
        /*
        注册广播接收器
        当网络发生变化时，系统发出的是一条值为"android.net.conn.CONNECTIVITY_CHANGE"的广播消息
         */
        mIntentFilter=new IntentFilter();
        mIntentFilter.addAction(ConnectivityManager.CONNECTIVITY_ACTION);
        mNetworkChangeReceiver=new NetworkChangeReceiver();
        registerReceiver(mNetworkChangeReceiver,mIntentFilter);

    }


    //注册的广播接收都需要解除注册
    @Override
    protected void onDestroy() {
        super.onDestroy();
        unregisterReceiver(mNetworkChangeReceiver);
    }

    class NetworkChangeReceiver extends BroadcastReceiver{

        @Override
        public void onReceive(Context context, Intent intent) {
//            Toast.makeText(context,"network change",Toast.LENGTH_SHORT).show();
            ConnectivityManager connMgr =
                    (ConnectivityManager) getSystemService(Context.CONNECTIVITY_SERVICE);
            NetworkInfo activeInfo = connMgr.getActiveNetworkInfo();

            if (activeInfo != null && activeInfo.isConnected()) {
                wifiConnected = activeInfo.getType() == ConnectivityManager.TYPE_WIFI;
                mobileConnected = activeInfo.getType() == ConnectivityManager.TYPE_MOBILE;
                if(wifiConnected) {
//                    Toast.makeText(context,"wifi is connected",Toast.LENGTH_LONG).show();
                    mWifiTextView.setText("Wifi is connected");
                    mMobileTextView.setText("mobile network is not connected");
                } else if (mobileConnected) {
//                    Toast.makeText(context,"mobile network is connected",Toast.LENGTH_LONG).show();
                    mWifiTextView.setText("Wifi is not connected");
                    mMobileTextView.setText("mobile network is connected");
                }
            } else {
//                Toast.makeText(context,"no network",Toast.LENGTH_LONG).show();
                mWifiTextView.setText("Wifi is not connected");
                mMobileTextView.setText("mobile network is not connected");
            }
        }
    }
}
```

另外还需在增加以下两个权限，否则会在打开的时候崩溃。

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

### 效果

![](assets/img/posts/broadcast_network_connectivity.gif)


## 静态注册

```java
public class BootCompleteReceiver extends BroadcastReceiver{

    @Override
    public void onReceive(Context context, Intent intent) {
        Toast.makeText(context,"Boot Complete",Toast.LENGTH_LONG).show();
    }
}
```

在AndroidManifest.xml中需要添加下列语句：

```xml
<user-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED"/>
......
<application
	...>
	.....
    
    <receiver android:name=".BootCompleteReceiver">
        <intent-filter>
            <action android:name="android.intent.action.BOOT_COMPLETED"/>
        </intent-filter>
    </receiver>
    
</application>
```

afas$$$aaa$$$afas
$$aa$$