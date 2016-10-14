# 2016-10-12工作日志
===================

* 应完成工作
public class InetAddressDemo {

    public static void main(String[] args) throws
            UnknownHostException {

        InetAddress i = InetAddress.getLocalHost();
        // 获取到本机名和地址
        System.out.println(i.toString());
        // 获取ip
        System.out.println("address:" + i.getHostAddress());
        // 获取主机名
        System.out.println("name:" + i.getHostName());

        // 获取任意一台主机地址
        InetAddress ia = InetAddress.getByName("www.baidu.com");
        System.out.println("ia.getHostName()"+ia.getHostName());
        System.out.println("ia.getHostAddress()"+ia.getHostAddress());
        // 获取百度多个IP
        InetAddress[] allByName = InetAddress.getAllByName("www.baidu.com");
        for (int j = 0; j < allByName.length; j++) {
            System.out.println(allByName[j].getHostAddress());
        }
    }
}
* 未完成工作
* 未完成原因
* 工作成功
