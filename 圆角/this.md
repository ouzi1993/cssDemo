圆角实现方式
=====================

##css3
>border-radius

##border-image
>一个任意长宽的圆角背景图。25px决定圆角弧度的大小，25%决定了background和文字间的padding宽度

	.box {
		-webkit-border-image:url("background.png")
		25% 25% 25% 25% / 25px round round;
	}

##静态圆角
>box的width:424px,因为bg图的宽度就是424。。。。少了会缺，多了字会溢出来;repeat-y所以会竖直方向能自动扩；  
h2的图放top，底下p的图放bottom；  
有no-repeat,才不会出现：比如h2的高度大于原top2.gif，它就会在h2的高度内竖直repeat；  
再加一些padding就好了
>缺点：只能竖直方向自动，水平不行；

    .box {
        width: 424px;
        background: url("tile2.gif") repeat-y;
    }
    .box h2 {
        background: url("top2.gif") no-repeat top;
        padding-top: 20px;
    }
    .box .last {
        background: url("bottom2.gif") no-repeat bottom;
        padding-bottom: 20px;
    }
    p {
        margin: 0px;
    }
    .box h2, .box p {
      padding-left: 20px;
      padding-right: 20px;
    }

    <div class = "box">
        <h2>title</h2>
        <p class="last">Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Proin venenatis turpis ut quam. In dolor. Nam ultrices nisl sollicitudin sapien. Ut lacinia aliquet ante. dasd afdsdfasdfdsafasfd gasdFDASFSDFASDFDASFSDAFSDAFSD</p>
    </div>

##动态圆角
>四个嵌套顺序是 左下，右下，左上，右上；  
全部都要 no-repeat;  
全部都要position；

    .box {
        width: 20em;
        background: url('bottom-left.gif') no-repeat bottom left;
    }
    .box-outer {
        background: url('bottom-right.gif') no-repeat bottom right;
    }
    .box-inner {
        background: url('top-left.gif') no-repeat top left;
    }
    .box h2 {
        background: url('top-right.gif') no-repeat top right;
    }
    .box h2, .box p {
        padding-left: 1em;
        padding-right: 1em;
    }

    <div class = "box">
        <div class = 'box-outer'>
            <div class = 'box-inner'>
                <h2>nihao</h2>
                <p>dhasjldg hgajdkgA ;DHSA;KDLHSAJkdhasj;d;HAL DHAJDSA hdsakj dhsakj dhkjas hdkjas HDKJSAHDKSA HLFAGF LHa;kdsjad;jsa;L</p>
            </div>
        </div>
    </div>

