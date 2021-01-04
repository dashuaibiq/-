# -
魔方18电信3班
（文档）。准备就绪（函数（）{


	var  useLockedControls  =  true ，
		控件 =  useLockedControls吗？ERNO 。锁定：ERNO 。自由形式;

	var  ua  = 导航器。userAgent ，
		isIe  =  ua 。indexOf （'MSIE' ） >  - 1  ||  ua 。indexOf （'Trident /' ） >  - 1 ;

	窗口。cube  = 新的 ERNO 。立方体（{
		hideInvisibleFaces：true ，
		控件：控件，
		渲染器：是吗？ERNO 。渲染器。IECSS3D：null
	} ）;


	var  container  =  document 。getElementById （ 'container'  ）;
	容器。的appendChild （ 立方体。一个DOMElement  ）;



	if （ 控件 ===  ERNO 。已锁定 ）{
		var  fixedOrientation  = 新的 三个。欧拉（  数学式。PI * 0.1 ， 数学。PI * - 0.25 ， 0  ）;
		立方体。object3D 。lookAt （ 立方体，相机。位置 ）;
		立方体。旋转。x  + =  fixedOrientation 。x ;
		立方体。旋转。y  + =  fixedOrientation 。Ÿ ;
		立方体。旋转。z  + =  fixedOrientation 。z ;
	}




	控制台。日志（窗口。立方体）;

