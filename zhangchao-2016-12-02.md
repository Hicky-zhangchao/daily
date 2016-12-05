# 2016-11-30 工作日志
===================
* 应完成工作
* 已完成工作

public class ActivityLead extends MyBaseActivity {

    private ImageView[] points = new ImageView[4];
    private LeadImgAdapter adapter;
    private ViewPager viewPager;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_lead);
        viewPager = (ViewPager)findViewById(R.id.Viewpager);
        //设置每一个具体界面的样式
        List<View>viewList = new ArrayList<View>();
        viewList.add(getLayoutInflater().inflate(R.layout.lead_1,null));
        viewList.add(getLayoutInflater().inflate(R.layout.lead_2,null));
        viewList.add(getLayoutInflater().inflate(R.layout.lead_3,null));
        viewList.add(getLayoutInflater().inflate(R.layout.lead_4,null));
        points[0] = (ImageView)findViewById(R.id.iv_p1);
        points[1] = (ImageView)findViewById(R.id.iv_p2);
        points[2] = (ImageView)findViewById(R.id.iv_p3);
        points[3] = (ImageView)findViewById(R.id.iv_p4);
        setPoint(0);
        //初始化控件
        viewPager = (ViewPager)findViewById(R.id.Viewpager);
        //初始化适配器
        adapter = new LeadImgAdapter(viewList);
        //设置适配器
        viewPager.setAdapter(adapter);
        viewPager.setOnPageChangeListener(listener);
    }
    private void setPoint(int index){
        for (int i = 0; i<points.length;i++){
            if (i==index){
                points[i].setAlpha(255);
            }
            else {
                points[i].setAlpha(100);
            }
        }
    }
    /**当界面切换后调用*/
    private ViewPager.OnPageChangeListener listener = new ViewPager.OnPageChangeListener() {

        /**当界面切换后调用*/
        @Override
        public void onPageScrolled(int arg0, float arg1, int arg2) {

        }

        @Override
        public void onPageSelected(int arg0) {
            setPoint(arg0);
            if (arg0>=3){
                openActivity(ActivityLogo.class);
                finish();
                SharedPreferences preferences = getSharedPreferences("runconfig",MODE_PRIVATE);
                SharedPreferences.Editor editor = preferences.edit();
                editor.putBoolean("isFirstRun",false);
                editor.commit();
            }
        }
       /**滑动状态变化时调用*/
        @Override
        public void onPageScrollStateChanged(int arg0) {

        }
    };
}
* 未完成工作
* 未完成原因
