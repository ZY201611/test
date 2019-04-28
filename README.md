# ** 海鸟项目**

基于Hybird实现文件本地化管理
1、封装的一个webViewController,暴露一些配置参数，实现里面定义好的功能，开放一些功能，但也会有些功能不允许定制的。
2、剩下的以**DEMO**参考

## https配置
- 1、<key>NSAppTransportSecurity</key>
<dict>
 <key>NSAllowsArbitraryLoads</key>
    <true/>
         </dict>
         
         - 2、Build Phases(Build Phases->Link Binary With Libraries)
         导入   JavaScriptCore.framework，SystemConfiguration.framework
         
         
         ## 体系结构（包含哪些主要的类）
         
         LazyWebView    //WKWebView类
         AFNetworkTool  //封装网络请求类
         AFNetworkDownLoad  //下载的工具类
         LazyZipMD5     //文件夹内容加密
         LazyWebViewController  //主要的webView界面
         
         
         ## 集成步骤：
         
         #### 第一步：
         把demo中的HybirdCodeClass整个文件夹拷贝到工程中即可，不需要自己导入图片了，图片我已经生成在bundle文件中。
         
         ## 第二步：
         
         Podfile中需要导入的文件
         
         pod 'UnrarKit'
         pod 'SSZipArchive'
         pod 'LzmaSDK-ObjC', :inhibit_warnings => true
         
         ## 第三步：
         
         在Appdelegate中： #import “LazyWebViewManager.h”  //导入
         在didFinishLaunchingWithOptions方法中实现下面的方法。
         [[LazyWebViewManager shareLazyManager] initializeMD5:@"这里是后台返回文件加密的md5值" zipUrl:@"这里是下载zip的url" version:@"这里是后台返回zip的版本号" isFull:NO isUpdate:NO domainName:@"域名" progress:^(NSInteger hasLoadLength, NSInteger totalLengt) {
         
          } downLoadSuccess:^{ 
          
           }];
           
           ## 第四步：
           
           导入配置文件 #import “LazyWebViewNavBarModel.h”，#import     “LazyWebViewController.h”
           所有的配置都在这个model中，传入定义好的参数即可
           
           
            ```html
             LazyWebViewController *wkVC = [[LazyWebViewController alloc] init];
              [self.navigationController pushViewController:wkVC animated:YES];
              ```
              
