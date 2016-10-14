# 2016-10-13工作日志
===================

* 应完成工作
 * 用IntelliJ IDEA Community Edition 连接数据库 查看日报 新增日报 退出
 public class Main {

    public static void main(String[] args) throws SQLException {

        Scanner scanner = new Scanner(System.in);
        UserController userController = new UserController(scanner);

        String filePath = "d:\\1234567\\java_demo\\daily\\src\\main\\resources";

        String fileName = "welcome.txt";

        userController.showSelectItem(filePath, fileName);

        int selected = userController.selectedItem();

        boolean loginResult = false;

        if (1 == selected) {

            // 登录
            loginResult = userController.login();
        }
        else {

            // 注册
            userController.register();
        }

        // 登录成功后的操作
        if (loginResult) {

            fileName = "operate_item.txt";

            userController.showSelectItem(filePath, fileName);

            selected = userController.selectedItem();


        }
        else {

        }

        switch (selected){
            case 1:
                // 查看日报
                DailyController.getDaily();
                break;
            case 2:
                // 新增日报
                DailyController.writeDaily();
                break;
            case 3:
                // 退出
                break;
            default:
                System.out.println("系统错误");
                System.exit(-1);
        }
    }
}
  * 调用getDaily查看日报
   public static void getDaily() {

        String strSql = "select * from  `daily_`";
        List<Map<String,Object>> list = DBUtils.queryTable(strSql);

        for (Map<String,Object> map:list) {
            for (Map.Entry<String,Object> entry : map.entrySet()) {
                String key = entry.getKey();
                Object value = entry.getValue();
                System.out.print(key+":"+value+",");
            }

            System.out.println();
        }
    }
  * 调用writeDaily新增日报
  public class DailyController {



    //新增日报


    public static void writeDaily() throws SQLException {


        UserController uc = new UserController();
        String name = UserController.name;

        Scanner sc = new Scanner(System.in);

        System.out.println("请输入：");

        System.out.println("应完成:");
        String inputSFW = sc.next();
        System.out.println("已完成:");
        String inputHFW = sc.next();
        System.out.println("未完成原因:");
        String inputReason = sc.next();
        System.out.println("问题:");
        String inputQAA = sc.next();
        System.out.println("计划:");
        String inputNDP = sc.next();
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        String date = sdf.format(new Date());
        SimpleDateFormat sdf2 = new SimpleDateFormat("yyyy-MM-dd");
        String date2= sdf2.format(new Date());
        StringBuffer sb = new StringBuffer();
        sb.append(" insert into daily_ (id,name,create_date,should_finished_work,have_finished_work,unfinished_work_reason," +
                "question_and_answer,next_day_plain) values (");
        sb.append(System.currentTimeMillis()+", \"");
        sb.append(name+"-"+ date2 +"  日报\",\" ");
        sb.append(date+" \",\" ");
        sb.append(inputSFW+" \",\" ");
        sb.append(inputHFW+" \",\" ");
        sb.append(inputReason+" \",\" ");
        sb.append(inputQAA+" \",\" ");
        sb.append(inputNDP+"\" ) ");

        System.out.println(sb.toString())
        ;
       DBUtils.modifyTable(sb.toString());
        System.out.println("日报存入");
    }
}

* 未完成工作
* 未完成原因
* 工作成功
