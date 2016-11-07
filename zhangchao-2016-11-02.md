# 2016-11-02工作日志
==================
* 应完成工作
public class LogoActivity extends Activity {

    private ImageView img_logo = null;
    private Animation animation = null;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_logo);
        //初始控件级动画
        img_logo = (ImageView)findViewById(R.id.iv_logo);
        animation = AnimationUtils.loadAnimation(this,R.anim.anim_logo);
    }

    private Animation.AnimationListener animationListener = new Animation.AnimationListener(){
        //动画开始
        @Override
        public void onAnimationStart(Animation animation) {

        }
        //动画重复
        @Override
        public void onAnimationRepeat(Animation animation){

        }
        //动画结束
        @Override
        public void onAnimationEnd(Animation animation){
            Intent intent = new Intent(LogoActivity.this,TelmsgActivity.class);
            startActivity(intent);
            finish();

        }

    };
}

* 已完成工作
* 未完成工作
* 未完成原因
