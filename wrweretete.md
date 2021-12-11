<?php
	if(isset($_POST['btnadd'])){
		$data = file_get_contents('users.json');
		$data = json_decode($data, true);
		$add_arr = array(
			'first_name' => $_POST['txtFname'],
			'last_name' => $_POST['txtLname'],
			'address' => $_POST['txtAddress'],
			'email' => $_POST['txtEmail'],
			'mobile' => $_POST['txtMobile']
		);
		
		$my_file = $_POST['txtFname'];
		$data[] = $add_arr;

		$data = json_encode($data, JSON_PRETTY_PRINT);
		file_put_contents('users.json', $data);
 
		header('location: index.php');
		
		
        $handle = fopen($my_file, 'a') or die('Cannot open file:  '.$my_file);
       fwrite($handle, $data);
	}
?>