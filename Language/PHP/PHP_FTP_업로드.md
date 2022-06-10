```
// 이미지 가져오기

$extension = explode( ".", $_FILES['img']['name']);

$extension = strtolower( $extension[ count( $extension ) - 1 ] );

$filename = md5(microtime().rand( 0, 9999 ));

$random_filename = 'img_'.$filename.'.'.$extension;

$root = '/var/www/html/homePage/sources/'.$random_filename;


// 연동할 FTP 정보 설정

$host="";

$port="";

$ftp_id="";

$ftp_pw="";

$ftp_file = '';


// FTP 연결

$ftp = ftp_connect($host, $port);

// FTP 로그인

ftp_login($ftp, $ftp_id, $ftp_pw);


// FTP 패시브 연결 설정

// 패시브모드를 사용하지 않을 경우 20번 포트를 사용하지 못해서 504에러가 날 수 있다.

ftp_pasv($ftp, true);


// 해당 서버의 경로 폴더로 이동

if (!@ftp_chdir($ftp, $ftp_file)) {

	// 없다면 생성

	ftp_mkdir($ftp,$ftp_file);

	// 생성 후 이동

	ftp_chdir($ftp,$ftp_file);

}


// 해당 경로에 이미지 업로드

ftp_put($ftp, $random_filename, $_FILES['img']['tmp_name'], FTP_BINARY);


// FTP 닫기

ftp_close($ftp);
```