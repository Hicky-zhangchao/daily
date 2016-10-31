# 2016-10-24工作日报
==========================

*应完成工作
public class MainActivity extends AppCompatActivity {

    private ListView listView1;
    private List<Map<String,String>> list;

    @Override
    protected void onCreate(@Nullable Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main_layout);

        listView1 = (ListView) findViewById(R.id.listView1);
            list = getData();

        //绑定适配器
        listView1.setAdapter(baseAdapter);
        //监听事件
        listView1.setOnItemClickListener(oicl);
    }
    private AdapterView.OnItemClickListener oicl = new AdapterView.OnItemClickListener() {
        @Override
        public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
            Toast.makeText(MainActivity.this,"position="+position+",id="+id,Toast.LENGTH_LONG).show();
        }
    };
    private List<Map<String,String>>getData(){
        List<Map<String,String>>tmp = new ArrayList<Map<String,String>>();
        for (int i =0;i<20;i++){
           Map<String,String>map = new HashMap<String,String>();
            map.put("id",i+"");
            map.put("createData","2016-10-"+i);
            map.put("name","2016-10-"+i+"日报");
            tmp.add(map);
        }
        return tmp;
    }
    private BaseAdapter baseAdapter =new BaseAdapter() {
        //定义数据的个数
        @Override
        public int getCount() {
            return list.size();
        }
        //定义每行数据的对象
        @Override
        public Map<String,String>getItem(int position) {
            return list.get(position);
        }
        //定义每行的id值
        @Override
        public long getItemId(int position) {
            return position;
        }
        //定义每行都是什么样的布局，如何展示数据
        @Override
        public View getView(int position, View convertView, ViewGroup parent) {
            Map<String,String> tmpMap = getItem(position);
            String id = tmpMap.get("id");
            String createData = tmpMap.get("createData");
            String name = tmpMap.get("name");
            View view = getLayoutInflater().inflate(R.layout.main_item_layout,null);
            TextView tvId = (TextView)view.findViewById(R.id.tvId);
            TextView tvName = (TextView)view.findViewById(R.id.tvName);
            TextView tvData = (TextView)view.findViewById(R.id.tvData);
            tvId.setText(id);
            tvData.setText(createData);
            tvName.setText(name);
            return view;
        }
    };
}

*未完成工作
*未完成原因
*工作成功
