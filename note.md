异常： to resolve: com.android.support:appcompat-v7:27.+：
分析：
解决方案：降低compileSdkVersion 和targetSdkVersion版本

异常：Error:Execution failed for task ':app:mergeDebugResources'.
	> Error: Some file crunching failed, see logs for details：
分析：
解决方案：在app下的build.gradle  android{}中添加：
 		aaptOptions{
        	cruncherEnabled = false
       		useNewCruncher = false
  	  	}

背景：使用DelegateAdapter；adapter继承DelegateAdapter.Adapter时；进行数据的刷新或移除等操作
异常：使用DelegateAdapter时，产生ViewHolder 强制类型转换异常
分析：可能是ViewHolder复用引起的，
解决方案：为每个adapter的ViewHolder设置getItemViewType()（注意：应该为每个ViewHolder都返回唯一的标识）
		
使用ViewPager加载多个fragment中时，在fragment中执行某些操作，
可能会引起某些重复（如数据加载重复，某段行为执行多次等），
		原因：导致这些重复行为的原因可能是 ViewPager的预加载引起的