// JavaScript Document


//window.onload
function documentReady( fn ){
	if ( document.addEventListener ){       ////  w3c 标准
		document.addEventListener ( 'DOMContentLoaded', fn, false );
	} else {
		document.attachEvent ( 'onreadystatechange', function ( ){        /// IE标准
			if ( document.readyState=='complete' ){
				fn && fn ( );
			};
		} );
	};
};

///----------qise_tools---------------------qise_tools---------------------qise_tools---------------------
var qise_tools={  

	//屏幕居中显示-------------------------------------------------------------
	"showCenter": function (obj){
		var l=(document.documentElement.clientWidth-obj.offsetWidth)/2;
		var h=(document.documentElement.clientHeight-obj.offsetHeight)/2;
		obj.style.left=l+'px';
		obj.style.top=h+'px';
		window.onresize=function(){
			showCenter(obj)
		};
	},
	
	
	//拖拽-------------------------------------------------------------
	"drag": function (obj,title){
		title=title || obj;
		//鼠标点击
		title.onmousedown=function(ev){
			ev = ev || window.event;
			//计算减对象的宽、高
			var disX=ev.clientX-obj.offsetLeft;
			var disY=ev.clientY-obj.offsetTop;
			//鼠标移动
			document.onmousemove=function(ev){
				ev = ev || window.event;
				//计算坐标
				var x=ev.clientX-disX;             //鼠标X轴
				var y=ev.clientY-disY;             //鼠标Y轴
				//屏幕的宽高
				var screen_w=document.documentElement.clientWidth;    //屏幕宽度
				var screen_h=document.documentElement.clientHeight;   //屏幕高度
				//判断坐标
				if(x>screen_w-obj.offsetWidth ){
					x=screen_w-obj.offsetWidth;
				};
				if(x<0){x=0;};
				if(y<0){y=0;};
				if(y>screen_h-obj.offsetHeight){
					y=screen_h-obj.offsetHeight;
				};
				//赋值
				obj.style.left=x+'px';
				obj.style.top=y+'px';
			};
			//鼠标松开
			document.onmouseup=function(){
				document.onmousemove=null;
			};
			return false;
		};
	},
	
	//增加class  -------------------------------------------------------------
	"addClass": function (elm,newCls){       //elm=obj     newCls=新class名
		var newClass=elm.className+' '+newCls;
		return newClass;
	},
	
	
	//放大镜 内置span显示图 ---------------------------------------------------------------------
	"big_glass_one": function (obj1,obj2,obj_img){  //obj1=被放大图的div    obj2=放大镜div   obj_img=放大的图片
		//oBox的move事件
		obj1.onmousemove=function(ev){
			//滚动条
			var scrollTop=document.documentElement.scrollTop || document.body.scrollTop;        //滚动条top
			var scrollLeft=document.documentElement.scrollLeft || document.body.scrollLeft;     //滚动条left
	
			//obj2显示
			obj2.style.display='block';
	
			//计算鼠标和oSpan位置
			ev=ev || event;
			var l=ev.clientX+scrollLeft-obj1.offsetLeft-obj2.offsetWidth/2;     //left坐标
			var t=ev.clientY+scrollTop-obj1.offsetTop-obj2.offsetHeight/2;      //top坐标
	
			//判断 oSpan的边框位置
			if(l<0){l=0;};
			if(t<0){t=0;};
			if(l>obj1.offsetWidth-obj2.offsetWidth){
				l=obj1.offsetWidth-obj2.offsetWidth;
			};
			if(t>obj1.offsetHeight-obj2.offsetHeight){
				t=obj1.offsetHeight-obj2.offsetHeight;
			};
	
			// 赋值
			obj2.style.left=l+'px';     //span的left坐标
			obj2.style.top=t+'px';      //span的top坐标
			
			//计算移动比率
			var move_t=t/(obj1.offsetHeight-obj2.offsetHeight);
			var move_l=l/(obj1.offsetWidth-obj2.offsetWidth);
			//大图移动
			obj_img.style.left=-(obj_img.offsetWidth-obj2.offsetWidth)*move_l+'px';      ////大图的left坐标
			obj_img.style.top=-(obj_img.offsetHeight-obj2.offsetHeight)*move_t+'px';     ////大图的top坐标
	
		};
		//鼠标out事件
		obj1.onmouseout=function(){
			obj2.style.display='none';
		};
	},
	//放大镜 外置div显示图 ---------------------------------------------------------------------
	"big_glass_two": function (obj1,glass,obj2,obj_img){  //obj1=被放大图的div  glass==镜子   obj2=放大镜div   obj_img=放大的图片
		//obj1的move事件
		obj1.onmousemove=function(ev){
			//滚动条
			var scrollTop=document.documentElement.scrollTop || document.body.scrollTop;        //滚动条top
			var scrollLeft=document.documentElement.scrollLeft || document.body.scrollLeft;     //滚动条left
	
			//obj2显示
			glass.style.display=obj2.style.display='block';          //显示oSpan
	
			//计算鼠标和oSpan位置
			ev=ev || event;
			var l=ev.clientX+scrollLeft-qise_tools.offsetLeft(obj1)-glass.offsetWidth/2;     //left坐标
			var t=ev.clientY+scrollTop-qise_tools.offsetTop(obj1)-glass.offsetHeight/2;      //top坐标
			
			//判断 oSpan的边框位置
			if(l<0){l=0;};
			if(t<0){t=0;};
			if(l>obj1.offsetWidth-glass.offsetWidth){
				l=obj1.offsetWidth-glass.offsetWidth;
			};
			if(t>obj1.offsetHeight-glass.offsetHeight){
				t=obj1.offsetHeight-glass.offsetHeight;
			};
	
			// 赋值
			glass.style.left=l+'px';     //span的left坐标
			glass.style.top=t+'px';      //span的top坐标
			
			//计算移动比率
			var move_t=t/(obj1.offsetHeight-glass.offsetHeight);
			var move_l=l/(obj1.offsetWidth-glass.offsetWidth);
			//console.log(move_l)
			//大图移动
			obj_img.style.left=-(obj_img.offsetWidth-obj2.offsetWidth)*move_l+'px';      ////大图的left坐标
			obj_img.style.top=-(obj_img.offsetHeight-obj2.offsetHeight)*move_t+'px';     ////大图的top坐标
	
		};
		//鼠标out事件
		obj1.onmouseout=function(){
			glass.style.display=obj2.style.display='none';
		};
	},
	
	
	//计算offsetTop
	"offsetTop":function (elm){ 
		var top = elm.offsetTop; 
		var parent = elm.offsetParent; 
		while( parent != null ){ 
			top += parent.offsetTop; 
			parent = parent.offsetParent; 
		}; 
		return top; 
	}, 
	
	//计算offsetLeft
	'offsetLeft':function(elm){ 
		var left = elm.offsetLeft; 
		var parent = elm.offsetParent; 
		while( parent != null ){ 
			left += parent.offsetLeft; 
			parent = parent.offsetParent; 
		}; 
		return left; 
	},
	
	//事件监听 ----------------------------------------------------------------
	"addEvent": function ( obj, ev, fn ){
		obj.attachEvent ? obj.attachEvent ( 'on'+ev, fn ) : obj.addEventListener ( 'click', fn, false );
	},
	
	
	//过滤文本和空格 --------------------start-----------------------------------------
	"get_firstChild":function (elm){
		var x=elm.firstChild;
		while (x.nodeType!=1){
			x=x.nextSibling;//把自己变成节点，while继续向前查找
		}
		return x;
	},
	
	"get_lastChild":function (elm){
		var x=elm.lastChild;
		while (x.nodeType!=1){
			x=x.previousSibling;//把自己变成节点，while继续向前查找
		}
		return x;
	},
	
	"get_previousSibling":function (elm){
		var x=elm.previousSibling;
		while (x.nodeType!=1){
			x=x.previousSibling;//把自己变成节点，while继续向前查找
		}
		return x;
	},
	
	"get_nextSibling":function (elm){
		var x=elm.nextSibling;
		while (x.nodeType!=1){
			x=x.nextSibling;
		}
		return x;
	},
	//过滤文本和空格 --------------------end-----------------------------------------
	
	
	
	//读取样式getStyle -------------------------------------------------------------
	"getStyle":function (obj,styleName){
		var value=obj.currentStyle? obj.currentStyle[styleName] : getComputedStyle( obj, false)[styleName];
		styleName==='opacity'? value=parseFloat(value)*100 : value=parseInt(value);
		return value;
	},
	
	
	//运动  -------------------------------------------------------------
	"move":function (obj,modeJson,time,fn){
		
		//设计时间
		var speed={
			"veryslow":2000,
			"slow":1500,
			"normal":1000,
			"fast":500,
			"veryfast":100
		};
		//判断time
		if(time){
			if(typeof time=='string'){      //判断类型
				time=speed[time];           //根据类型赋值
			};
		}else{
			time=speed.normal;
		};
		
		//初始值
		var start={};  //开始初始值
		var dis={};
		
		//遍历modeJson
		for(var key in modeJson){
			start[key]=this.getStyle(obj,key);
			dis[key]=modeJson[key]-start[key];
		};
		
		//时间分段
		var count=parseInt(time/30);     //分段
		var n=0;
			
		//清定时器
		clearInterval(obj.timer);
		//定时器
		obj.timer=setInterval(function(){
			n++;
			var a=1-n/count;
			for(var key2 in dis){
				//步长
				var step_dis=start[key2]+dis[key2]*(1-a*a*a);       
				
				//判断 opacity
				if( key2=='opacity' ){
					//opacity 时
					obj.style.opacity=step_dis/100;
					obj.style.filter='alpha(opacity:'+step_dis+')';
					//console.log(step_dis);
				}else{
					//非opacity 时
					obj.style[key2]=step_dis+"px";
				};
			};
			
			//判断 结束
			if(n===count){
				clearInterval(obj.timer);     
				fn && fn();
			};
		},30);
	}
	







};//结束




