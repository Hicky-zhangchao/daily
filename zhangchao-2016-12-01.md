# 2016-12-01 工作日志
===================
* 应完成工作
* 已完成工作

public class ActivityMain extends MyBaseActivity {
    /**主界面*/
    private android.support.v4.app.Fragment fragmentType; private android.support.v4.app.Fragment fragmentMain; private android.support.v4.app.Fragment fragmentLogin; private android.support.v4.app.Fragment fragmentRegister; private android.support.v4.app.Fragment fragmentFavorite; private android.support.v4.app.Fragment fragmentForgetPass;
    public static SlidingMenu slidingMenu;
    private ImageView iv_set, iv_user;
    private TextView textView_title;
    private android.support.v4.app.Fragment fragmentMenu;
    private android.support.v4.app.Fragment fragmentMenuRight;
    private android.support.v4.app.FragmentManager supportFragmentManager;


    @Override
    protected void onCreate(Bundle arg0) {
        super.onCreate(arg0);
        setContentView(R.layout.activity_main);
        textView_title=(TextView) findViewById(R.id.textView1);
        iv_set = (ImageView) findViewById(R.id.imageView_set);
        iv_user = (ImageView) findViewById(R.id.imageView_user);
        iv_set.setOnClickListener(onClickListener);
        iv_user.setOnClickListener(onClickListener);
        initSlidingMenu();
//        showFragmentMain();
    }
    private View.OnClickListener onClickListener = new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            switch (v.getId()) {
                case R.id.imageView_set:
                    if (slidingMenu != null && slidingMenu.isMenuShowing()) {
                        slidingMenu.showContent();
                    } else if (slidingMenu != null) {
                        slidingMenu.showMenu();
                    }
                    break;
                case R.id.imageView_user:
                    if (slidingMenu != null && slidingMenu.isMenuShowing()) {
                        slidingMenu.showContent();
                    } else if (slidingMenu != null) {
                        slidingMenu.showSecondaryMenu();
                    }
                    break;
            }
        }
    };
    /**初始化侧滑菜单**/
    public void initSlidingMenu() {
        fragmentMenu = new android.support.v4.app.Fragment();
        fragmentMenuRight = new android.support.v4.app.Fragment();

        slidingMenu = new SlidingMenu(this);
        slidingMenu.setMode(SlidingMenu.LEFT_RIGHT);
        slidingMenu.setTouchModeAbove(SlidingMenu.TOUCHMODE_FULLSCREEN);
        slidingMenu.setBehindOffsetRes(R.dimen.slidingmenu_offset);
        slidingMenu.attachToActivity(this, SlidingMenu.SLIDING_CONTENT);

//为左侧滑菜单设置布局
        slidingMenu.setMenu(R.layout.fragment_menu_left);
        //为右侧滑菜单设置布局
        slidingMenu.setSecondaryMenu(R.layout.fragment_menu_right);


/*
        getSupportFragmentManager().beginTransaction()
                .replace(R.id.layout_menu, fragmentMenu).commit();
        getSupportFragmentManager().beginTransaction()
                .replace(R.id.layout_menu_right, fragmentMenuRight).commit();
        */


    }

    @Override
    public void onBackPressed() {
        if (slidingMenu.isMenuShowing()) {
            slidingMenu.showContent();
        } else {
            exitTwice();
        }
    }

    //两次退出
    private boolean isFirstExit=true;
    private void exitTwice(){
        if(isFirstExit){
            Toast.makeText(this, "再按一次退出！", Toast.LENGTH_SHORT).show();
            isFirstExit=false;
            new Thread(){
                public void run() {
                    try {
                        Thread.sleep(3000);
                        isFirstExit=true;
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                };
            }.start();
        }else{
            finish();
        }
    }

    /**
     * 显示：“显示新闻更多分类Fragment”
     */
    public void showFragmentType() {
        setTitle("分类");
        slidingMenu.showContent();
        if (fragmentType == null)
            fragmentType = new FragmentType();
        getSupportFragmentManager().beginTransaction()
                .replace(R.id.layout_content, fragmentType).commit();
    }
    /**
     * 显示:“显示新闻列表的Fragment”
     */
    public void showFragmentMain() {
        setTitle("资讯");
        slidingMenu.showContent();
        if (fragmentMain == null)
            fragmentMain = new android.support.v4.app.Fragment();
        getSupportFragmentManager().beginTransaction(). replace(R.id.layout_content, fragmentMain).commit();
    }
    /**
     * 显示:“登录的Fragment”
     */
    public void showFragmentLogin() {
        setTitle("用户登录");
        slidingMenu.showContent();
        if (fragmentLogin == null)
            fragmentLogin = new android.support.v4.app.Fragment();
        getSupportFragmentManager().beginTransaction().replace(R.id.fragment_login, fragmentLogin).commit();
    }

    /**
     * 显示:“注册的Fragment”
     */
    public void showFragmentRegister() {
        setTitle("用户注册");
        if (fragmentRegister == null)
            fragmentRegister = new FragmentRegister();
        getSupportFragmentManager().beginTransaction()
                .replace(R.id.fragment_reg, fragmentRegister).commit();
    }

    /**
     * 显示:“忘记密码的Fragment”
     */
    public void showFragmentForgetPass() {
        setTitle("忘记密码");
        if (fragmentForgetPass == null)
            fragmentForgetPass = new FragmentForgetPass();
        getSupportFragmentManager().beginTransaction();
    }
    /**
     * 显示:“显示收藏新闻列表的Fragment”
     */
    public void showFragmentFavorite() {
        setTitle("收藏新闻");
        slidingMenu.showContent();
        if(fragmentFavorite==null)
            fragmentFavorite=new FragmentFavorite();
        getSupportFragmentManager().beginTransaction()
                .replace(R.id.layout_content, fragmentFavorite).commit();
    }

    /**
     * 更换当前界面的Title
     */
    private void setTitle(String title){
        textView_title.setText(title);
    }

    @Override
    public boolean onTouchEvent(MotionEvent event) {
        System.out.println("ActivityMain");
        return false;
    }


    public android.support.v4.app.FragmentManager getSupportFragmentManager() {
        return supportFragmentManager;
    }

    public void setSupportFragmentManager(android.support.v4.app.FragmentManager supportFragmentManager) {
        this.supportFragmentManager = supportFragmentManager;
    }
}
* 未完成工作
* 未完成原因
