# FlappyBird_js
FlappyBird 业务逻辑：
1、鼠标点击，点击一次，鸟向上飘一次，再下坠
2、水管不断向左移动
3、检查有没有碰撞
#test
实现：
1、背景图嵌入（done）
	背景图不断向左移动，表现出小鸟不断向右飞的样子(done)
		little trick:将背景图片扩大到两倍，使div只有一倍大小，这样背景图循环起来，没到-288就重置位置为0，看上去就像动画一样
2、小鸟先自由落体，再响应'SPACE'按键事件弹跳（done）
	响应"鼠标点击"小鸟跳跃(done)
	响应"touch",小鸟跳跃(done)
	Crafty.trigger("KeyDown", {key: Crafty.keys.UP_ARROW});触发跳跃(done)
3、背景图作为不断向左移动
4、pipe不断向左移，若小鸟从中间穿过，得分，碰到上下任一块，dies
	获得一个随机数表示得分线的位置，得分线长度为三个小鸟的宽度
	得分线上、下部各为一个entity(done)
	得分线与两个entity一起向左移动；(done)
	若碰得分线且没碰管道，得分；碰到管道，dies(done)
		使用Collision组件中的onHit()方法，检测是否与pipe碰撞
	管道出界后，重新获得随机数，管道的循环解决！(done)
		使用.bind('EnterFrame', function (){
			if(...){
			...
		}
		})
		绑定在得分线上，当出界时，将横坐标重置
