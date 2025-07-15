# GDPR Data Theft

For this challenge, I started the Kali VM to launch the OWASP Juice Shop application.

![Kali VM](imgs/gdpr_kali_vm.png)

With the VM active, I started the OWASP Juice Shop and the `ZAP` tool. The `ZAP` tool will be used as a penetration testing tool to find vulnerabilities in web applications.

![Start Juice Shop and ZAP](imgs/gdpr_start_app_zarp.png)

Once the proxy tool started, I opened the browser from the `ZAP` tool. In the newly opened browser, I entered the URL from the Juice Shop in the search bar.

```
http://localhost:3000
```

![Launch browser from ZAP](imgs/gdpr_brwser_lauch.png)

![Localhost](imgs/juice_sh_localhost.png)

Next, I logged in as an existing user, in this case as `bender@juice-shop.op` (attack target), to make some product orders and inspect the requests to the server.

I went to `http://localhost:3000/#/login` and in the email field I typed the following:

```
bender@juice-shop.op' OR email = 'bender@juice-shop.op' --
```

I performed an injection here because the Juice Shop page is not protected against it and I don't know the password for `bender`.

After the login, I went to `http://localhost:3000/#/basket` and completed the purchase of the item that was already in the shopping basket.

![Bender's basket](imgs/bender_basket.png)

![Bender's complete order](imgs/complete_order.png)

With the completed order, I went back to `ZAP` and inspected the complete order request. I could see a `GET` request `http://localhost:3000/rest/track-order/<order_number>` with the following response payload:

![Order response](imgs/complete_order_res.png)

The response shows the user `email` with the vowels substituted with `*` before storing the order in the database. The `orderId` is also available in the payload and can be used as a reference when retrieving the personal data with a new user.

Creating a new user `bandar@juice-shop.op` that only has different vowels than `bender` to cause a clash when obfuscating the email.

The first thing to do is log out as bender, and the second is to create a new user.

![Bandar registration](imgs/bandar_regist.png)

After having logged in with `bandar`, I visited `http://localhost:3000/#/privacy-security/data-export` and selected an export format (JSON).

![Challenge success](imgs/challenge_success.png)

The challenge was solved just after requesting the personal data.

I compared the previous `orderId` from `bender`, which is `130f-f2f4e2800ed87fc0`. When we click export data, a popup will open with the data in JSON format. There is the `130f-f2f4e2800ed87fc0` from the previous user purchase but using another user account that only happens to have different vowels than the attack target user. This weakness can be used to get more data from all the users in the Juice Shop (the users with purchase history).

![Order ID comparison](imgs/compare_id.png)

Other repercussions can include legal violations, financial damage, and reputational harm for the application provider.



