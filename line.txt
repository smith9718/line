<?php
  
function send_LINE($msg){
 $access_token = '45nis0kjrGYqQ6Bsx4rK/RO4dTI4vRRy13FDI493RAfE1YwMDeHaxNHiV/VfxPf/lgHEK9RAW/G1hiSWE390jToDoZLe10ev8MbkuStt92M4ThhZPZt0NGXS5/FUUr42gwRm5lpaRHyx0IgcfxdEsgdB04t89/1O/w1cDnyilFU='; 
  $messages = [
        'type' => 'text',
        'text' => $msg
        //'text' => $text
      ];
      // Make a POST Request to Messaging API to reply to sender
      $url = 'https://api.line.me/v2/bot/message/push';
      $data = [
        'to' => 'e7a2d29562687e61f4e6b944b6d8860e',
        'messages' => [$messages],
      ];
      $post = json_encode($data);
      $headers = array('Content-Type: application/json', 'Authorization: Bearer ' . $access_token);
      $ch = curl_init($url);
      curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "POST");
      curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
      curl_setopt($ch, CURLOPT_POSTFIELDS, $post);
      curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
      curl_setopt($ch, CURLOPT_FOLLOWLOCATION, 1);
      $result = curl_exec($ch);
      curl_close($ch);
      echo $result . "\r\n"; 
}
?>