# oc-jwt
OctoberCMS plugin for JWT encryption the decryption

A simple library to encode and decode JSON Web Tokens (JWT) in PHP, conforming to RFC 7519.

<h3>Installation</h3>
<p>Use composer to manage your dependencies and download PHP-JWT Or Dowload plugin directly into
your October project program root:</p>

<code>composer require doninyangm/oc-jwt</code>

<h2>Example </h2>



<pre>
////Php Script
-----
-----
-----
use InyangAndino\Classes\OcJwt;

$key = "example_key";
$token = array(
    "iss" => "http://example.org",
    "aud" => "http://example.com",
    "iat" => 1356999524,
    "nbf" => 1357000000
);

/**
 * IMPORTANT:
 * You must specify supported algorithms for your application. See
 * https://tools.ietf.org/html/draft-ietf-jose-json-web-algorithms-40
 * for a list of spec-compliant algorithms.
 */
$jwt = OcJwt::encode($token, $key);
$decoded = OcJwt::decode($jwt, $key, array('HS256'));

print_r($decoded);

/*
 NOTE: This will now be an object instead of an associative array. To get
 an associative array, you will need to cast it as such:
*/

$decoded_array = (array) $decoded;

/**
 * You can add a leeway to account for when there is a clock skew times between
 * the signing and verifying servers. It is recommended that this leeway should
 * not be bigger than a few minutes.
 *
 */
OcJwt::$leeway = 60; // $leeway in seconds
$decoded = OcJwt::decode($jwt, $key, array('HS256'));

?>
</pre>
