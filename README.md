# XBButtonEdgeExtension
UIButton的图片文字位置排布拓展，支持图在上文字在下、图在左文字在右、图在右文字在左排布。左右排布支持设置图文间距，整体内容（图片和文字）居左，居中和居右


#import "ViewController.h"

#import "UIButton+CustomFunctions.h"


@interface ViewController ()
{
    UIButton *testBtn;
}

@end

@implementation ViewController

- (void)viewDidLoad {
    [super viewDidLoad];
    
    testBtn=[UIButton buttonWithType:UIButtonTypeCustom];
    [self.view addSubview:testBtn];
    testBtn.frame=CGRectMake(20, 100, 250, 130);
    testBtn.backgroundColor=[UIColor orangeColor];
    [testBtn setTitle:@"lufy" forState:UIControlStateNormal];
    [testBtn setImage:[UIImage imageNamed:@"LUFY"] forState:UIControlStateNormal];
    testBtn.titleLabel.textColor=[UIColor whiteColor];
    [testBtn imageLeftAndTitleRightWithImageHScale:0.2 spaceOfImageAndTitle:20 side:XBLCRSideLeft sideSpace:10];
}

- (IBAction)btnClick:(UIButton *)sender {
    sender.selected=!sender.selected;
    if (sender.selected)
    {
        //参数1：图片竖直方向上所占的比例（自动根据宽高比调整大小）
        //参数2：图片距离button顶部的距离
        //剩下的空间中，titleLabel竖直方向上居中
        [testBtn imageTopAndTitleBottomWithImageHScale:0.7 topSpace:10];
    }
    else
    {
        //参数1：图片竖直方向上所占的比例（自动根据宽高比调整大小）
        //参数2：图片和文字的距离
        //参数3：内容整体（图片和文字）居左、居中还是居右
        //参数4：居左和居右才有效果，居左：整体内容离控件左边的距离   居右：整体内容离控件右边的距离
        [testBtn imageLeftAndTitleRightWithImageHScale:0.2 spaceOfImageAndTitle:20 side:XBLCRSideLeft sideSpace:10];
    }
}

@end
