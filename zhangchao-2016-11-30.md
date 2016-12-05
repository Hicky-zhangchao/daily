# 2016-11-30 工作日志
===================
* 应完成工作
* 已完成工作

public class FragmentMenuRight extends Fragment {


        private View view;
        private RelativeLayout relativelayout_unlogin;
        private RelativeLayout relativeLayout_logined;
        private boolean islogin;
        private SharedPreferences sharedPreferences;
        private ImageView imageView1, iv_pic;
        private TextView textView1, updateTv;
        private String[] str;
      //  DownloadCompleteReceiver receiver;
        private ImageView iv_friend;
        private ImageView iv_qq;
        private ImageView iv_friends;
        private ImageView iv_weibo;

        public static final int WEBCHAT = 1, QQ = 2, WEBCHATMOMENTS = 3, SINA = 4;

        @Override
        public View onCreateView(LayoutInflater inflater, ViewGroup container,
                                 Bundle savedInstanceState) {
            view = inflater.inflate(R.layout.fragment_menu_right, container, false);
            sharedPreferences = getActivity().getSharedPreferences("userinfo",
                    Context.MODE_PRIVATE);
            islogin = sharedPreferences.getBoolean("islogin", false);
            relativelayout_unlogin = (RelativeLayout) view
                    .findViewById(R.id.relativelayout_unlogin);
            relativeLayout_logined = (RelativeLayout) view
                    .findViewById(R.id.relativelayout_logined);
            imageView1 = (ImageView) view.findViewById(R.id.imageView1);
            textView1 = (TextView) view.findViewById(R.id.textView1);
            updateTv = (TextView) view.findViewById(R.id.update_version);
            // 初始化分享功能控件
            iv_friend = (ImageView) view.findViewById(R.id.fun_friend);
            iv_qq = (ImageView) view.findViewById(R.id.fun_qq);
            iv_friends = (ImageView) view.findViewById(R.id.fun_friends);
            iv_weibo = (ImageView) view.findViewById(R.id.fun_weibo);

            iv_friend.setOnClickListener(l);
            iv_qq.setOnClickListener(l);
            iv_friends.setOnClickListener(l);
            iv_weibo.setOnClickListener(l);

            imageView1.setOnClickListener(l);
            textView1.setOnClickListener(l);
            return view;
        }
        private View.OnClickListener l = new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // 判断登陆
                if (v.getId() == R.id.imageView1 || v.getId() == R.id.textView1) {
                    ((ActivityMain) getActivity()).showFragmentLogin();
                }
            }
        };
        /**根据用户信息是否存在本地来设置当前视图**/
        public void changeView() {
            islogin = sharedPreferences.getBoolean("islogin", false);
            if (islogin) {
                relativeLayout_logined.setVisibility(View.VISIBLE);
                relativelayout_unlogin.setVisibility(View.GONE);
                initUserInfo();
            } else {
                relativelayout_unlogin.setVisibility(View.VISIBLE);
                relativeLayout_logined.setVisibility(View.GONE);
            }
        }

        /** 初始化用户信息**/
        private void initUserInfo() {
            TextView tv_name = (TextView) view.findViewById(R.id.textView_name);
            iv_pic = (ImageView) view.findViewById(R.id.imageView_photo);
            tv_name.setText(str[0]);



//        String iconPath = SharedPreferencesUtils
//                .getUserLocalIcon(getActivity());
//        if (!TextUtils.isEmpty(iconPath)) {
//            LogUtil.d(LogUtil.TAG, "menu right 本地存在用户主动上传的头像");
//            Bitmap bitmap = BitmapFactory.decodeFile(iconPath);
//            iv_pic.setImageBitmap(bitmap);
//            return;
//        }



            if (!TextUtils.isEmpty(str[1])) {
                LogUtil.d(LogUtil.TAG, "menu right 本地存在用户主动上传的头像");




//            LoadImage loadImage = new LoadImage(getActivity(), this);
//            loadImage.geBitmap(str[1],iv_pic);
//    		iv_pic.setImageBitmap(loadImage.geBitmap(str[1]));
            }
        }

    }
* 未完成工作
* 未完成原因
