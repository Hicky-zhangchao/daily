# 2016-10-19工作日志
===================

* 应完成工作
class ForthActivity extends AppCompatActivity {

    @TargetApi(value=17)
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

       /* String value = getIntent().getStringExtra("key");
        int intValue= getIntent().getIntExtra("intkey",-1);*/
        Bundle bundle = getIntent().getExtras();

        String value = bundle.getString("key");
        int intValue= bundle.getInt("intKey");


        RelativeLayout rl = new RelativeLayout(this);

        ViewGroup.LayoutParams vp = new ViewGroup.LayoutParams(
                ViewGroup.LayoutParams.MATCH_PARENT,
                ViewGroup.LayoutParams.MATCH_PARENT
        );

        rl.setLayoutParams(vp);
        rl.setBackgroundColor(Color.YELLOW);


        EditText editText = new EditText(this);
        RelativeLayout.LayoutParams editTextParams = new RelativeLayout.LayoutParams(
                RelativeLayout.LayoutParams.MATCH_PARENT,
                RelativeLayout.LayoutParams.WRAP_CONTENT
        );
        editText.setLayoutParams(editTextParams);
        editText.setGravity(Gravity.RIGHT);
        editText.setId(R.id.my_id);
        editText.setText(value+":"+intValue);


        rl.addView(editText);

        RelativeLayout.LayoutParams btnParams7 = new RelativeLayout.LayoutParams(
                RelativeLayout.LayoutParams.WRAP_CONTENT,
                RelativeLayout.LayoutParams.WRAP_CONTENT
        );

        btnParams7.addRule(RelativeLayout.BELOW, editText.getId());

        Button btn7 = new Button(this);
        btn7.setLayoutParams(btnParams7);
        btn7.setId(View.generateViewId());
        btn7.setText("7");

        RelativeLayout.LayoutParams btnParams8 = new RelativeLayout.LayoutParams(
                RelativeLayout.LayoutParams.WRAP_CONTENT,
                RelativeLayout.LayoutParams.WRAP_CONTENT
        );

        btnParams8.addRule(RelativeLayout.RIGHT_OF, btn7.getId());
        btnParams8.addRule(RelativeLayout.ALIGN_TOP,btn7.getId());
        Button btn8 = new Button(this);
        btn8.setLayoutParams(btnParams8);
        btn8.setId(View.generateViewId());
        btn8.setText("8");

        RelativeLayout.LayoutParams btnParams9 = new RelativeLayout.LayoutParams(
                RelativeLayout.LayoutParams.WRAP_CONTENT,
                RelativeLayout.LayoutParams.WRAP_CONTENT
        );
        btnParams9.addRule(RelativeLayout.RIGHT_OF, btn8.getId());

        Button btn9 = new Button(this);
        btn9.setLayoutParams(btnParams9);
        btn9.setId(View.generateViewId());
        btn9.setText("9");

        RelativeLayout.LayoutParams btnParamsMul = new RelativeLayout.LayoutParams(
                RelativeLayout.LayoutParams.WRAP_CONTENT,
                RelativeLayout.LayoutParams.WRAP_CONTENT
        );
        btnParamsMul.addRule(RelativeLayout.RIGHT_OF, btn9.getId());
        Button btnMul = new Button(this);
        btnMul.setLayoutParams(btnParamsMul);
        btnMul.setText("*");

        rl.addView(btn7);
        rl.addView(btn8);
        rl.addView(btn9);
        rl.addView(btnMul);

        setContentView(rl);
    }
}

* 未完成工作
* 未完成原因
* 工作成功
* 遇到的问题及解决方法
