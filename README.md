# user-Authentication-and-Password-Protection-using-an-Algorithm-ACR

Abstract: 

In general, every web or android based application required security for login. So for that we have to encrypt the password while signup itself,these encrypting the password there are many algorithm but by trail and error method or by using some attacks(man in middle attack etc..,) we can know the password, so in order to reduce attacks we came up with new algorithm to protect the password. Even after getting the password where many of the applications like banking , messaging application uses OTP process. These OTP could also be stolen easily (although it is difficult to do so) but still. So to over come this we came up with modified OTP process that decreases the time and it will be difficult to stole. So here we first we will encrypt the password using algorithm ACR and when user want lo login we go with the modified OTP process.

Keywords : security, encyption, OTP, man in middle   attack.


PROBLEM FLOW:

Firstly user need to sign up, in this process the password will be encrypted and saved in database. so that middle person who are dealing with database works can not view password. If user already exist he can directly skip signup. After submitting the registration page it will be redirected to Login page which contains a field where user need to submit UserId. Based on UserId , here undergoes two processes. 

         1) Password is fetched from database
         2) Phone number is fetched from database

Password that is fetched is decrypted to undergo validation OTP(Random Generation) will be send to registered phone number including format of password entry which is decided randomly.(eg XXXXOTP or OTPXXXX).If message is XXXXOTP the password field should contain password followed by OTP(concated). If message is OTPXXXX the password field should conatin OTP followed by password.

Finally ,Validation is done to authorize the user.


Encryption Process for ACR   

    i. The password given by the user will be saved in database in encrypted manner. A huge set of characters will be intialized in an array.
    ii. Initially a space value will be generated.
    iii. Each two characters of the password will be inserted with randomly generated characters acoording to the sapce value.
    iv. Now the total number of characters will serve as a base value or a key. Each character present in the password will be multiplied with base value.
    v. Now the multiplied value will be divided into two factors and the index charcter will be fetched from array using the two factors .
    vi. Now the character before multiplication will be repled with those two characters (i.e factors)and this process will be repeated for whole password.
    vii. Now the index charcater of the base value will be appended to the modified password and it is saved in the database.



Decryption process for ACR

    i. The password that is saved in the database will be fetched The same array used in encryption is used here.
    ii. Array index value of last character present in password will be fetched.
    iii. Now two consecutive character of paasword will be multiplied (index values are taken from array)
    iv. Now the multiplied value will be divided with the base value
    v. The output value is used to fetch the characater from the array which is replaced with those two characters.
    vi. Finally the last character will be deleted from the string(i.e Base value will be deleted)
      Fig 3 . Architecture for Decryption of ACR
           


Steps involved in this process

Step -1: Registration phase
User has to signup first,while submitting the signup formthe password will be encrypted and stored in the database.



Step -2:Login Page
After the registration, when the user try to login first he has
to submit User id. Then user get the OTP, the OTP will be in form of OTPXXXX or XXXXOTP.



Step -3:OTP Received to mobile with format

    i. If the OTP is like “OTPXXXX” then user password will be OTP folloed by Password.
    ii. If the OTP is like “XXXXOTP” then user password will be password followed by OTP.
                     
Step -4:Entering the password

 If the correct credentials are entered we will get

The array used for encryption and decryption

String option[]= {"$","1","2","3","4","5","6","7","8","9","0","A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T","U","V","W","X","Y","Z","@","a","b","c","d","e","f","g","h","i","j","k","l","m","n","o","p","q","r","s","t","u","v","w","x","y","z","#","*","!","%","^","&","(",")","_","-","+","=","~","?","/","[","]","{","}","|","`",":",";",",",".","<"};

RESULT AND DISCUSSION

To implement the ACR algorithm we have used Netbeans (java) and mysql for the database.few inputs and outputs are mention below.

The space value is chosen randomly, so password length varies every time. For example if we take password as “ara@210” the length of password is seven and space value(random number) is 2.Now in between two characters two random values(based on space value) from array will be selected and placed then the password size is 19. Then each character is divided into two character,now length becomes 38 and in password we insert space value and length of the password as this data will be used for the decryption of the password.

CONCLUSION

The proposed ACR algorithm will improve the security for the login authentication. As we used randam space value, as password size increases the encrypted size also  increases which results to providing more security to the password. In this paper we proposed random OTP process which protect from the attacks. As the OTP and Password  concatination will be in two ways which will be randomly given to user, according to that the password varies every time user login and every time user login the password will be different as we add OTP to the password.
