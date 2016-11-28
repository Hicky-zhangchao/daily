# 2016-11-22 工作日志
====================
* 应完成工作
* 已完成工作

public class MainActivity extends AppCompatActivity {

    private Button btnMain;
    private Button btnFrag;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        btnMain = (Button) findViewById(R.id.btn_main);

        BtnListener bl = new BtnListener(this,"男神");
        btnMain.setOnClickListener(bl);
        //btnMain.performClick();




    }


}

public class BtnListener implements View.OnClickListener {

    private FragmentActivity context;
    private String strContext;

    public BtnListener(FragmentActivity context,String strContext) {
        this.context = context;
        this.strContext = strContext;
    }

    @Override
    public void onClick(View v) {

        switch (v.getId()) {
            case R.id.btn_main:

                BtnFragment bf = new BtnFragment();
                FragmentManager fm = context.getFragmentManager();
                FragmentTransaction ft = fm.beginTransaction();
                Bundle bd = new Bundle();
                bd.putString("txt",strContext);
                bf.setArguments(bd);
                ft.add(R.id.ly_main, bf);

                ft.commit();

                break;
            case R.id.btn_frg:

                rtnData(rtnInf);
                break;
            default:

                Toast.makeText(context, "", Toast.LENGTH_LONG).show();
                break;
        }
    }

    public void rtnData(IResult result) {
        result.getData(strContext);
    }

    public interface IResult{
        public void getData(String value);
    }

    private BtnListener.IResult rtnInf = new BtnListener.IResult() {
        @Override
        public void getData(String value) {
            Log.d("value",value);
            Button btn = (Button) context.findViewById(R.id.btn_main);
            btn.setText(value);
        }
    };
}

* 未完成工作
* 未完成原因
