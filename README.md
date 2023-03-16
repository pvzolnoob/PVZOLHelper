# pvzolhelper
植物ol优化，解决高峰期进入游戏加载卡顿问题

下载fiddler https://www.telerik.com/download/fiddler

打开自定义规则/快捷键 CTRL+R

下翻/ CTRL+F 搜索找到static function OnBeforeRequest(oSession: Session) {

另起一行，直接将代码复制到下面用于自动加载本地数据:
var path: String = System.IO.Directory.GetCurrentDirectory() + "/cache/" + oSession.PathAndQuery.Split("?")[0]; 
if (System.IO.File.Exists(path)){oSession.LoadResponseFromFile(path);return;}

更改完后 CTRL+S 或者手动保存

下载cache文件，链接：https://github.com/pvzolnoob/pvzolhelper/raw/main/cache.rar

将文件解压/直接拖拽出来到AppData\Local\Programs\Fiddler文件夹里
路径不清楚，右键fiddler快捷键图标，选择属性并打开文件路径

实现自动加载本地存储资源/不需要再向服务器一次次请求动画资源
