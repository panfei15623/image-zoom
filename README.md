ͼƬԤ�����    

���˵����     
 �������������QQ�������ͼƬԤ�����ܣ�����bootstrap.js��ģ̬��ʵ�ֵ�ͼƬԤ����������а���ͼƬ�Ŵ���С����ת���ܡ�    
 
 ʹ��˵����   
 1����������д�image-zoom.html�����Կ���Ч��������          
 2������ʱ����jquery.js,bootstrap.mim.js,ks-drag.js,IMG.js,bsf.css�ļ���������ļ��е�࣬ks-drag.js�Ƿ�װ����ק���������֮�����ʵ�������ͼƬ�ȵ���ק���ܣ�     
 3���ļ���������IMG.show(imgPath);����ΪͼƬ·������     
 
 ֪ʶ���ܽ᣺    
 1��IE8��֮ǰ�汾��˫���¼���bug   
 ������˫���¼����¼�����˳��   
 (1)mousedown   
 (2)mouseup   
 (3)click   
 (4)mousedown   
 (5)mouseup   
 (6)click   
 (7)dbclick   
 click��dbclick�¼����������������¼��Ĵ�������mousedown��mouseup���������¼���Ӱ�졣   
 
 IE8��֮ǰ�汾�е�ʵ����һ��Сbug����˫���¼��У��������ڶ���mousedown��click�¼�����˳�����£�   
  (1)mousedown   
  (2)mouseup   
  (3)click   
  (4)mouseup    
  (5)dbclick      
  
  IE9�޸������bug��֮��˳�����ȷ�ˡ�     
 
 �ڸ�����мȰ�dbclick�¼��ְ�click�¼����IE8˫������        
 
 2���ж�������汾   
 (1)�ж��ǲ���IE�����    
 �ж�������Ƿ�֧��__proto__���ԣ�����IE�������������֧�֣�   
 '__proto__' in {}   
 
 (2)�жϸ������
 navigator.userAgent  ����������汾��Ϣ

�����·�ʽ�������жϸ������������
navigator.userAgent.indexOf(�������) > 0

/*** �ж�IE8/IE9*/

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

(3)�ж�������Ƿ�֧��DOM2���¼���IE8��֧�֣�IE8����֧��        
   isIEgt8 = document.implementation.hasFeature("MouseEvents","2.0");
   
 3��IE8��֧��CSS3��rotateͼƬ��ת����     
 ����취��     
 ��id���filter���ԣ�ie8_deg��ֵΪ0��1��2��3  �ֱ��Ӧ90�ȣ�180�ȣ�270�ȣ�360��      
 $("#rotate-btn").bind("click", function() {     
     ie8_deg = (ie8_deg + 1) % 4;      
     $img.get(0).style.filter = 'progid:DXImageTransform.Microsoft.BasicImage(rotation='+ ie8_deg + ')';     
 });
 
 4�������¼�
 ����������IE��Opera��Safari��Firefox��Chrome�����¼�����ͬ��firefox�¼���Ϊ"DOMMouseScroll",����������¼���Ϊ"mousewheel".
 �¼����Բ�ͬ��firefoxʹ��detail����������ʹ��wheelDelta;
 ȡֵ�ϲ�ͬ��������һ�£�detail��wheelDeltaֻ��ȡ����ֵ��detailֻȡ��3��wheelDeltaֻȡ��120
    
  $imgContainer.bind("mousewheel", zoomImageOnMouse).bind("DOMMouseScroll", zoomImageOnMouse);    
    
   function zoomImageOnMouse(event) {      
       //firefoxʹ��detail����������ʹ��wheelDelta,Firefox���Ϲ� < 0�������ĸ�������෴��     
       var wheel = event.originalEvent.wheelDelta || -event.originalEvent.detail;     
       wheel > 0 ? IMG.zoomIn() : IMG.zoomOut();     
   }

  
  
      
  

 
 
 


 

