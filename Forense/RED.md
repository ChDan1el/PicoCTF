# RED

This challenge involves inspecting the metadata of an image to find the *flag*

> Hint: Check whatever Facebook is called now.

##### [Challenge link](https://play.picoctf.org/practice/challenge/460?category=4&page=1)

## Step by Step

After downloading the file, I obtained the following image 

<img width="128" height="128" alt="red" src="https://github.com/user-attachments/assets/ebccbe2b-2fe8-49ac-9ffb-97479884160a" />

Using the challenge hint, I analyzed the image with [AperiSolve](https://www.aperisolve.com/) and discovered a Base64-encoded string in the Zteg tool output

<img width="1676" height="508" alt="image" src="https://github.com/user-attachments/assets/120eacda-ecc1-4630-9950-67e40423306f" />

String in base64: `cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==`

After that, I decoded the string using [CyberChef](https://gchq.github.io/CyberChef/) to obtain the *flag*

<img width="1221" height="539" alt="image" src="https://github.com/user-attachments/assets/5893cdca-4eab-48a7-b600-347f97a4185a" />

## FLAG: picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}

### Conclusion

This challenge is simple but effective in demonstrating how hidden information can be stored 
withing image metada. It reinforces the importance of analyzing the file structes and using 
forensic tools to uncover encoded data
