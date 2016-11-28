# 2016-11-23 工作日志
====================
* 应完成工作
* 已完成工作

public class MianActivity1 extends Activity{

    private List<Map<String,Object>> data=null;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main_activity);
        //加载数据
        initDate();
        GridView gview= (GridView)findViewById(R.id.gview);
        //获取适配器对象
        SimpleAdapter adapter=new SimpleAdapter(this, data,R.layout.layout_imgs, new String[]{"image","imageName"}, new int[]{R.id.image,R.id.text});
        //gview绑定adapter
        gview.setAdapter(adapter);
    }

    //加载数据
    public void initDate(){
        int[] ico=new int[]{
                R.drawable.icon_1, R.drawable.icon_1, R.drawable.icon_1,
                R.drawable.icon_1, R.drawable.icon_1, R.drawable.icon_1,
                R.drawable.icon_1, R.drawable.icon_1, R.drawable.icon_1,
        };

        String[] icoName=new String[]{
                "通讯录", "日历", "照相机",
                "时钟", "游戏", "短信",
                "铃声", "设置", "语音",
        };

        //把数据放到键值对中
        data=new ArrayList<Map<String,Object>>();
        for(int i=0;i<ico.length;i++){
            Map<String,Object> map=new HashMap<String,Object>();
            map.put("image",ico[i]);
            map.put("imageName", icoName[i]);
            data.add(map);
        }
    }
}

<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#000">

    <GridView
        android:id="@+id/gview"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:numColumns="3"
        android:columnWidth="80dp"
        android:stretchMode="columnWidth">
    </GridView>
</LinearLayout>

<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:padding="10dp">

    <ImageView
        android:src="@drawable/icon_1"
        android:id="@+id/image"
        android:layout_width="60dp"
        android:layout_height="60dp"

        />

    <TextView
        android:id="@+id/text"
        android:layout_marginTop="5dp"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textColor="#ffffff"
        android:text="文字"
        />
</LinearLayout>

* 未完成工作
* 未完成原因
