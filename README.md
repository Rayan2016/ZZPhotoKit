# ZZPhotoKit
/* 说明 */

/*
 
    ** 此开源仅供初学者学习参考，不喜欢的大神们还望轻虐。
 
    ** 此开源中并不完善还需以后的慢慢改进，增强功能。
 
    ** 此开源中相机调用部分代码来自另外一个作者。
 
    ** 相册多选使用最新的 PhotoKit 框架
 
    ** 图片浏览器支持 SDWebImage 加载图片
 
    ***
    有什么不明白的地方，或者哪里需要改进的可以联系我 
    
    ** 联系方式
 
    *** 关注微博：袁亮_TRICK  *** QQ:412016060
 
 */

/*
    ** 更新内容   UIImageHandle.h 文件
    1. 修复第一次打开相册不弹出相册Bug.
    2. 修复导入报错问题.
    3. 更新连拍相机页面UI.
    4. 添加图片返回类型.（目前支持两种类型，原图和缩略图。）
 
 */

/*
    ** 使用方法
    
    ※※※ 首先重要提醒一个 文件，Common.h 这个配置文件。
    ※※※ 1.包含了所有的按钮图片信息，任意更换即可.
    ※※※ 2.包含了图片返回类型的公共枚举.
    ※※※ 3.所有用到的头文件。以及一些颜色、控制器宽高、屏幕宽高宏定义.
 
    ***** 导入头文件   *****
    #import "ZZPhotoController.h"
    #import "ZZCameraController.h"
    #import "ZZBrowserPickerViewController.h"
 
 
    * 相册多选的调用
    ZZPhotoController *photoController = [[ZZPhotoController alloc]init];
 
    //设置最大选择张数
    photoController.selectPhotoOfMax = 5;
 
    //设置图片返回类型 （下面例子为缩略图）
    photoController.imageType = ZZImageTypeOfThumb;
 
    [photoController showIn:self result:^(id responseObject){
        //返回结果集
        NSLog(@"%@",responseObject);
        NSArray *array = (NSArray *)responseObject;
 
        UIImage *image = [array objectAtIndex:0];
        _imageView.image = image;
    }];
 
    * 相机连拍的调用
    ZZCameraController *cameraController = [[ZZCameraController alloc]init];
    //设置最大连拍张数
    cameraController.takePhotoOfMax = 8;
    //设置图片返回类型 （下面例子为缩略图）
    cameraController.imageType = ZZImageTypeOfThumb;
    [cameraController showIn:self result:^(id responseObject){
        //返回结果集
        NSLog(@"%@",responseObject);
        NSArray *array = (NSArray *)responseObject;
 
        UIImage *image = [array objectAtIndex:0];
        _imageView.image = image;
    }];
 
    * 简单的图片浏览器
    ZZBrowserPickerViewController *browserController = [[ZZBrowserPickerViewController alloc]init];
    browserController.delegate = self;
    [browserController showIn:self animation:ShowAnimationOfPush];
    
    //delegate
    //图片的个数。
    -(NSInteger)zzbrowserPickerPhotoNum:(ZZBrowserPickerViewController *)controller
    //图片的数组。
    -(NSArray *)zzbrowserPickerPhotoContent:(ZZBrowserPickerViewController *)controller
 
 
    ** 详细使用方法还是看demo 吧。
 */

