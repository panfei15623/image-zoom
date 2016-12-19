图片预览组件    

组件说明：     
 该组件是类似于QQ聊天里的图片预览功能，基于bootstrap.js的模态框实现的图片预览组件，其中包括图片放大、缩小、旋转功能。    
 
 使用说明：   
 1、在浏览器中打开image-zoom.html，可以看到效果并操作          
 2、集成时引入jquery.js,bootstrap.mim.js,ks-drag.js,IMG.js,bsf.css文件（引入的文件有点多，ks-drag.js是封装的拖拽组件，集成之后可以实现聊天框、图片等的拖拽功能）     
 3、文件引入后调用IMG.show(imgPath);参数为图片路径即可     
 
 知识点总结：    
 1、IE8及之前版本中双击事件的bug   
 正常的双击事件，事件触发顺序：   
 (1)mousedown   
 (2)mouseup   
 (3)click   
 (4)mousedown   
 (5)mouseup   
 (6)click   
 (7)dbclick   
 click和dbclick事件会依赖其他先行事件的触发，而mousedown和mouseup则不受其他事件的影响。   
 
 IE8及之前版本中的实现有一个小bug，在双击事件中，会跳过第二个mousedown和click事件，其顺序如下：   
  (1)mousedown   
  (2)mouseup   
  (3)click   
  (4)mouseup    
  (5)dbclick      
  
  IE9修复了这个bug，之后顺序就正确了。     
 
 在该组件中既绑定dbclick事件又绑定click事件解决IE8双击问题        
 
 2、判断浏览器版本   
 (1)判断是不是IE浏览器    
 判断浏览器是否支持__proto__属性（除了IE，其他浏览器都支持）   
 '__proto__' in {}   
 
 (2)判断各浏览器
 navigator.userAgent  返回浏览器版本信息

用以下方式，可以判断各种浏览器类型
navigator.userAgent.indexOf(浏览器名) > 0

/*** 判断IE8/IE9*/

var judgeIE = function() {
if(navigator.userAgent.indexOf("MSIE") > 0) {      
  if(navigator.userAgent.indexOf("MSIE 6.0") > 0) {}     
  if(navigator.userAgent.indexOf("MSIE 7.0") > 0) {}      

  if(navigator.userAgent.indexOf("MSIE 8.0") > 0) {      
      console.log("IE8");     
  }     

  if(navigator.userAgent.indexOf("MSIE 9.0") > 0) {     
      console.log("IE9");     
  }     
 }     
};     

(3)判断浏览器是否支持DOM2级事件，IE8不支持，IE8以上支持        
   isIEgt8 = document.implementation.hasFeature("MouseEvents","2.0");
   
 3、IE8不支持CSS3的rotate图片旋转属性     
 解决办法：     
 给id添加filter属性，ie8_deg的值为0，1，2，3  分别对应90度，180度，270度，360度      
 $("#rotate-btn").bind("click", function() {     
     ie8_deg = (ie8_deg + 1) % 4;      
     $img.get(0).style.filter = 'progid:DXImageTransform.Microsoft.BasicImage(rotation='+ ie8_deg + ')';     
 });
 
 4、滚轮事件
 五大浏览器（IE、Opera、Safari、Firefox、Chrome）中事件名不同，firefox事件名为"DOMMouseScroll",其他浏览器事件名为"mousewheel".
 事件属性不同，firefox使用detail，其余四类使用wheelDelta;
 取值上不同，代表含义一致，detail与wheelDelta只各取两个值，detail只取±3，wheelDelta只取±120
    
  $imgContainer.bind("mousewheel", zoomImageOnMouse).bind("DOMMouseScroll", zoomImageOnMouse);    
    
   function zoomImageOnMouse(event) {      
       //firefox使用detail，其余四类使用wheelDelta,Firefox向上滚 < 0，其他四个浏览器相反。     
       var wheel = event.originalEvent.wheelDelta || -event.originalEvent.detail;     
       wheel > 0 ? IMG.zoomIn() : IMG.zoomOut();     
   }

  
  
      
  

 
 
 


 

