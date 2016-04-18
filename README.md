# Android_Monkey_UI_Test
在monkey的源码中我们可以看到以下例子： 
  /**  
   * monkey event queue. It takes a script to produce events  
   *   
   * sample script format:  
   *      type= raw events  
   *      count= 10  
   *      speed= 1.0  
   *      start data >>  
   *      captureDispatchPointer(5109520,5109520,0,230.75429,458.1814,0.20784314,  
   *          0.06666667,0,0.0,0.0,65539,0)  
   *      captureDispatchKey(5113146,5113146,0,20,0,0,0,0)  
   *      captureDispatchFlip(true)  
   *      ...  
   */    
 
由此可知，我们可以通过编写script来实现使用monkey进行指定操作。

首先，我们需要获取被测程序的包名和lanch activity。

然后我们需要编写一个script脚本，具体如下：

qqtest.script

API中还有其他比较常用的事件，如：DispatchKey（按手机硬件）、DispatchTrakball（轨迹球）等。

上例中有几个重要参数需要解释一下：

DispatchPointer(downTime, eventTime,action, x, y, pressure, size, metaState, xPrecision, yPrecision,device, edgeFlags);

其中action=0时为按下，action=1时为移动，action=2时为抬起，action=3时为取消。x、y为坐标点。pressure为压力值类型为float，size为点击范围大小类型为float。device为deviceID。

其他的参数仍然在研究中。

下载附件到D盘。

然后输入命令： 

  adb push D:\qqtest.script /sdcard/
  
  adb shell monkey -f /sdcard/qqtest.script -v 1

其中1为执行脚本次数。 
