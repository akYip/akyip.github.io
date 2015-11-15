---
layout: post
title: Watson Visual Recognition API sample code
---
IBM's Watson API has visual recognition API. With the API, you can detect objects in a photo.

At this moment, <a href="https://gateway.watsonplatform.net/visual-recognition-beta/api/v1/tag/labels">labels</a> are limietd.Not all objects, items are detected via API.


This is an image I used.
<img src="http://o.aolcdn.com/dims/GAME/5/168/168/100/https://spthumbnails.5min.com/10377524/518876164_c_570_411.jpg" alt="" />

Here's sample code.


~~~~
$url="https://gateway.watsonplatform.net/visual-recognition-beta/api/v1/tag/recognize"
$username= "YOURNAME";
$password="YOURPASSWORD";

$data = array(
   'img_file'=&gt;'@map.jpg',//put the name of image file to upload
);

$a = base64_encode($username . ":" . $password);
$o = array(
   'Authorization: Basic ' . $a,
);

$curl = curl_init();
curl_setopt($curl, CURLOPT_HTTPHEADER, $o);
curl_setopt($curl, CURLOPT_POST, true);
curl_setopt($curl, CURLOPT_POSTFIELDS, $data);
curl_setopt($curl, CURLOPT_URL, $url);
curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);
curl_setopt($curl, CURLOPT_SAFE_UPLOAD, true);
curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, false);

$result = curl_exec($curl);
curl_close($curl);

$dat = json_decode($result, true);
print_r($dat);
~~~~


 
If you succeed, results are below.



~~~~
Array ( [images] =&gt; Array ( [0] =&gt; Array ( [image_id] =&gt; 0 [image_name] =&gt; map.jpg [labels] =&gt; Array ( [0] =&gt; Array ( [label_name] =&gt; Indoors [label_score] =&gt; 0.684761 ) [1] =&gt; Array ( [label_name] =&gt; Room [label_score] =&gt; 0.679865 ) [2] =&gt; Array ( [label_name] =&gt; Scene [label_score] =&gt; 0.673028 ) [3] =&gt; Array ( [label_name] =&gt; Human [label_score] =&gt; 0.659111 ) [4] =&gt; Array ( [label_name] =&gt; People View [label_score] =&gt; 0.646733 ) [5] =&gt; Array ( [label_name] =&gt; Group of People [label_score] =&gt; 0.633192 ) [6] =&gt; Array ( [label_name] =&gt; Mixed Color [label_score] =&gt; 0.618089 ) [7] =&gt; Array ( [label_name] =&gt; People Activity [label_score] =&gt; 0.548905 ) ) ) ) )

 ~~~~

 
