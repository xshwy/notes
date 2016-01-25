控制台调试输出 `console.log();`

获取radio被选中的值`$("input[name='rate-control']:checked").val()`

判断checkbox是否被选中`$("#annoy").is(':checked')`

修改元素的css样式`$('#progress_bar').css("width", "100%");`

隐藏、显示元素`$('#process').hide();` `$('#process').show();`

获取JS方法的参数 `arguments[0]`

刷新当前页面 `location.reload()`

定时器 间隔指定的毫秒数不停地执行指定的代码 `setInterval("alert(123)",1000)`

间隔指定的毫秒数不停地执行指定的代码 `setTimeout("alert(123)",1000)`

AJAX同步设置
```javascript
$.ajaxSetup({
    async: false
});
```

AJAS POST提交
```javascript
$.post(getStudentInfoUrl, {
    student_id: student_id,
    teacher_id: teacher_id
}, function (data, textStatus) {
    students = data;
});
```

转换JSON `$.parseJSON(students);`

循环
```javascript
$.each(students, function (i, val) {
    console.log(val);
});
```
