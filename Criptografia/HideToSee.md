# HideToSee

This challenge is about substitution cryptography, more specifically the Atbash cipher

> Hint: Download the image and try to extract it.

##### [Challenge link](https://play.picoctf.org/practice/challenge/351?category=2&page=2)

## Step by Step

After dowloading the file, I obtained the following image

![atbash](https://github.com/user-attachments/assets/e7aff0fe-ccf2-4799-b8c9-52b5200a5e41)

Using the hint from the challenge description, I used [AperiSolve](https://www.aperisolve.com/) 
to extract hidden data from the image

AperiSolve found a file, "encrypted.txt", using *Steghide* tool

<img width="689" height="350" alt="image" src="https://github.com/user-attachments/assets/7ecf42e6-2380-4910-bec1-35a5cdf0fdcc" />

After downloading this file, I obtained the *flag* encrypted with the Atbash cipher:

`krxlXGU{zgyzhs_xizxp_05y2z65z}`

Using the first image from the decryption process, we have:

k -> p

r -> i

x -> c

l -> o

X -> C

G -> T

U -> F

...

etc.

Special characters and numbers remain the same, such as "_"

After decrypting the string, I obtained the *flag*

## FLAG: picoCTF{atbash_crack_05b2a65a}

### Conclusion

This challenge is simple, but it effectively combines cryptography and digital forensics 
concepts. It demonstrates how hidden data can be extracted from images and how substitution 
ciphers can be used to obscure information.
