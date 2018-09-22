# 价格解密算法示例

## 可以使用的测试数据：

    enckey: ABE53CC1B7FDA2903681192D105A53EC
    sigkey: da2d9026aa90400cbc9c4db053e65b82
    加密价格：ebHrWLBZ_vQ8id_wknHJAw
    实际价格：3500

## PHP

```php

	<?php
	/*-------------------------example------------------------------*/
	$PriceDec = new PriceDec($encKey, $sigKey);
	$price = $PriceDec->decode($enPrice);
	var_dump($price);
	/*-------------------------example------------------------------*/

	class PriceDec
	{

	    protected $encKey;

	    protected $sigKey;

	    public function __construct($encKey, $sigKey)
	    {
	        $this->encKey = hex2bin($encKey);
	        $this->sigKey = hex2bin($sigKey);
	    }

	    public function decode($base64Str)
	    {
	        $data = $this->base64urlDecode($base64Str);
	        if (!$data || strlen($data) != 16) {
	            return false;
	        }
	        
	        $timeMsStamp = substr($data, 0, 4);
	        $encPrice = substr($data, 4, 8);
	        $sig = substr($data, 12, 4);
	        
	        $pad = hex2bin(hash_hmac('sha1', $timeMsStamp, $this->encKey));
	        $decPrice = $this->xorBytes($pad, $encPrice, 8);
	        $price = unpack('d', $decPrice);
	        
	        if (!isset($price[1])) {
	            return false;
	        }
	        
	        $osig = hex2bin(hash_hmac('sha1', $decPrice . $timeMsStamp, $this->sigKey));
	        if ($sig != substr($osig, 0, strlen($sig))) {
	            return false;
	        }
	        
	        return $price[1];
	    }

	    protected function xorBytes($s1, $s2, $length)
	    {
	        $result = "";
	        for ($i = 0; $i < 8; ++ $i) {
	            $result .= chr(ord($s1[$i]) ^ ord($s2[$i]));
	        }
	        
	        return $result;
	    }

	    protected function base64urlDecode($base64Str)
	    {
	        $base64Str = str_replace(array('-','_'), array('+','/'), $base64Str);
	        $base64Len = strlen($base64Str);
	        $pad = 4 - ($base64Len % 4);
	        $pad < 4 && $base64Str = str_pad($base64Str, $base64Len + $pad, "=");
	        
	        return base64_decode($base64Str);
	    }
	}
```

## JAVA

```java

	import java.io.UnsupportedEncodingException;  
	import javax.crypto.Mac;  
	import javax.crypto.spec.SecretKeySpec;
	import java.util.Arrays;
	import java.nio.ByteBuffer;
	import java.util.Base64;  
	import javax.xml.bind.DatatypeConverter;
	import java.math.BigInteger;

	class PriceDec
	{
	    private byte[] encKey;
	    private byte[] sigKey;

	    public void Price()
	    {

	    }

	    public void setEncKey(String encKey)
	    {
	        this.encKey = hex2bin(encKey);
	    }

	    public void setSigKey(String sigKey)
	    {
	        this.sigKey = hex2bin(sigKey);
	    }

	    public double decode(String base64Str)
	    {
	        byte[] temp = base64UrlDecode(base64Str);

	        if (temp.length != 16) {
	            throw new RuntimeException("base64UrlDecode string length less 16"); 
	        }

	        byte[] timeStamp = new byte[4];
	        byte[] encPrice = new byte[8];
	        byte[] sig = new byte[4];
	        
	        timeStamp = Arrays.copyOfRange(temp,0,4);
	        encPrice = Arrays.copyOfRange(temp, 4,12);
	        sig = Arrays.copyOfRange(temp, 12,16);

	        byte[] pad = hex2bin(hmac_sha1(timeStamp, this.encKey));
	        byte[] decPrice = xorBytes(pad, encPrice, 8);

	        double d = byteArrToDouble(decPrice);

	        int i=0;
	        byte[] calByte = new byte[12];
	        for (i=0;i<8;i++) {
	            calByte[i] = decPrice[i];
	        }
	        for (i=0;i<4;i++) {
	            calByte[8+i] = timeStamp[i];
	        }

	        byte[] osig = hex2bin(hmac_sha1(calByte, this.sigKey));
	        byte[] compareSig = Arrays.copyOfRange(osig, 0,4);

	        if (!Arrays.equals(sig, compareSig)) {
	            throw new RuntimeException("sig not equal");
	        }

	        return d;
	    }

	    public byte[] xorBytes(byte[] padStr, byte[] encPrice, int n)
	    {
	        int i;  
	        byte[] retArr = new byte[n];
	        for (i=0;i<n;i++) {
	            retArr[i] = (byte)(padStr[i]^encPrice[i]);
	        }
	        return retArr;
	    }

	    public byte[] base64UrlDecode(String base64Str)
	    {
	        base64Str = base64Str.replaceAll("-", "+");
	        base64Str = base64Str.replaceAll("_", "/");
	        int length = base64Str.length();
	        int pad = 4-(length%4);
	        int i;
	        for (i=0;i<pad;i++) {
	            base64Str += "=";
	        }
	        byte[] bytes = base64Str.getBytes();
	        byte[] decoded = Base64.getDecoder().decode(base64Str);
	        return decoded;
	    }

	    public double byteArrToDouble(byte[] b) {   
	        long l;   
	        l = b[0];   
	        l &= 0xff;   
	        l |= ((long) b[1] << 8);   
	        l &= 0xffff;   
	        l |= ((long) b[2] << 16);   
	        l &= 0xffffff;   
	        l |= ((long) b[3] << 24);   
	        l &= 0xffffffffl;  
	        l |= ((long) b[4] << 32);   
	        l &= 0xffffffffffl;   
	        l |= ((long) b[5] << 40);   
	        l &= 0xffffffffffffl;   
	        l |= ((long) b[6] << 48);   
	        l &= 0xffffffffffffffl;   
	        l |= ((long) b[7] << 56);   
	        return Double.longBitsToDouble(l);  
	    }

	    public byte[] hex2bin(String hex) {
	        char[] hex2char = hex.toCharArray();
	        byte[] bytes = new byte[hex.length() / 2];
	        int temp;
	        for (int i = 0; i < bytes.length; i++) {
	            temp = Character.digit(hex2char[2 * i], 16) * 16;
	            temp += Character.digit(hex2char[2 * i + 1],16);
	            bytes[i] = (byte) (temp & 0xff);
	        }
	        return bytes;
	    }

	    private String hmac_sha1(byte[] value, byte[] key) {  
	        try {  
	            byte[] keyBytes = key;          
	            SecretKeySpec signingKey = new SecretKeySpec(keyBytes, "HmacSHA1");  
	            Mac mac = Mac.getInstance("HmacSHA1");  
	            mac.init(signingKey);  
	            byte[] rawHmac = mac.doFinal(value);  
	            String hexBytes = DatatypeConverter.printHexBinary(rawHmac); 
	            return hexBytes;  
	        } catch (Exception e) {  
	            throw new RuntimeException(e);  
	        }  
	    }  
	}


	/**----------------begin使用范例---------------------**/
	public class pricedec{
	    public static void main(String args[]) {
	        
	        PriceDec p = new PriceDec();
	        p.setEncKey($encKey);
	        p.setSigKey($sigKey);

	        String base64Str = $enPrice;
	        System.out.println(p.decode(base64Str));
	    }
	}
	/**----------------end  使用范例---------------------**/
```

## golang

```go

	package main

	import (
		"bytes"
		"crypto/hmac"
		"crypto/sha1"
		"encoding/base64"
		"encoding/binary"
		"encoding/hex"
		"errors"
		"fmt"
		"strings"
	)

	func main() {
		fmt.Println(Decode("这是dec_key", "这是sig_key", "这是price_enc"))
	}

	func Decode(dec_key, sig_key, price_enc string) (float64, error) {
		data, err := base64url_decode(price_enc)
		if err != nil {
			return 0, err
		}

		if len(data) != 16 {
			return 0, errors.New("Illegal base64 string")
		}

		time_ms_stamp_bytes := data[:4]
		enc_price := data[4:12]
		sig := data[12:16]

		dec_key_bytes := hex2bin(dec_key)

		pad := sha1_hmac(time_ms_stamp_bytes, dec_key_bytes)
		dec_price := xor_bytes(pad, enc_price, 8)

		var price float64

		dec_price_buf := bytes.NewBuffer(dec_price)
		binary.Read(dec_price_buf, binary.LittleEndian, &price)

		//校验
		sig_key_bytes := hex2bin(sig_key)
		osig := sha1_hmac(append(dec_price, time_ms_stamp_bytes...), sig_key_bytes)
		if bytes.Compare(sig, osig[:len(sig)]) == 0 {
			//校验成功
			return price, nil
		}

		return price, errors.New("signature is illegal")
	}

	func xor_bytes(b1, b2 []byte, length int) []byte {
		new_b := make([]byte, length)
		for i := 0; i < length; i++ {
			new_b[i] = b1[i] ^ b2[i]
		}
		return new_b
	}

	func hex2bin(s string) []byte {
		ret, _ := hex.DecodeString(s)
		return ret
	}

	func sha1_hmac(data, key []byte) []byte {
		mac := hmac.New(sha1.New, key)
		mac.Write(data)
		return mac.Sum(nil)
	}

	func base64url_encode(data []byte) string {
		ret := base64.StdEncoding.EncodeToString(data)
		return strings.Map(func(r rune) rune {
			switch r {
			case '+':
				return '-'
			case '/':
				return '_'
			}

			return r
		}, ret)
	}

	func base64url_decode(s string) ([]byte, error) {
		base64Str := strings.Map(func(r rune) rune {
			switch r {
			case '-':
				return '+'
			case '_':
				return '/'
			}

			return r
		}, s)

		if pad := len(base64Str) % 4; pad > 0 {
			base64Str += strings.Repeat("=", 4-pad)
		}

		return base64.StdEncoding.DecodeString(base64Str)
	}
```

## C#

```c

	using System;
	using System.Linq; 
	using System.Security.Cryptography;

	class demo
	{
		public static void Main(string[] args)
		{
			PriceDec a = new PriceDec();    
			Console.WriteLine(a.decode($encKey,$sigKey,$enPrice));
			Console.ReadKey(true);
		}
	}
		
	public class PriceDec
	{
		
		public double decode(string enc_key, string sig_key, string price)
		{
			byte[] data = this.base64UrlDecode(price);
			if (data==null|| data.Length != 16)
			{
				throw new ArgumentException("The price is not a valid string");
			}
			
			byte[] encKey = hex2Bin(enc_key);
			byte[] sigKye = hex2Bin(sig_key);
			
			byte[] timeMsStamp = data.Take(4).ToArray();
			byte[] encPrice = data.Skip(4).Take(8).ToArray();
			byte[] sig = data.Skip(12).Take(4).ToArray();
			
			byte[] pad = hash_hmac(timeMsStamp, encKey);
			byte[] dec_price= xorBytes(pad, encPrice, 8);

			byte[] osigData = new byte[dec_price.Length + timeMsStamp.Length];
			dec_price.CopyTo(osigData,0);
			timeMsStamp.CopyTo(osigData, dec_price.Length);
			byte[] osig = hash_hmac(osigData, sigKye);
			
			if(!sig.SequenceEqual(osig.Take(4).ToArray())){
				throw new ArgumentException("The price is not a complete string");
			}
			
			return BitConverter.ToDouble(dec_price, 0);
		}
		
		private byte[] hex2Bin(string hexdata)
		{
			if (hexdata == null)
				throw new ArgumentNullException("hexdata");
			if (hexdata.Length % 2 != 0)
				throw new ArgumentException("hexdata should have even length");

			byte[] bytes = new byte[hexdata.Length / 2];
			for (int i = 0; i < hexdata.Length; i += 2)
				bytes[i / 2] = (byte)(HexValue(hexdata[i]) * 0x10
				                      + HexValue(hexdata[i + 1]));
			return bytes;
		}

		static int HexValue(char c)
		{
			int ch = (int)c;
			if (ch >= (int)'0' && ch <= (int)'9')
				return ch - (int)'0';
			if (ch >= (int)'a' && ch <= (int)'f')
				return ch - (int)'a' + 10;
			if (ch >= (int)'A' && ch <= (int)'F')
				return ch - (int)'A' + 10;
			throw new ArgumentException("Not a hexadecimal digit.");
		}


		private byte[] hash_hmac(byte[] signatureString, byte[] secretKey, bool raw_output = false)
		{
			HMACSHA1 hmac = new HMACSHA1(secretKey);
			hmac.ComputeHash(signatureString);
			return hmac.Hash;
		}

		protected byte[] xorBytes(byte[] s1, byte[] s2, int length)
		{
			byte[] result = new byte[length];
			for (int i = 0; i < length; i++)
			{
				result[i] = Convert.ToByte((int)s1[i] ^  (int)s2[i]);
			}
			return result;
		}

		protected byte[] base64UrlDecode(string base64Str)
		{
			base64Str = base64Str.Replace("-", "+");
			base64Str = base64Str.Replace("_", "/");
			int base64Len = base64Str.Length;
			int pad = 4 - (base64Len % 4);
			if (pad < 4) base64Str = base64Str.PadRight(base64Len + pad, '=');
			return Convert.FromBase64String(base64Str);
		}
	}
```
