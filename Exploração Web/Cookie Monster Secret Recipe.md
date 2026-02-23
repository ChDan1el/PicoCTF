# Cookie Monster Secret Recipe

This challenge focuses on web exploration, specifically analyzing [browser cookies](https://www.kaspersky.com.br/resource-center/definitions/cookies)

##### [Challenge link](https://play.picoctf.org/practice/challenge/469)

## Step by Step

After reviewing the challenge description, I began trying to log in with `user=admin` and 
`password=admin`

<img width="815" height="356" alt="image" src="https://github.com/user-attachments/assets/d8acb6b4-f345-4245-93d6-7e642fa01062" />

However, this message provides a hint: **check the cookies**

<img width="640" height="234" alt="image" src="https://github.com/user-attachments/assets/4b43b236-79ad-4d76-a4b3-97dbcac16e23" />

After seeing the hint, I analyzed the browser cookies and I found a cookie encoded in Base64

<img width="1751" height="450" alt="image" src="https://github.com/user-attachments/assets/69a7a5f9-410a-404c-90ad-7b8d0ad352eb" />

**COOKIE:** `cGljb0NURntjMDBrMWVfbTBuc3Rlcl9sMHZlc19jMDBraWVzX0IzQUQ5NEMyfQ==`

I used [CyberChef](https://gchq.github.io/CyberChef/) to decode the value and retrieve the *flag*

<img width="1217" height="510" alt="image" src="https://github.com/user-attachments/assets/fb747746-4b46-4941-9d14-221411510db0" />

## FLAG: picoCTF{c00k1e_m0nster_l0ves_c00kies_B3AD94C2}

### Conclusão:

This challenge is easy but at the same time excenllent for learning, as it teaches us how 
cookies works. It also helps develop logical thinking when dealing with stored data and 
understand how to extract endoded information, in this case, the *flag*.
