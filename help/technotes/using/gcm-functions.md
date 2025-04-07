---
product: campaign
title: New GCM based functions
description: New GCM based functions
feature: Technote
---
# GCM based functions {#new-functions}
 
To improve security, we have deprecated the use of the AES (Advanced Encryption Standard) algorithm with CBC (Cipher Block Chaining) mode for cryptographic operations. New encryption functions have been introduced. These functions use AES with Galois/Counter Mode (AES-GCM), providing a more secure alternative. These functions are available in JavaScript, JSP, SOAP APIs, and XML schemas, allowing customers to transition from CBC to GCM for encryption and decryption.

This documentation lists the newly introduced AES-GCM functions and the CBC-based functions that are being deprecated. 

New functions: 

* [EncryptString API function](#encryptString-api-xtk)
* [EncryptStringWithServerPassword API funtion](#EncryptStringWithServerPassword-api-xtk)
* [encryptString javascript function](#encryptString-javascript)

Legacy functions that can be used for GCM:

* [DecryptString javascript function](#decryptString-javascript)
* [DecryptPassword javascript function](#decryptPassword-javascript)

[Deprecated functions](#depracated-functions)

## API functions

### EncryptString {#encryptString-api-xtk}

Encrypts the character string with the instance key using AES algorithm with GCM Mode. 

```

            String 
            encrypted = Encrypt (
            String       
            decrypted
            

      )
         
```

**Parameters**: Decrypted text

**Return value(s)**: encrypted

**Schema**: xtk:session 

**Static**: Yes 

## EncryptStringWithServerPassword {#EncryptStringWithServerPassword-api-xtk}

Encrypts the character string with the server key using AES algorithm with GCM Mode. 

 
```

            String 
            encrypted = EncryptStringWithServerPassword (
            String       
            decrypted
            

      )
         
```

**Parameters**: Decrypted

**Return value(s)**: encrypted

**Schema**: xtk:session 

**Static**: Yes 

## Javascript functions

### encryptString() {#encryptString-javascript}

Encrypts a string of characters with the key of the instance or any other key.

```

            cryptString (str [, key
      ] [, useSalt ])
         
```

**Parameters**: 

* str: The character string to encrypt. 
* key: The AES encryption key is encoded in base 64: 256 bits if key length is 32; 192 bits if the key length is 24; 128 bits if the key length is 16 or if no key is specified.
* useSalt: Use a salt of the data to encrypt. True by default. 

**Return value**: Returns the encrypted character string.

**Remarks**

Encryption takes place according to the following method: 

* The unicode character string is transformed into a UTF-8 string. 
* A check character is added in cipher text at the end.
* This string is encrypted using the AES algorithm in Galois/Counter Mode (GCM) mode using salt with a 12 bytes initialization vector and 16 bytes tag. If no key is provided as a parameter, the instance key is used.
* Cipher text will contain the tag and initialization vector. 
* The encrypted block is then converted into base 64. 

Decryption is carried out using the decryptString function. 

**Features**

Available in:

* Content management 
* Delivery properties 
* Delivery message 
* Typology rule 
* Import 
* JSSP 
* SOAP Method 
* WebApp 
* Workflow

### decryptString() {#decryptString-javascript}

Encrypts a string of characters with the key of the instance or any other key. This legacy function can be used with GCM. It is deprecated for decryption of cipher text that is encrypted using AES-CBC mode.

```

            decryptString (str [, key
      ] [, useSalt ])
         
```

**Parameters**: 

* str: The character string to decrypt. 
* key: The AES encryption key is encoded in base 64: 256 bits if key length is 32; 192 bits if the key length is 24; 128 bits if the key length is 16 or if no key is specified.
* useSalt: Use a salt of the data to decrypt. True by default. 

**Return value**: Returns the decrypted character string.

**Warning**: Passwords stored in the database (options / external accounts) cannot be decrypted anymore by the use of this method. For that, use [decryptPassword](#decryptPassword-javascript).

### decryptPassword() {#decryptPassword-javascript}

Decrypts a password stored in an external account. This legacy function can be used with GCM. It is deprecated for decryption of cipher text that is encrypted using AES-CBC mode.

```

            decryptPassword (str)
         
```

**Parameters**: 

* str: The character string to decrypt. 

**Return value**: Returns the plain-text password.

**Remarks**

This function cannot be called in workflows, web applications, reports or deliveries. It can be called in JSSP or SOAP call implementations. Example:

```

        function nms_extAccount_LogonToRemoteInstance(remoteInstanceUrl, login, encryptedPassword) {
        var cnx = null, sessionService = null;
        try
            {
                var cnx = new HttpSoapConnection(remoteInstanceUrl + '/nl/jsp/soaprouter.jsp', 'utf-8', 0);
                sessionService = new SoapService(cnx, 'xtk:session');
                sessionService.addMethod("Logon", "xtk:session#Logon",
                    ["token", "string", "login", "string", "password", "string", "parameters", "NLElement"],
                    ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
                return sessionService.Logon("", login, decryptPassword(encryptedPassword), <parameters/>);
            }
        catch( e ) {
        logError(e);
        }
        finally {
        if( sessionService ) sessionService.dispose();
        if( cnx ) cnx.dispose();
        }
        })
      
```

## Deprecated functions {#depracated-functions}

The following functions are fully deprecated: 

* cryptString
* Encrypt
* EncryptServerPassword
