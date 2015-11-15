---
layout: post
title: PHP Sample code:Bing translation API
---
<h2>What's Bing translation API</h2>
Microsoft Bing offers translation API.
WIth it, you can translate English text into Japanese, or Japanese text into English.
Translations is not perfect, but not bad.

You can use 2,000,000 chars for free per one month.

Here's official API site. 
<a href="https://datamarket.azure.com/dataset/bing/microsofttranslator">https://datamarket.azure.com/dataset/bing/microsofttranslator </a>

<span style="font-size:10px;"><a href="http://www.igosso.net/flk/4456608222.html" target="_blank"><img src="https://farm3.staticflickr.com/2781/4456608222_01e0186ed6_m.jpg" alt="" /></a><br />Bing logo redesign / andymangold</span>

 
~~~~
print htmlBingTrans("free","en","ja");

function htmlBingTrans($text,$from, $to){
$APPID = "YOUR ID";
if($from=="")$from="en"; 
if($to=="")$to="ja";

$request = 'https://api.datamarket.azure.com/Bing/MicrosoftTranslator/v1/Translate?Text=%27'. urlencode($text).'%27&amp;From=%27'.$from.'%27&amp;To=%27'.$to.'%27';

$cred = sprintf('Authorization: Basic %s', base64_encode($APPID . ":" . $APPID) );
$context = stream_context_create(array( 'http' =&gt; array( 'header' =&gt; $cred ) ));
$response = file_get_contents($request, 0, $context); //print($response);
$response = explode('', $response); $response = explode('', $response[1]);
return $response[0];
} 
~~~~
 
