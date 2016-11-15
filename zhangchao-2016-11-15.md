# 2016-11-15工作日志
=================
* 应完成工作
public class  ListBitMapActvityo extends AppCompatActivity {

    private List<Integer> listData =null;


    private ListView lv1;

    private BaseAdapter ba = new BaseAdapter() {
        @Override
        public int getCount() {
            return listData.size();
        }

        @Override
        public Integer getItem(int position) {
            return listData.get(position);
        }

        @Override
        public long getItemId(int position) {
            return position;
        }

        @Override
        public View getView(int position, View convertView, ViewGroup parent) {

            LayoutInflater lif = (LayoutInflater) getSystemService(Context.LAYOUT_INFLATER_SERVICE);
            convertView = lif.inflate(R.layout.bitmap_item_layout,null);
            ImageView iv1 = (ImageView) convertView.findViewById(R.id.iv1);
            iv1.setImageResource(getItem(position));
            return convertView;
        }
    };

    @Override
    protected void onCreate(@Nullable Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.bitmap_layout);

        lv1 = (ListView) findViewById(R.id.lv_1);

        listData = getData();
        lv1.setAdapter(ba);
    }

    private List<Integer> getData() {

        List<Integer> result = new ArrayList<>();
        result.add(R.drawable.img_0094);
        result.add(R.drawable.img_0095);
        result.add(R.drawable.img_0096);
        result.add(R.drawable.img_0097);
        result.add(R.drawable.img_0098);
        result.add(R.drawable.img_0099);
        result.add(R.drawable.img_0100);
        result.add(R.drawable.img_0101);
        result.add(R.drawable.img_0102);
        result.add(R.drawable.img_0103);
        result.add(R.drawable.img_0104);

        return result;
    }

}
* 已完成工作
* 未完成工作
* 未完成原因
