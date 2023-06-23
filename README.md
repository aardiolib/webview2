# webview2

这是一个 webview2 SDK, 具体用法参考示例以及 [WebView2 Win32 C++](https://learn.microsoft.com/en-us/microsoft-edge/webview2/reference/win32/)

## 安装
### npm

下载扩展库
``` bash
npm i @aardiolib/webview2
```

复制扩展库到用户库
``` bash
Xcopy .\node_modules\@aardiolib\webview2\ .\lib\webview2\ /E /Y
```

## 示例

简单示例
```js
import win.ui;
import webview2;

/*DSG{{*/
var winform = win.form(text="webview2 Demo";right=759;bottom=469)
winform.add()
/*}}*/

..webview2.CreateCoreWebView2Environment(function(errorCode,createdEnvironment){
	
	createdEnvironment.CreateCoreWebView2Controller(winform,function(errorCode, createdController){
		
		winform.adjust = function(){
			createdController.put_Bounds(winform.getClientRect());
		}
		
		createdController.put_Bounds(winform.getClientRect());
		
		createdController.put_IsVisible(true);
		
		var m_webView = createdController.get_CoreWebView2();
		
		m_webView.Navigate("https://www.baidu.com/");
	})
})

winform.show();

win.loopMessage();
```

### 更多示例

- [多开](./example/%E5%A4%9A%E5%BC%80.aardio)