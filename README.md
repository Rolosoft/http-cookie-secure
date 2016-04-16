# HTTP Cookie (Secure)
__Encrypted, tamper proof cookies for .NET / IIS__

[![rolosoft_public_packages MyGet Build Status](https://www.myget.org/BuildSource/Badge/rolosoft_public_packages?identifier=f667e8af-7fd1-4f91-8044-8c23c66d2e6d)](https://www.myget.org/)

## Overview
Server side software for software running on IIS.

## Features and Benefits
* __encryption and decryption of HTTP cookies.__.
* __provides protection against manual cookie tampering.__ 

## Who Is This For?
This component is for anyone that needs to dump a cookie on a client device that is secure from prying eyes or tampering.

## Installation
From [Nuget].
```
Install-Package Rsft.HttpCookieSecure
```

## Quickstart

### Encode

```c#
string myValueToStoreInCookie = "My details";

/*Create a "standard" (unencrypted) HttpCookie*/ 
HttpCookie myCookie = new HttpCookie("MyCookieName",myValueToStoreInCookie);

/*encrypt the "standard" cookie*/ 
HttpCookie myEncodedCookie = CookieSecure.Encode(myCookie);

/*Add the encoded cookie to the response stream.*/ 
Page.Response.AppendCookie(myEncodedCookie);
```

### Decode
```c#
HttpCookie standardCookie = Request.Cookies["MyCookieName"]; 

if(standardCookie!=null) { 
	HttpCookie decodedCookie = CookieSecure.Decode(standardCookie,System.Web.Security.CookieProtection.Encryption); 

    /* ...Go on to process decoded cookie*/ 

}
```