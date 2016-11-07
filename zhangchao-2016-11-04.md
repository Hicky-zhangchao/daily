# 2016-11-04工作日志
* 应完成工作
public class LeadActivity extends BaseActivity  implements View.OnClickListener {

    @Override
    public void onClick(View v) {

    }

    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.leadactivity);
        Intent intent = getIntent();
        String fromClassName = intent.getStringExtra("className");
        if (fromClassName != null &&
                fromClassName.equals("SettingActivity")) {
            isFromSetting = true;
        }
        SharedPreferences preferences =
                getSharedPreferences("lead_config", Context.MODE_PRIVATE);
        boolean isFirstRun = preferences.getBoolean("isFirstRun", true);
        if (!isFirstRun) {
            startActivity(LogoActivity.class);
            finish();
        }
// 从当前引导页面开始执行
        else {
            setContentView(R.layout.leadactivity);
// 初始化引导页面小图标+skip (5 个小图标 + 1 个 skip 文字)
            initLeadIcon();
// 初始化引导页面 ViewPager 视图 (给 ViewPager 设置 Adapter)
            initViewPager();
// 初始化引导页面 ViewPager 内显示的视图数据 (向 ViewPager 的Adapter 内添加视图(图片))
            initPagerData();
        }finish();
    }


    private void initLeadIcon() {
        ImageView[] icons = new ImageView[0];
        icons[0] = (ImageView) findViewById(R.id.icon1);
        icons[1] = (ImageView) findViewById(R.id.icon2);
        icons[2] = (ImageView) findViewById(R.id.icon3);
        icons[0].setImageResource(R.drawable.adware_style_selected);
        TextView tv_skip = (TextView) findViewById(R.id.tv_skip);
        tv_skip.setVisibility(View.INVISIBLE);
        tv_skip.setOnClickListener(this);
    }
    private void initViewPager() {
        ViewPager viewPager = (ViewPager) findViewById(R.id.viewpager);
        BasePagerAdapter leadPagerAdapter = new BasePagerAdapter(this);
        viewPager.setAdapter(leadPagerAdapter);
        ViewPager.OnPageChangeListener pageChangeListener = new ViewPager.OnPageChangeListener() {
            @Override
            public void onPageScrolled(int position, float positionOffset, int positionOffsetPixels) {

            }

            @Override
            public void onPageSelected(int position) {

            }

            @Override
            public void onPageScrollStateChanged(int state) {

            }
        };
        viewPager.setOnPageChangeListener(pageChangeListener);
    }
    private void initPagerData() {
        ImageView imageView = null;
        imageView = (ImageView)
                getLayoutInflater().inflate(R.layout.activity_lead_item, null);
        imageView.setImageResource(R.drawable.adware_style_applist);
        BasePagerAdapter leadPagerAdapter = null;
        leadPagerAdapter.addViewToAdapter(imageView);
        imageView = (ImageView)
                getLayoutInflater().inflate(R.layout.activity_lead_item, null);
        imageView.setImageResource(R.drawable.adware_style_banner);
        leadPagerAdapter.addViewToAdapter(imageView);
        imageView = (ImageView)
                getLayoutInflater().inflate(R.layout.activity_lead_item, null);
        imageView.setImageResource(R.drawable.adware_style_creditswall);
        leadPagerAdapter.addViewToAdapter(imageView);
        leadPagerAdapter.notifyDataSetChanged();
    }
    private ViewPager.OnPageChangeListener pageChangeListener = new
            ViewPager.OnPageChangeListener() {
                @Override
                public void onPageSelected(int arg0) {
// 到达最后一个 page 时，显示出 skip 文本
                    tv_skip.setVisibility(View.INVISIBLE);
                    if (arg0 >= 2) {
                        tv_skip.setVisibility(View.VISIBLE);
                    }
// 更新下标图标
                    ImageView[] icons = new ImageView[0];
                    for (int i = 0; i < icons.length; i++) {
                        icons[i].setImageResource(R.drawable.adware_style_default);
                    }
                    icons[arg0].setImageResource(R.drawable.adware_style_selected);
                }
                @Override
                public void onPageScrolled(int arg0, float arg1, int arg2) {
                }
                @Override
                public void onPageScrollStateChanged(int arg0) {
                }
            };

    private boolean isFromSetting;

    private void savePreferences() {
        SharedPreferences preferences =
                getSharedPreferences("lead_config", Context.MODE_PRIVATE);
        SharedPreferences.Editor editor = preferences.edit();
        editor.putBoolean("isFirstRun", false);
        editor.commit();
    }



}
public class timerTask extends Activity{ 
  private int recLen = 11; 
  private TextView txtView; 
  Timer timer = new Timer(); 
  public void onCreate(Bundle savedInstanceState){ 
    super.onCreate(savedInstanceState); 
    setContentView(R.layout.timertask); 
    txtView = (TextView)findViewById(R.id.txttime); 
    timer.schedule(task, 1000, 1000);    // timeTask 
  }   
  TimerTask task = new TimerTask() { 
    @Override
    public void run() { 
      runOnUiThread(new Runnable() {   // UI thread 
        @Override
        public void run() { 
          recLen--; 
          txtView.setText(""+recLen); 
          if(recLen < 0){ 
            timer.cancel(); 
            txtView.setVisibility(View.GONE); 
          } 
        } 
      }); 
    } 
  }; 
}
* 已完成工作
* 未完成工作
* 未完成原因
