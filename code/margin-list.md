## 带 margin 的列表

### 多层 div overflow 
````html
<div class="box">
    <div class="inner b-clear">
        <div class="item"> 1 </div> <div class="item"> 2 </div> <div class="item"> 3 </div> <div class="item"> 4 </div> <div class="item"> 5 </div> <div class="item"> 6 </div> </div>
</div>
````
````css
body {
    padding-left:10px;
    padding-right:10px;
}
.box,
.box2 {
    background:#eee;
}
/* 清理浮动 */
.b-clear:after {visibility:hidden; display:block; font-size:0; content:" "; clear:both; height:0;}
.b-clear {zoom:1; /* for IE6 IE7 */}
````

````css
.box { 
    width:320px;
    /*overflow:hidden;*/
}
.inner {
    width:330px;
}
.item {
    width:100px;
    height:100px;
    background:#ABCDEF;
    float:left;
    margin-right:10px;
    text-align:center;
    color:white;
    line-height:100px;
}
````

### css3 nth-child

````html
<div class="box2 b-clear">
    <div class="item"> 1 </div> <div class="item"> 2 </div> <div class="item"> 3 </div> <div class="item"> 4 </div> <div class="item"> 5 </div> <div class="item"> 6 </div> 
</div>
````

````css
.box2 {
    width:320px;
}
.box2 .item:nth-child(3n+0) {
    margin-right:0;
}
/* 配合媒体查询改变 nth-child 值 */
@media (min-width: 960px){
    .box2 {
        width:210px;
    }
    .box2 .item:nth-child(3n+0) {
        margin-right:10px;
    }
    .box2 .item:nth-child(2n+0) {
        margin-right:0px;
    }
}
````


### div边框相互覆盖
````html
<div class="box3 b-clear">
    <div class="item"> 1 </div>
    <div class="item"> 2 </div>
    <div class="item"> 3 </div>
    <div class="item"> 4 </div>
    <div class="item item-on"> 5 </div>
    <div class="item"> 6 </div>
    <div class="item"> 7 </div>
    <div class="item"> 8 </div>
    <div class="item"> 9 </div>  
</div>
````

````css
.box3 {
    width:320px;
}
.box3 .item{
    box-sizing: initial;
    width:100px;
    height:100px;
    border:5px solid yellow;
    margin-right:-5px;
    margin-bottom:-5px;
}
.box3 .item-on{
    border:5px solid red;
    position:relative;
    z-index:10;<!--z-index和position必须一起才有效-->
}
````
