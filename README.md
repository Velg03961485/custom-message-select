# custom-message-select
you custom message select by yourself custom 

当你需要对或许的信息 进行选择填入的时候，就需要一个选择器插件了

如果你看多日期选择插件，你就会了解到，这是从日期插件演变过来的

一种自定义信息选择插件

引入外部文件
<link rel="stylesheet" href="/js/select/mobileSelect.css" type="text/css"/>
<link rel="stylesheet" href="/js/select/public.css" type="text/css"/>

<script type="text/javascript" src="/js/select/mobileSelect.js"></script>


<div class="textBox-verification" >
	<div class="phne-name">门店</div>
	<div class="userName">
		<!--请选择门店-->
		<div  class="select userInput"   id="storeModel" >请选择门店</div>
	</div>
</div>


$.ajax({
        type: "POST",
        url: "/web/depart/getChildrenStore",
        success:function(data){

            for(var i=0;i<data.length;i++){
                parm.push({
                    'id':data[i].id,
                    'value':data[i].name
                })
            }
            //门店选择
            var weekdayArr=parm;
            var mobileSelect1 = new MobileSelect({
                trigger: '#storeModel',
                title: '请选择',
                wheels: [
                    {data: weekdayArr}
                ],
                position:[0], //初始化定位 打开时默认选中的哪个  如果不填默认为0
                transitionEnd:function(indexArr, data){
//            console.log(data);
                },
                callback:function(indexArr, data){
                    id=data[0].id;
                    $('.select').css('color','black');
                }
            });
        },
        error:function(data){

        }
    })
	
这个插件对数据的格式 有严格的要求，你可从获取的数据中，把数据再重新调整一遍，然后传入到插件里面

同时，你也可以在 callback 函数里面掉连贯筛选（比如选取 省市级县）
