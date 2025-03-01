$recaptchaResponse = 'RecaptchaResponse';
$recaptchaSecret = 'RecaptchaSecret';

if (empty($recaptchaResponse)) {
  error_log("Recaptcha response Is Empty")
}

$url = 'https://www.google.com/recaptcha/api/siteverify';
$data = [
'secret' => $recaptchaSecret,
'response' => $recaptchaResponse
];

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
$responseCaptcha = curl_exec($ch);
curl_close($ch);

$responseKeys = json_decode($responseCaptcha, true);
