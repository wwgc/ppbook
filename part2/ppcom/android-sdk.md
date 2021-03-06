# `PPCom Android SDK`

---

#### 下载

[ ![Download](https://api.bintray.com/packages/ppmessage/maven/ppcomsdk/images/download.svg) ](https://bintray.com/ppmessage/maven/ppcomsdk/_latestVersion)


===

你可通过 `Maven` 或者 `Gradle` 下载 `PPCom Android SDK`.

> 0.0.2版本可不是固定的哟

* Maven

```xml
<dependency>
  <groupId>com.ppmessage</groupId>
  <artifactId>ppcomsdk</artifactId>
  <version>0.0.2</version>
  <type>pom</type>
</dependency>
```

* Gradle

```gradle
compile 'com.ppmessage:ppcomsdk:0.0.2'
```

#### 界面

`PPCom Android SDK` 包括三个界面。

1. `对话列表`

  `对话列表`界面显示了所有的对话。点击一个对话会打开这个对话的`对话窗口`界面。

2. `对话窗口`

  `对话窗口` 显示了对话里的消息，`PPCom`用户可以在`对话窗口`下方的输入框里输入文字，然后点击`发送`按钮发送消息。

3. `对话成员`

  在`对话窗口`界面，如果`PPCom`用户点击窗口右上角的 `group` 按钮，会打开`对话成员`界面。`对话成员`界面显示了对话里所有的成员（包括当前`PPCom`用户和对话里的客服）。`PPCom`用户可以通过点击某个客服单独和该客服建立对话。


#### 使用说明

===

1. 初始化

  ```java
  public class App extends Application {
      private static final String PPMESSAGE_APP_UUID = "xxx";
      @Override
      public void onCreate() {
          super.onCreate();
          PPComSDK sdk = PPComSDK.getInstance();
          sdk.init(new PPComSDKConfiguration.Builder()
              .setContext(this)
              .setAppUUID(PPMESSAGE_APP_UUID)
              .setApiKey(PPCOM_API_KEY)
              .setApiSecret(PPCOM_API_SECRET)
              .build());
      }
  }
```

2. 启动`PPCom`

  ```java
  public class MainActivity extends ConversationsActivity {
      @Override
      protected void onCreate(Bundle savedInstanceState) {
          super.onCreate(savedInstanceState);
          startUp();
      }
  }
```

> sdk.update() 可以在startup conversation 之前进行配置更新，更新的数据只能包括 user_fullname, user_icon, ent_user_data, jpush_registration_id，其它数据只能在初始化的时候指定。并且update一定是sdk.init()成功之后才能执行。