# 2016-10-18工作日志
===================

* 应完成工作

  点击控件事件布局
  
  public class MainActivity extends Activity {

    //public class MainActivity extends Activity implements View.OnClickListener{
    
   private Button mybutton_btn = null;

    @Override
    
     protected void onCreate(Bundle savedInstanceState){
     
       super.onCreate(savedInstanceState);
       
      setContentView(R.layout.main_activity);
      
       mybutton_btn = (Button)findViewById(R.id.mybutton_btn);
       
       // mybutton_btn.setOnClickListener(this);
       
       // mybutton_btn.setOnClickListener(new View.OnClickListener() {
       
//            @Override

//            public void onClick(View v) {

//                Toast.makeText(getApplicationContext(),"点击事件一",Toast.LENGTH_LONG).show();
//            }
//        });

//        mybutton_btn.setOnClickListener(listener);
     }


    //  public void onClick(View v){
    
    //     if(v == mybutton_btn){
    
    //Toast.makeText(this,"处处闻啼鸟",Toast.LENGTH_LONG).show();
    // }
    //  }
    public void onClick2(View v) {
    
        Toast.makeText(this, "夜来风雨声", Toast.LENGTH_LONG).show();
        
        //   View.OnClickListener listener = new View.OnClickListener() {
        
        //       @Override
        
        //       public void onClick(View v) {
        
        //          Toast.makeText(getApplicationContext(), "点击事件二", Toast.LENGTH_LONG).show();
        //     }
        //   };
         }
}

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center">
    <Button
        android:id="@+id/mybutton_btn"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="10dp"
        android:onClick="onClick2"
        android:text="春眠不知晓"/>
</LinearLayout>

<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.myapplication44">

    <application android:allowBackup="true" android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name" android:supportsRtl="true"
        android:theme="@style/AppTheme">

        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN"></action>
                <category android:name="android.intent.category.LAUNCHER"></category>
            </intent-filter>
        </activity>
    </application>


</manifest>

* 未完成工作
* 未完成原因
* 工作成功
* 遇到的问题及解决方法
