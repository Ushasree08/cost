<?php
//echo"Creation of scam data base<br>";
//echo"..................<br>";
$servername="localhost";
$username="root";
$password="";
$dbname="scam";
$conn=mysqli_connect($servername,$username,$password,$dbname);
if(!$conn)
{
die("connection failed: ".mysqli_connect_error());
}
else
{
//echo".............";
$board=$_REQUEST['board'];
$dest=$_REQUEST['dest'];
$mode=$_REQUEST['mode'];
$sql="insert into booktrip(board,dest,mode)values('$board','$dest','$mode')";
if(mysqli_query($conn,$sql))
{
	echo"<BR><BR><center><b><big> Your cost details are:</big> <b></center>";
	echo"<BR>";
}
}
$sql2="SELECT cost,tot_cost FROM booktrip AS b,cost AS c WHERE b.board=c.board AND b.dest=c.dest AND b.mode=c.mode ";
if($result=mysqli_query($conn,$sql2))
{
	while($row=mysqli_fetch_assoc($result))
	{
		echo "<tr>";
		echo "<center>";
		//echo <td>".$row['cost']."</td>;
		//echo <td>".$row['tot_cost']."</td>;
        print_r($row);
        echo "</center>";		
		echo"<br>";
	}
	mysqli_free_result($result);
}
?>
<html>
<head><title>Existing</title>
<style>
body{
background-image:url("world.jpg");
background-repeat:no repeat;
}
</style>
</head>
<body>
</br>
</br></br><center>
<a href="final.php" target="_self"><input type="Button" value="Book"></a>
<a href="scam.php" target="_self"><input type="Button" value="Cancel"></a>
</center></body>
</html>
