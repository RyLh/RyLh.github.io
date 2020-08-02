---
title: 全面查看自己ip
date: 2020-07-13 22:15:54
---
### 本地地址
##### 这是通过WebRTC协议获取的您的内网IP.
<span id="LANIP">内网IP</span>

<script>
               window.RTCPeerConnection = window.RTCPeerConnection || window.mozRTCPeerConnection || window.webkitRTCPeerConnection;   //compatibility for firefox and chrome
               var pc = new RTCPeerConnection({iceServers:[]}), noop = function(){};      
               pc.createDataChannel("");    //create a bogus data channel
               pc.createOffer(pc.setLocalDescription.bind(pc), noop);    // create offer and set local description
               pc.onicecandidate = function(ice){  //listen for candidate events
               if(!ice || !ice.candidate || !ice.candidate.candidate)  return;
                 var myIP = /([0-9]{1,3}(\.[0-9]{1,3}){3}|[a-f0-9]{1,4}(:[a-f0-9]{1,4}){7})/.exec(ice.candidate.candidate)[1];
                     //console.log('my IP: ', myIP);   
                     document.getElementById("LANIP").textContent=myIP;
                     pc.onicecandidate = noop;
                    };
</script>



### 国内网站
##### 如果没有全局代理或者VPN，下方显示的IP就是您本机的IP。如果有，则显示的就是全局代理或者VPN的IP地址。
<iframe src="https://myip.ipip.net" width="100%" height="40" scrolling="no" frameborder="0" marginheight="0" marginwidth="0"> </iframe>



### 国外网站
##### 下面的IP就是您用来访问国外普通网站的IP。
 <iframe src="https://api-ipv4.ip.sb/ip" width="100%" height="30" scrolling="no" frameborder="0" marginheight="0" marginwidth="0"> </iframe>



### 谷歌网站
##### 下方如果没有显示一个IP地址，则说明您现在还不能访问谷歌等国外网站。显示IP则表示可以富强上网，这个地址就是您用来富强上网的IP地址。
 <iframe src="https://ipv4.appspot.com/" width="100%" height="30" scrolling="no" frameborder="0" marginheight="0" marginwidth="0"> </iframe>