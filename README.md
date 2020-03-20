## JS原生轮播原生代码

以下是我个人总结的简单经验分享
1.先设计好轮播样式（图片、左右箭头键、轮播点）
2.设计点的样式改变（自动播放、点击变样式，其他样式相反、点击选中原先图片）
3.调用轮播动图
4.绑定右键（一般右键和轮播滚动方向一致，设置到终点回调第一张图片就好了）绑定左键（正好相反）
5.设置鼠标进入改变样式



### 废话少说上代码

```markdown
<div class="all" id="all">
		    <!-- 内容部分 -->
		    <ul class="content1" id="content1">
		        <li><img src="1.jpg" alt=""></li>
				<li><img src="2.jpg" alt=""></li>
				<li><img src="3.jpg" alt=""></li>
				<li><img src="4.jpg" alt=""></li>
				<li><img src="5.jpg" alt=""></li>
		    </ul>
		    <!-- 内容部分 end -->
		
		    <!-- 点 -->
		    <div class="dian" id="dian">
		        <span></span>
				<span></span>
				<span></span>
				<span></span>
				<span></span>
		    </div>
		    <!-- 点 end -->
		    <!--箭头-->
		   <div class="huan" id="huan">
		        <span id="huan_left" class="huan_left">&lt;</span>
		        <span id="huan_right" class="huan_right">&gt;</span>
		    </div>
		
		    <!--箭头 end-->
		
		</div>

# Header 1

<script type="text/javascript">
		
			var qwe = 0;
			var long = 1200;
			var cont = document.getElementById("content1");
			var dian =document.getElementById("dian").getElementsByTagName("span");
			var all = document.getElementById("all");
			
			
			var left = document.getElementById("huan_left");
			var right = document.getElementById("huan_right");
			
	
			function zido(){  //自动加载
						qwe++;
						if(qwe>4){
							qwe=0;
							cont.style.transform="translateX("+(-long*qwe)+"px)";
//							dian[a].className='';
						}
						else{
							cont.style.transform="translateX("+(-long*qwe)+"px)";
							for(var a =0;a<dian.length;a++)
										{
											dian[a].className='';//清空其他样式
										}
							dian[qwe].className='green';//设置当前样式

							
						}
						
						
						
						}
			
			var www=setInterval(zido,500)
			all.onmouseover = function()
			{
				clearInterval(www)//清除样式
			}
			all.onmouseout = function(){ //鼠标移开事件（恢复自动轮播）
			www=setInterval(zido,500)
			}
						
						for(let i=0;i<dian.length;i++){
									dian[i].index=i;
									dian[i].onclick=function()
									{
										for(var j =0;j<dian.length;j++ )
											{
											dian[j].className='';//清空其他样式
											}

										dian[i].className='green';//设置当前样式
										cont.style.transform="translateX("+(-long*i)+"px)";

									}
						
								}
				
			
			left.onclick=function(){
				qwe--;
				if(qwe<0)
					{
						qwe=4;
						cont.style.transform="translateX("+(-long*qwe)+"px)";
						
					}
				else
					{
						cont.style.transform="translateX("+(-long*qwe)+"px)";
					}
				
			}
			
			right.onclick=function(){
				zido();
				
			}
  
  ```
  
  
### 由于时间仓促，就用原生简单写了一下，后面还需要修改一下
### 其实轮播图最好用jquery来写(因为代码比较少，还很灵活)

- 以上是本人的简单JS轮播代码 欢迎关注我的git  https://github.com/tianwenlike

- 本人有个独自的微信公众号，欢迎骚扰————零点起飞
