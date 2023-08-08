#### 实时检测猫脸

 ## cameraId 0 是后置相机   1是前置相机
 ## quality  返回图片压缩比 默认80
 ## type  0 实时检测返回图片，  1 检测1秒以上，选取一张图片返回并关闭页面
 ## num  1单独检测最大的那个脸框  其他检测多个
 ### goToFace（{String cameraId,int quality,int type,int num}，callback(boolean face,String faceBase64)）
 ##  face 目前只要有返回都是true
 ##  faceBase64 返回图片base64  如果需要显示记得加  data:image/jpeg;base64,





#### 关闭检测并退出页面
 ### closePage（）
