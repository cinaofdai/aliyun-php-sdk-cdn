# aliyun-php-sdk-cdn
阿里云CDN推送SDK包

## 使用方法
   资料见:https://help.aliyun.com/document_detail/27257.html?spm=5176.doc27234.6.709.aWpyJz
   
 **SDK示例**

```php
 AliyunCdn::start();
 $c = new \AliyunClient;
 $c->accessKeyId = "<accessKeyId>";
 $c->accessKeySecret = "<accessKeySecret>";
 $c->serverUrl = "<serverUrl>"; //根据不同产品选择相应域名，例如：CDN，http://cdn.aliyuncs.com/


 //刷新缓存
 $req = new \Cdn20141111RefreshObjectCachesRequest();
 $req->setObjectType("File"); // or Directory
 $req->setObjectPath("www.yourdomain.com/path/filename.ext");
 try {
     $resp = $c->execute($req);
     if(!isset($resp->Code))
     {    
         //刷新成功
         echo($resp->RequestId);
         print_r($resp);
     }
     else 
     {
         //刷新失败
         $code = $resp->Code;
         $message = $resp->Message;
     }
 }
 catch (Exception $e)
 {
     // TODO: handle exception
 }
```