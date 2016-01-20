1秒後に移動します。
<script language="JavaScript">// <![CDATA[
mnt = 1; //秒数
url = "http://socialzukan.com/alchemy/";//移動先
function jumpPage() {
  if(url=="")return;
  location.href = url;
}
setTimeout("jumpPage()",mnt*1000)
// ]]></script>
