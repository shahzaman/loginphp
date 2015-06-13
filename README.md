
<?php
session_start();
mysql_connect("localhost", "root", "") or die("mysql connection is failure.");
mysql_select_db("trading") or die("Database does not exists.");
if (isset($_POST['submit'])){
$UserName=mysql_escape_string($_POST['username']);
$Pass_word=mysql_escape_string($_POST['pass_word']);
if (!$_POST['username'] | !$_POST['pass_word'])
 {    
echo ("<SCRIPT LANGUAGE='JavaScript'>
        window.alert('You did not complete all of the required fields')
        window.location.href='Login_panel.php'
        </SCRIPT>");
exit();
     }

$sql= mysql_query("SELECT * FROM user WHERE username = '$UserName' AND password = '$Pass_word'");
if(mysql_num_rows($sql) > 0)
{
	  $_SESSION['login_user']=$UserName; //Initializing Session
	 
echo ("<SCRIPT LANGUAGE='JavaScript'>
        window.alert('Login Succesfully!.')
        window.location.href='profile.php'
        </SCRIPT>");
	
exit();
}
else{
echo ("<SCRIPT LANGUAGE='JavaScript'>
        window.alert('Wrong username password combination.Please re-enter.')
        window.location.href='index.html'
        </SCRIPT>");
exit();
}
}

?>

    
