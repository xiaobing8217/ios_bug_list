# ios_bug_list

1、snapshot方法引起的crash
详情：在工程中有一个文件叫UIView+Snapshot.h，里面定义了一个UIView的分类方法叫- (UIImage *)snapshot; 在更新了iOS13.4.1的机器上，调用snapshot方法时调用不到此方法导致抛异常crash。分析可能是系统内提供了同名的方法导致调用的时候调到了系统内部的方法，而系统内部的方法在UIView还没有渲染完成的时候调用会抛异常导致crash。
展示规律：程序运行总是在调用此方法后的方法上中断，并不会直观的断在此方法上。
解决办法：把方法名改成别的名称，与系统内部的方法名区分开，例如改为customsnapshot；

2、子线程中调用ui相关的方法引起的crash
详情：
展示规律：随机crash，也有可能不crash，没发现规律；
解决办法：避免这种情况

