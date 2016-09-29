# OL流
======================
* 流的概念
      * 流是一组有顺序的，有起点和终点的字节集合，是对数据传输的总称或抽象。
	
	    * 所谓的IO就是指流的读(input输入)与写(output输出)操作的简称。
	
	    * Java对数据的操作是通过流的方式
	
      * IO流用来处理设备之间的数据传输
      
      public class FileDemo {
      
    public static void main(String[] args){
    
        //创建一个File对象
        
        File file = new File("D:\\tmp\\安卓6组\\java部分");
        
        //创建文件夹
        
        //要判断文件夹是否存在 不存在再创建文件夹
        
        if(!file.exists()) {
        
            file.mkdirs();
            
        }
    }
}

* 创建文件
 
  		package com;

		import java.io.File;
		import java.io.IOException;
    
    public class FileDemo1 {

    public static void main(String[] args){
    
         //创建一个File对象
         
         File file = new File("D:\\tmp\\测试");
         
         file.mkdirs();
         
         //根据文件所在文件夹对象，创建文件
         
         File fileDoc = new File("E:\\tmp\\测试");
         
         //创建文件
         
         try{
         
             fileDoc.createNewFile();
             
         }
         
         catch(IOException e){
         
             e.printStackTrace();
             
         }
     }
}

* 判断File对象是目录还是文件

public class FileDeom2 {

    public static void main(String[] args){
    
        // 创建一个File对象
        
        File file = new File("D:\\tmp\\测试\\爱党\\爱国.doc");

        // 判断 file 是文件夹还是文件
        
        boolean bln = file.isDirectory();
        
        boolean bln1 = file.isFile();

        System.out.println("是否是目录："+bln+"|是否是文件:"+bln1);

    }
}

* 给文件重命名

  public class FileDemo3 {
    
        public static void main(String[] args) {

            // 创建一个File对象
            
            File file = new File("E:\\tmp\\测试\\爱国.doc");
            
            try {
            
                file.createNewFile();
                
            } catch (IOException e) {
            
                e.printStackTrace();
                
            }
            
            // 判断 file 是文件夹还是文件
            
            boolean bln = file.isDirectory();
            
            boolean bln1 = file.isFile();

            // 所谓的修改文件的名称，实际上是先把源文件内容复制到一个新名称的新文件中，
            
            // 然后把源文件给删除
            
            file.renameTo(new File("E:\\tmp\\测试\\","不爱国.doc"));

            // 获取file的名字
            
            System.out.println("文件的（绝对）路径:" + file.getAbsolutePath());
            
            System.out.println("文件的名字:" + file.getName());
            
            System.out.println("是否是目录：" + bln + "|是否是文件:" + bln1);
            

        }
    }
    
    *修改文件
    
    public class FileDemo4 {
    
        public static void main(String[] args) {

            // 创建一个File对象
            
            File file = new File("E:\\tmp\\测试");
            
            // 判断 file 是文件夹还是文件
            
            boolean bln = file.isDirectory();
            
            boolean bln1 = file.isFile();

            // 修改文件夹是将文件夹改名
            
            file.renameTo(new File("E:\\tmp\\测试1"));

            // 获取file的名字
            
            System.out.println("文件的（绝对）路径:" + file.getAbsolutePath());
            
            System.out.println("文件的名字:" + file.getName());
            
            System.out.println("是否是目录：" + bln + "|是否是文件:" + bln1);
            

        }
    }

    *复制文件
    
    
