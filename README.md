- 👋 Hi, I’m <?php
function TemplateLicense($user, $lisensi){
return '


         Lisense (TOOL_PHP)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Author (iewil maestro)
Youtube Channel : youtube.com/@iewil
Telegram Channel: https://t.me/MaksaJoin

Hai, '.$user.'
Your Licensi:
'.$lisensi.'

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Dont forget to subscribe to my YT and join my Telegram channel
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
';
}
function CreateLisensi($txt){
$api_paste_name= urlencode("License");
$api_paste_code= urlencode($txt);
$url 				= 'https://pastebin.com/api/api_post.php';
$ch 				= curl_init($url);
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, 'api_option=paste&api_user_key=&api_paste_private=1&api_paste_name='.$api_paste_name.'&api_paste_expire_date=10M&api_paste_format=php&api_dev_key=krbn97_fY2uyWgaqpsI9nH-N4NRGyiOT&api_paste_code='.$api_paste_code.'');
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_VERBOSE, 0);
curl_setopt($ch, CURLOPT_NOBODY, 0);

$response  			= curl_exec($ch);
$patch = explode('https://pastebin.com/',$response)[1];
return ["url"=>'https://pastebin.com/raw/',"patch"=>$patch];
}
function ShortExe($link){
	$long_url = urlencode($link);
	$api_token = '12c11d8a2bd717fc085c92ebaf6ca4424cea7874';
	$api_url = "https://exe.io/api?api={$api_token}&url={$long_url}";
	$result = @json_decode(file_get_contents($api_url),TRUE);
	if($result["shortenedUrl"]){
		return $result["shortenedUrl"];
	}
}
/*
function Licensi($text){
	$url = "https://api.telegram.org/bot".base64_decode("Njg5NTU3NjYwMTpBQUVZQ25TV0xqREhCS2ZjY3ktMWZ0RkdnS0JqbUY1bzc0OA==")."/sendMessage";
	$data = [
		'chat_id' => 'xxx',
		'text' => $text,
		'parse_mode' => 'markdownv2',
		'disable_web_page_preview' => false
	];
	$opts = ['http' =>['method'  => 'POST','header' => ['Content-Type: application/json'],'content' => json_encode($data)]];
	$r = json_decode(file_get_contents($url, false, stream_context_create($opts)),1);
	return $r;
}
function TemplateLicense($usermu, $license){
	$text = "*Welcome @$usermu*\n";
	$text .= "*Lisensi mu sudah siap *\n";
	$api = json_decode(file_get_contents("http://ip-api.com/json"),1);
	if($api){
		$text .= $api['city'].",".$api['regionName'].",".$api['country']."\n";
	}
	$text .= "> *Subscribe*: [iewil official](https://www.youtube.com/c/iewil)\n";
	$text .= "> *Lisensi* : `$license`\n";
	$text .= "```sc_error?🤯\n";
	$text .= ' `git reset --hard`'."\n";
	$text .= ' `git pull````'."\n";
	return $text;
}
*/
$api = json_decode(file_get_contents("http://ip-api.com/json"),1);
if($api){
	$tz = $api["timezone"];
	date_default_timezone_set($tz);
}else{
	date_default_timezone_set("UTC");
}

if(!file_exists("Data/License")){
	$key = md5(date("c"));
	Ban();
	print Error("Ups🤭 Please Activasi first!\n");
	Cetak("Channel","https://t.me/MaksaJoin");
	print line();
	$usermu = readline(Isi("User Telegram (@user)"));
	print line();
	//$greeting = preg_replace("/[^A-Za-z0-9 ]/",'',$usermu);
	$txt = CreateLisensi(TemplateLicense($usermu,$key));
	if(!$txt["patch"])exit(Error("Limit Request!, Change your ip first\n"));
	$link = ShortExe($txt["url"].$txt["patch"]);
	print c."---[ ] Created Link: ".k.date("d/M/Y").m."-".k.date("H:i:s").n;
	$expired = time()+600;
	print m."---[ ] Expired Link: ".k.date("d/M/Y",$expired).m."-".k.date("H:i:s",$expired).n;
	print h."---[ ] Licensi Link: ".k.$link.n;
	$x = readline(Isi("License"));
	print line();
	if($x == $key){
		print Sukses("Terimakasih sudah Menggunakan script saya ");
		sleep(3);
		file_put_contents("Data/License",$key);
	}else{
		print Error("Ups Lisensi yang anda masukkan salah!\n");
		exit;
	}
}
Gidil87
<!---
Gidil87/Gidil87 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
