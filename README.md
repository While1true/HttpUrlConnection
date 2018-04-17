# HttpUrlConnection
## 如果你不想导入第三方库，这个原生自带直接用就可以
1.支持 get post 上传 下载 进度
2.支持 webservice
```
public class Main {

    public static void main(String[] args) {


        String soap = NetUtils.doSoap(
                "http://10.0.110.117:8080/Androidpacs/services/PacsAppController",
                "getUserInfo",
                new NetUtils.Params()
                        .add("userName", "kesuzhen")
                        .add("token"));
                        
                        
        String result = NetUtils.get("http://10.0.110.134:8090/masterWeiBo/getHistory100",
                new NetUtils.Params()
                        .add("user","1ec5b436727ddc245b8e2a984eab14b3"));
        System.out.println(result);
        NetUtils.download("http://sw.bos.baidu.com/sw-search-sp/software/d4e97ccd4bd9f/jdk-8u144-windows-i586_8.0.1440.1.exe", new File("123.exe"), new NetUtils.ProgressListener() {
            @Override
            public void call(long current, long total,int speed,String index) {
                System.out.println(String.format("%.2f",speed/1024f)+"Mb/s"+"文件名: "+index+"----"+current*100/total+"%");
            }
        });
//        String upload = NetUtils.upload("http://10.0.110.134:8090/masterWeiBo/uploadPattern", new NetUtils.Params()
//                         .add("user","1ec5b436727ddc245b8e2a984eab14b3")
//                         .add("name","aaa")
//                         .addFile("aaa",new File("123.exe")),
//                     new NetUtils.ProgressListener() {
//                        @Override
//                        public void call(long current, long total,int speed, String name) {
//                            System.out.println("正在上传" + name + "---进度：" + current / 1024 / 1024 + "/" + total / 1024 / 1024);
//                            if(current==total){
//                                System.out.println("-----------" + name + "---完成-------------");
//                            }
//                        }
//                    });
//        System.out.println(upload);
    }
}
```
