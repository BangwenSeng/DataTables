# DataTables
DataTables的使用配置
<h2>DataTables常用</h2>
<pre><code>     &quot;iDisplayLength&quot;:20, //默认显示的记录数  
     &quot;bPaginite&quot;: true,
     &quot;bInfo&quot;: true,
     &quot;bLengthChange&quot;: false,   //去掉每页显示多少条数据方法
     &quot;bSort&quot;: true,
     &quot;bFilter&quot;: true,//去处搜索框
     &quot;columnDefs&quot;:[{
　　　　'targets' : [0,1],    //除第0，第1两列外，都默认不排序
　　　　'orderable' : false  //其他不排序
       &quot;bStateSave&quot;: true,//保存状态
       &quot;stateSaveParams&quot;: function (settings, data) {
        data.search.search = &quot;&quot;;   搜索条件不报存
       data.columns= &quot;&quot;;  分页条件不保存
      data.order= &quot;&quot;;  排序条件不保存
      console.log(data);
</code></pre>

<h3>服务器模式下的排序</h3>
<pre><code>    $new_array = array();

    foreach($Array as $value){

        $new_array[]=$value[$iSortCol_0];

     }
    if($iDisplayOrder == 'desc'){

          array_multisort($new_array, SORT_DESC, $Array);

    }else{

        array_multisort($new_array, SORT_ASC, $Array);

    }

    $json_data = array ('sEcho'=&gt;$sEcho,'iTotalRecords'=&gt;$count,
    'iTotalDisplayRecords'=&gt;$count,'aaData'=&gt;$Array,'ever'=&gt;$allvip, 'pre'=&gt;$allpre); 
     //按照datatable的当前页和每页长度返回json数据

    $obj=json_encode($json_data);

    echo $obj; 
</code></pre>

<h3>服务器模式下的重新渲染表格</h3>
<pre><code>    table.draw();
</code></pre>

