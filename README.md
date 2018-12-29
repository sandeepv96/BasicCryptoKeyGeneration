# BasicCryptoKeyGeneration

/****************************************/
/*Public Key generation from Private Key*/
/****************************************/
Note :  No nonce is assumed
//! Key Generation

Input :  16 byte Private Key
Output:  16 byte Public Key

//! Input 16 byte string
    "ABCDEFGHIJKLMNOP"

//! Convert equalent ASCII code of 16 byte string
	65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 89

//! Substract 16 from Ascii byte number substraction to generate - Shifted 16 ASCII string
     for each byte from 16 byte ASCII String
	     substract 16 from ASCII code
		
	65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 89
	- 16 ASCII
	===============================================
	49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64
	===============================================

//! Group Shifted 15 ASCII string into 4 byte  

     (49 50 51 52) (53 54 55 56) (57 58 59 60) (61 62 63 64)
	 
//! Swap the sets of 4 bytes

     (53 54 55 56) (49 50 51 52) (61 62 63 64) (57 58 59 60)
	 
//! Substract 8 from Ascii byte number substraction to generate - Shifted 8 ASCII string
     for each byte from 8 byte ASCII String
	     substract 8 from ASCII code
		 
     (53 54 55 56) (49 50 51 52) (61 62 63 64) (57 58 59 60)
	 - 8 ASCII
	 =======================================================
	 (45 46 47 48) (41 42 43 44) (53 54 55 56) (49 59 51 52)
	 =======================================================
	 
//! Group Shifted 8 ASCII string into 8 byte sets
   
     ((45 46 47 48) (41 42 43 44))  ((53 54 55 56) (49 59 51 52))
	 
//! Swap the sets of 8 bytes

     ((53 54 55 56) (49 59 51 52)) ((45 46 47 48) (41 42 43 44))
	 
	 
//! Substract 4 from Ascii byte number substraction to generate - Shifted 4 ASCII string
     for each byte from 4 byte ASCII String
	     substract 4 from ASCII code
		 
	 ((53 54 55 56) (49 59 51 52)) ((45 46 47 48) (41 42 43 44))
	 - 4 ASCII
	 ===========================================================
	 ((49 50 51 52) (45 46 47 48)) ((41 42 43 44) (37 38 39 40))
	 ===========================================================
	 
	 
//! Shifted 4 ASCII string is a Final Key
      49 50 51 52 45 46 47 48 41 42 43 44 37 38 39 40
	  
//! Convert the ASCII string to the the character string
      "1234-./0)*+,%&'("
	  
//! Output will be Public Key 

/****************************************/
/*Private Key generation from Public Key*/
/****************************************/
Input :  16 byte Public Key
Output:  16 byte Private Key


//! Input 16 byte Public Key string
      "1234-./0)*+,%&'("
	  
//! Convert equalent ASCII code of 16 byte string
      49 50 51 52 45 46 47 48 41 42 43 44 37 38 39 40

//! Add 4 from Ascii byte number substraction to generate - Shifted 4 ASCII string
     for each byte from 4 byte ASCII String
	     add 4 to ASCII code
		 
	 49 50 51 52 45 46 47 48 41 42 43 44 37 38 39 40
	 + 4 ASCII
	 ===============================================
	 53 54 55 56 49 59 51 52 45 46 47 48 41 42 43 44
	 ===============================================
	 
//! Group Shifted 8 ASCII string into 8 byte sets

	 (53 54 55 56 49 59 51 52) (45 46 47 48 41 42 43 44)
	 	  
//! Swap the sets of 8 bytes

     (45 46 47 48 41 42 43 44)  (53 54 55 56 49 59 51 52)
	 
//! Add 8 from Ascii byte number substraction to generate - Shifted 8 ASCII string
     for each byte from 8 byte ASCII String
	     add 8 from ASCII code
		 
     (45 46 47 48 41 42 43 44) (53 54 55 56 49 59 51 52)
	 + 8 ASCII
	 ===================================================
	 (53 54 55 56 49 50 51 52) (61 62 63 64 57 58 59 60)
	 ===================================================
	 
//! Group Shifted 8 ASCII string into 4 byte  
     
	 ((53 54 55 56) (49 50 51 52))  ((61 62 63 64) (57 58 59 60))
	 
//! Swap the sets of 4 bytes
     ((49 50 51 52) (53 54 55 56))  ((57 58 59 60) (61 62 63 64))
	 
//! Add 16 from Ascii byte number substraction to generate - Shifted 16 ASCII string
     for each byte from 16 byte ASCII String
	     add 16 from ASCII code
	 
	 ((49 50 51 52) (53 54 55 56))  ((57 58 59 60) (61 62 63 64))
	 + 16 ASCII
	 ============================================================
     ((65 66 67 68) (69 70 71 72)) ((73 74 75 76) (77 78 79 89))
	 ============================================================
     
//! Convert equalent ASCII code of 16 byte string

    "ABCDEFGHIJKLMNOP"
	  
//! Output will be private Key
	  
