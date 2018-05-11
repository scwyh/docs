# PHPExcel bug

位置：vendor/phpoffice/phpexcel/Classes/PHPExcel/Writer/Excel5/Worksheet.php:

类：class PHPExcel_Writer_Excel5_Worksheet extends PHPExcel_Writer_Excel5_BIFFwriter

2863行：
	$errorStyle = $dataValidation->getType();
改为：
	$errorStyle = $dataValidation->getErrorStyle();
