---
layout: post
title: Azure Text Analytics API sample code
---
Microsoft azure has text analytics API. You can use API for free till 10,000 transactions.

To get more information about azure machine learning, visit below.
<a href="https://azure.microsoft.com/en-us/documentation/articles/machine-learning-apps-text-analytics/#api-definition">https://azure.microsoft.com/en-us/documentation/articles/machine-learning-apps-text-analytics/#api-definition</a>
 
<span style="font-size:10px;"><a href="http://www.igosso.net/flk/2978759074.html" target="_blank"><img src="https://farm4.staticflickr.com/3045/2978759074_0979a09252_m.jpg" alt="" /></a><br />Windows Azure / Carlos Gutiérrez G.</span>

Here's sample code .
Send text and get sentiment score.
~~~~
$accountKey = "YOURE APP ID";
$text = "Do you wanna hurt me?";//put your text here.


$url="https://api.datamarket.azure.com/data.ashx/amla/text-analytics/v1/GetSentiment?Text=".urlencode($text); 

try {
$cred = sprintf('Authorization: Basic %s', base64_encode($accountKey . ":" . $accountKey) );
$context = stream_context_create(array( 'http' =&gt; array( 'header' =&gt; $cred ) ));
$response = file_get_contents($url, 0, $context);
$j = json_decode($response);
print "SCORE:".$j-&gt;Score;

}catch(Exception $e){

echo "ERROR".$e-&gt;getMessage();

}
~~~~


If you succeed, you will get JSON below.

 

~~~~
"odata.metadata":"https://api.datamarket.azure.com/data.ashx/amla/text-analytics/v1/$metadata#TextAnalytics.FrontEndService.Models.SentimentResult","Score":0.1094211 } 
~~~~
