# 2016-11-29 工作日志
===================
* 应完成工作
* 已完成工作

public class FragmentMenu extends Fragment {
    private View view;
    private RelativeLayout[] rls = new RelativeLayout[5];


    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
        //利用回调中的参数 LayoutInflater对象导入布局文件，并发挥此 View
        view = inflater.inflate(R.layout.fragment_menu_left, container, false);
        rls[0] = (RelativeLayout) view.findViewById(R.id.rl_news);
        rls[1] = (RelativeLayout) view.findViewById(R.id.rl_reading);
        rls[2] = (RelativeLayout) view.findViewById(R.id.rl_local);
        rls[3] = (RelativeLayout) view.findViewById(R.id.rl_commnet);
        rls[4]=(RelativeLayout) view.findViewById(R.id.rl_photo);
        for(int i=0;i<rls.length;i++){
            rls[i].setOnClickListener(onClickListener);
        }



        return view;
    }
    private View.OnClickListener onClickListener=new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            for (int i = 0; i < rls.length; i++) {
                rls[i].setBackgroundColor(0);
            }
            switch (v.getId()) {
                case R.id.rl_news:
                    rls[0].setBackgroundColor(0x33c85555);
                    ((ActivityMain)getActivity()).showFragmentMain();
                    break;
                case R.id.rl_reading:
                    rls[1].setBackgroundColor(0x33c85555);
                    ((ActivityMain)getActivity()).showFragmentFavorite();
                    break;
                case R.id.rl_local:
                    rls[2].setBackgroundColor(0x33c85555);
                    Toast.makeText(getActivity(), "Local", Toast.LENGTH_SHORT).show();
                    break;
                case R.id.rl_commnet:
                    rls[3].setBackgroundColor(0x33c85555);
                    Toast.makeText(getActivity(), "Commnet", Toast.LENGTH_SHORT).show();
                    break;
                case R.id.rl_photo:
                    rls[4].setBackgroundColor(0x33c85555);
                    Toast.makeText(getActivity(), "Photo", Toast.LENGTH_SHORT).show();
                    break;
            }
        }
    };
}
* 未完成工作
* 未完成原因
