# tagsInputaAutoComplete
高配置性的layui input组件，可配置为标签input，autoComplate等等
**文件夹demo.html里有详细操作**


配置属性：
-----

    {
        elem: '#test',//将要渲染元素的id div标签
        inputMode: 'tags',//or text(标签input或普通)
        dropdownMode: 'list',//or group(拉下选择框模式)
        frequency: 0,//input改变触发事件的频率
        tagCloseable: false,//or group(拉下选择框模式)
        tagClickable: true,//标签项是否有删除标签
        autoComplete: true,//是否开启选择框
        autoCompleteData: [],//选择框的数据 通过reload方法可进行autoComplete更新
        backable: true,//标签是否可被退格键删除
        firstActived: false,//选择框是否第一默认选中
        tagsMode: 'append',
        // append || replace || toggle标签重复的如何处理
        dropdownSelectedStatus: true,//下拉框是否拥有选中状态样式
        placeholder: '',//input的placeholder
        listTemplate: '<p>{{d.name}}</p>',//下拉框每一项模板
        groupTemplate: '<p>{{d.name}}</p>',//dropdownMode:'group'有效 分组下拉框标题
        //不常用属性
        tagClassName: '',//为标签添加className
        textAppend: false,//inputMode text时 选择框选择后是否仍追加字符而不是替换
        dropdownonce: true,//dropdownonce为false时dropdown将不会在选择后消失
        keyboard: true,//是否启用键盘上下操作
        maxHeight: '300px',//下拉框最大高度
        width: 100,//数值100则作为百分比 字符串px
        //inputchange:function(val, allVal, event){}
        //其余事件
      }

事件event：
-------

    inputchange: function (val, allVal, event) {
              val = val || 'layUi'
              console.group('inputchange')
              console.log('input变化后的值：', val)//frequency设置频率
              console.log('全部值：', allVal)
              console.groupEnd()
              tagsInputAutoComplete.reload('test2', {
                autoCompleteData: [{ name: val + val }, { name: val + val + val }]
              })
            },
            backspace: function (val, allVal, event) {
              console.group('backspace')
              console.log('被删除tag的值:', val)
              console.log('全部值：', allVal)
              console.groupEnd()
            },
            enter: function (val, allVal, type, event) {
              console.group('enter')
              console.log('回车时的值：', val) //回车选择标签时不触发
              console.log('类型：', type)
              console.log('全部值：', allVal)
              console.groupEnd()
            },
            tagClose: function (val, allVal, event) {
              console.group('tagClose')
              console.log('被删除tag的值：', val)
              console.groupEnd()
            },
            tagRemove: function (val, allVal, type, event) {
              console.group('tagRemove')
              console.log('类型：', type)
              console.log('被点击tag的值：', val)
              console.log('全部值：', allVal)
              console.groupEnd()
            },
            tagClick: function (val, allVal, event) {
              console.group('tagClick')
              console.log('被点击tag的值：', val)//仅tagCloseable == true 时有效
              console.log('全部值：', allVal)
              console.groupEnd()
            },
            select: function (val, allVal, event) {
              console.group('select')
              console.log('下拉框选择的值：', val)
              console.log('全部值：', allVal)
              console.groupEnd()
            }
方法：
--
    //方法都可以实例调用或者类传id调用
    //reload方法重载 autoCompleteData属性 （groupTemplate，listTemplate）也可以
    tagsInputAutoComplete.reload('test', {
       autoCompleteData: [{ name: val + val }, { name: val + val + val }]
    })
    
    //getInputValue获取input的值。inputMode:tags时返回数组
    tagsInputAutoCompleteIns2 = tagsInputAutoComplete.render(options2);
      console.log('input的值为', tagsInputAutoComplete.getInputValue('test' || '#test'))
      document.getElementById('btn').addEventListener('click', function () {
      console.log(tagsInputAutoCompleteIns2.getInputValue())
    })
![简单小图][1]
![简单小图][2]


  [1]: //cdn.layui.com/upload/2019_3/35386176_1552832364914_86839.png
  [2]: //cdn.layui.com/upload/2019_3/35386176_1552832379594_84337.png