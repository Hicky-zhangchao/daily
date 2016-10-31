# 2016-10-26工作日志
* 应完成工作

public class MainActivity extends AppCompatActivity {

    private ListView listClass;

    private List<ClassInfo> listData = null;

    private ViewAdapter va = new ViewAdapter<ClassInfo>() {

        @Override
        public View getView(int position, View convertView, ViewGroup parent) {

            LayoutInflater lif = (LayoutInflater) getSystemService(Context.LAYOUT_INFLATER_SERVICE);

            View view = lif.inflate(R.layout.class_item_layout, null);
            TextView tvName = (TextView) view.findViewById(R.id.tv_class_name);
            tvName.setText(getItem(position).getName());
            return view;
        }
    };

    private AdapterView.OnItemClickListener ocl = new AdapterView.OnItemClickListener() {

        @Override
        public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
            Toast.makeText(MainActivity.this, "你点击的分类的idx是" + listData.get(position).getIdx(), Toast.LENGTH_LONG).show();

            Long idx = listData.get(position).getIdx();

            Intent intent = new Intent();
            intent.putExtra("idx",idx);

            intent.setClass(MainActivity.this,DetailActivity.class);
            startActivity(intent);
        }
    };

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // 获取对象
        listClass = (ListView) findViewById(R.id.list_class);

        // 获取显示数据 ？？？
        listData = getData();

        // 绑定适配器
        va.setListData(listData);

        listClass.setAdapter(va);

        // 设置监听
        listClass.setOnItemClickListener(ocl);
    }

    private List<ClassInfo> getData() {

        SQLiteDabseHandle handle = new SQLiteDabseHandle(this);
        SQLiteDatabase database = handle.getSQLite();

        StringBuilder sbSql = new StringBuilder();
        sbSql.append("  select        ");
        sbSql.append("       idx,name ");
        sbSql.append("  from          ");
        sbSql.append("      classlist ");

        Cursor cursor = database.rawQuery(sbSql.toString(), null);

        List<ClassInfo> result = new ArrayList<ClassInfo>();
        while (cursor.moveToNext()) {
            Long idx = cursor.getLong(0);
            String name = cursor.getString(1);

            ClassInfo classInfo = new ClassInfo(idx, name);
            result.add(classInfo);
        }

        return result;
    }

}

public class ClassInfo {

    private Long idx;
    private String name;
    public ClassInfo(Long idx,String name){
        this.idx = idx;
        this.name = name;
    }
    public Long getIdx(){
        return idx;
    }
    public void setIdx(Long idx){
        this.idx = idx;
    }
    public String getName(){
        return  name;
    }
    public void setName(String name){
        this.name = name;
    }
}

public class SQLiteDabseHandle {
    private Context context;

    public SQLiteDabseHandle(Context context) {
        this.context = context;
    }


    // 把assets/db下的commonnum.db文件复制到/data/data/packagename/db目录下

    // 文件复制
    /*
            1.找到源文件名称，源路径  目标文件名称，目标路径
     */

    private File copyDabaseFile() {

        String res_file_name = "commonnum.db";
        String res_file_path = "db";

        String target_file_name = "num.db";
        String target_file_path = "/data/data/" + context.getPackageName() + "/db";

        File file_target_path = null;
        File file_target_file = null;

        //  读取源路径下，源文件，使用源文件构件字节输入流 InputStream
        //  在目标路径创建目标文件，使用目标文件构件字节输出流 OutputStream
        //  从输入流中读取字节文件写入到输出流中

        try {

            // 判断目标路径是否存在，如果不存在则创建
            file_target_path = new File(target_file_path);

            if (!file_target_path.exists()) {
                file_target_path.mkdirs();
            }

            // 判断目标文件是否存在，如果不存在则创建
            file_target_file = new File(file_target_path, target_file_name);
            if (!file_target_file.exists()) {
                file_target_file.createNewFile();
            }

            AssetManager assetManager = context.getAssets();

            InputStream is = assetManager.open(res_file_path + File.separator + res_file_name);
            OutputStream os = new FileOutputStream(new File(target_file_path, target_file_name));

            int tmp = 0;

            while ((tmp = is.read()) != -1) {
                os.write(tmp);
            }

            os.flush();
            os.close();
            is.close();

        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }

        return file_target_file;
    }


    public SQLiteDatabase getSQLite() {
        SQLiteDatabase database = null;
        File dbFile = copyDabaseFile();

        if (dbFile != null && dbFile.exists()) {
            database = SQLiteDatabase.openOrCreateDatabase(dbFile, null);
        }

        return database;
    }
}

public class TableInfo {
    private Long _id;
    private String number;
    private String name;
    public char[] getNumber;

    public TableInfo(Long _id, String number, String name) {
        this._id = _id;
        this.number = number;
        this.name = name;
    }

    public Long get_id() {
        return _id;
    }

    public void set_id(Long _id) {
        this._id = _id;
    }

    public String getNumber() {
        return number;
    }

    public void setNumber(String number) {
        this.number = number;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
* 未完成工作
* 未完成原因
