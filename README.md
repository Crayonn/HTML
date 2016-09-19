<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		*{margin:0px;padding:0px;list-style:none;text-decoration:none;}
		#point li{
			float:left;
			width:20px;
			height:28px;
			background:url('star.png') no-repeat 0px 0px;
		}
		#con{
			font:12px/20px '微软雅黑';
			width:179px;
			height:67px;
			padding:5px 0px 0px 5px;
			background:url('icon.gif') no-repeat;
			position:absolute;
			top:28px;
			left:-100px;
			display:none;
			
		}
		#point{
			margin-left:20px;
			margin-top:100px;
			position:relative;
			float:left;
		}
		span{

			font:16px/225px '微软雅黑';
		}
		h3{
			font:16px '微软雅黑';
			float:left;
			margin-top:100px;
			margin-left:250px;
		}
		.ofont{
			color:gold;
		}
	</style>
</head>
<body>
	<h3>点击星星打分:</h3>
	<ul id='point'>
		<a href='javascript:;'><li></li></a>
		<a href='#'><li></li></a>
		<a href='#'><li></li></a>
		<a href='#'><li><a href='#'></a></li></a>
		<a href='#'><li style='margin-right:10px'></li></a>
		<div id='con'></div>	
	</ul>
	<span></span>
</body>
</html>
<script>
window.onload=function(){
	var aMsg = [
				"<font class='ofont'>1分</font> 很不满意<br />差得太离谱，与卖家描述的严重不符，非常不满",
				"<font class='ofont'>2分</font> 不满意<br />部分有破损，与卖家描述的不符，不满意",
				"<font class='ofont'>3分</font> 一般<br />质量一般，没有卖家描述的那么好",
				"<font class='ofont'>4分</font> 满意<br />质量不错，与卖家描述的基本一致，还是挺满意的",
				"<font class='ofont'>5分</font> 非常满意<br />质量非常好，与卖家描述的完全一致，非常满意"
				]
	var aaMsg = [
				"<font class='ofont'>1分</font> (差得太离谱，与卖家描述的严重不符，非常不满)",
				"<font class='ofont'>2分</font> (部分有破损，与卖家描述的不符，不满意)",
				"<font class='ofont'>3分</font> (质量一般，没有卖家描述的那么好)",
				"<font class='ofont'>4分</font> (质量不错，与卖家描述的基本一致，还是挺满意的)",
				"<font class='ofont'>5分</font> (质量非常好，与卖家描述的完全一致，非常满意)"
				]
	odiv = document.getElementById('point').getElementsByTagName('li');
	var sp = document.getElementsByTagName('span')[0];
	var ads = document.getElementById('con'); 
	var stop = false; 
	var star=0;
	for(var i= 0;i<odiv.length;i++){
		//给li数组添加引索
		odiv[i].index = i;
		//鼠标移入时
		odiv[i].onmouseover=function(){
			ad(this.index);
			ads.style.left = (odiv.length-this.index-1) *-1* odiv[0].offsetWidth + 'px';
			ads.style.display = 'block';
			for(var i=0;i<aMsg.length;i++){
				ads.innerHTML = aMsg[this.index];
			}
		}
		//鼠标移除时判断点击事件的值并根据该值循环
		odiv[i].onmouseout=function(){
				ad(star);
				ads.style.display = 'none';
			}

		//鼠标点击时
		odiv[i].onclick=function(){
			star=this.index;
			ads.style.display = 'none';
			ad(this.index)
			for(var i=0;i<aMsg.length;i++){
				sp.innerHTML = aaMsg[this.index]
			}
		}
	}
}
	//构造一个方法
	function ad(a){
		for(var i =0;i<odiv.length;i++){
			if(i<=a){
				odiv[i].style.backgroundPosition = '0px -28px';
			}else{
				odiv[i].style.backgroundPosition = '0px 0px';
			}	
		}
	}
</script>
