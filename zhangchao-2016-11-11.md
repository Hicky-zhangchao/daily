#2016-11-11工作日志
* 应完成工作
public class MemoryManager {

    public static long getPhoneTotalRamMemory(){
        try {
            FileReader fr = new FileReader("/proc/meminfo");
            BufferedReader br = new BufferedReader(fr);
            String text = br.readLine();
            String[] array = text.split("\\s+");
            return Long.valueOf(array[1]) * 1024; // 原为kb, 转为b
        }
        catch (FileNotFoundException e){
            e.printStackTrace();
        }
        catch (IOException e){
            e.printStackTrace();
        }
        return 0;
    }
    public static long getPhoneFreeRamMemory(Context context){
        ActivityManager.MemoryInfo info = new ActivityManager.MemoryInfo();
        ActivityManager am = (ActivityManager) context.getSystemService(Context.ACTIVITY_SERVICE);
        am.getMemoryInfo(info);
        return info.availMem;
    }
}

public class MySoftRef extends SoftReference<Bitmap> {

    private Integer _key = 0;


    public MySoftRef(Bitmap bmp, ReferenceQueue<Bitmap> q, int key) {
        super(bmp,q);
        _key = key;
    }

}
* 已完成工作
* 未完成工作
* 未完成原因
