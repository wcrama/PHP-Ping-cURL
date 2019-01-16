# PHP-Ping-cURL

<html>
<head>
</head>
<body>
    
<!-- Simple Ping Method IP/Domain -->    
    
<?php
$hostname = "172.217.20.110";    
$command = exec("ping -c 1 ".$hostname);
if ($result == 0){
  echo "ping succeeded"." ".$hostname."<br>";
}else{
  echo "ping failed"." "."<br>";
}
?>   

    
<!-- cURL Method (DomainName Only) -->
<?php

$url = 'google.com';
$ch = curl_init($url);
curl_setopt($ch, CURLOPT_TIMEOUT, 5);
curl_setopt($ch, CURLOPT_CONNECTTIMEOUT, 5);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
$data = curl_exec($ch);
$httpcode = curl_getinfo($ch, CURLINFO_HTTP_CODE);
curl_close($ch);
if($httpcode>=200 && $httpcode<300){
  echo $httpcode." ".'ONLINE'." "."<br>";
  
} else {
  echo $httpcode." ".'OFFLINE'." "."<br>";
}

?>

</body>
</html>
