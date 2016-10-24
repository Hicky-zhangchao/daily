# 2016-10-20工作日志
===================

* 应完成工作
    页面跳转并计算

public class MainActivity extends AppCompatActivity {

    private Button btnCal;
    private TextView txtCalResultValue;


    @Override
    protected void onCreate(@Nullable Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main_activity);
        txtCalResultValue=(TextView)findViewById(R.id.btnCal);
        btnCal = (Button) findViewById(R.id.btnCal);
        btnCal.setOnClickListener(ocl);


    }

    private View.OnClickListener ocl = new View.OnClickListener() {

        @Override
        public void onClick(View v) {
            Intent intent = new Intent();
            intent.setClass(MainActivity.this, InputActivity.class);
            startActivityForResult(intent, 99);
        }
    };
    @Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode,resultCode,data);
        int param1 = data.getIntExtra("param1",-1);
        int param2 = data.getIntExtra("param2",-1);

        int result = param1+param2;
        txtCalResultValue.setText(String.valueOf(result));
    }
}

public class InputActivity extends AppCompatActivity{

    private EditText param1;
    private EditText param2;
    private Button btnClose;

    @Override
    protected void onCreate(@Nullable Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.input_layout);

        param1=(EditText)findViewById(R.id.edit_param1);
        param2=(EditText)findViewById(R.id.edit_param2);
        btnClose = (Button)findViewById(R.id.btnClose);
        btnClose.setOnClickListener(ocl);
    }
    private View.OnClickListener ocl = new View.OnClickListener(){
        @Override
        public void onClick(View v){
            String strParam1 = String.valueOf(param1.getText());
            String strParam2 = String.valueOf(param2.getText());

            Intent intent = new Intent();
            intent.putExtra("param1",Integer.valueOf(strParam1));
            intent.putExtra("param2",Integer.valueOf(strParam2));
            setResult(100,intent);

            InputActivity.this.finish();
        }
    };

}

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">

<Button
    android:id="@+id/btnCal"
    android:layout_centerInParent="true"
    android:text="@string/btncal_name"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" />

    <TextView
        android:id="@+id/txtCalResult"
        android:text="@string/txtCal_result_label"
        android:layout_below="@id/btnCal"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />
    <TextView
        android:id="@+id/txtCalResultValue"
        android:layout_toRightOf="@id/txtCalResult"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />
</LinearLayout>

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/txt_param1"
        android:text="@string/param1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />
    <TextView
        android:id="@+id/txt_param2"
        android:text="@string/param2"
        android:layout_below="@id/txt_param1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />
    <EditText
        android:id="@+id/edit_param1"
        android:layout_toRightOf="@id/txt_param1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />
    <EditText
        android:id="@+id/edit_param2"
        android:layout_toRightOf="@id/txt_param2"
        android:layout_alignBottom="@id/edit_param2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <Button
        android:id="@+id/btnClose"
        android:text="@string/btnClose"
        android:layout_below="@id/edit_param1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />
</LinearLayout>

* 未完成工作
* 未完成原因
* 工作成功
* 遇到的问题及解决方法
