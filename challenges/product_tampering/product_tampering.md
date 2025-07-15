# Product Tampering

To start with this challenge, I started the Kali VM to launch the OWASP Juice Shop application.

![Kali VM](imgs/tamp_kali_vm.png)

With the VM active, I started the OWASP Juice Shop and the `ZAP` tool. The `ZAP` tool will be used as a penetration testing tool to find vulnerabilities in web applications.

![Start Juice Shop and ZAP](imgs/tamp_start_app_zarp.png)

Once the proxy tool started, I opened the browser from the `ZAP` tool. In the newly opened browser, I entered the URL from the Juice Shop in the search bar.

```
http://localhost:3000
```

![Launch browser from ZAP](imgs/tamp_brwser_lauch.png)

![Localhost](imgs/juice_sh_localhost.png)

Once on the main page, I started to search for the target product (O-Saft) and inspect the network to see how the requests look.

![O-Saft](imgs/check_network.png)

In the **Network** tab, I can see a request `http://localhost:3000/api/Quantitys` with all the available products and also a `ProductId`, but with no **description** of the products.

I decided to modify the request to `http://localhost:3000/api/products` to see if I can get something from the server. I got a list with all the products and, most importantly, the `id` and `description`.

![All products API](imgs/check_products_api.png)

This gave me the `id` of the `O-Saft` product, which is `id: 9`. The `description` contained the link that should be changed in this challenge.

![Product 9](imgs/product_id.png)

I had to find the correct path to make a request and change the `description` to `<a href=\"https://owasp.slack.com\" target=\"_blank\">More...</a>`.

I noticed that when I log in as `admin` and go to the `/administration` page, I can see the reviews of all products. I can also **delete** the reviews. So, I deleted a review and took a look at the network.

![Find API path](imgs/find_api_path.png)

I saw a `DELETE` request to `http://localhost:3000/api/Feedbacks/1` and looked at it in more detail with the `ZAP` tool.

![API path](imgs/get_api_path.png)

I copied this request and changed it to a `PUT http://localhost:3000/api/Products/9` and also added `Content-Type: application/json` to the **header**.

![Change request](imgs/put_req_to_id_9.png)

After sending the request, I looked at the site `http://localhost:3000/api/products/` to see the changes:

![Product modification](imgs/check_api_products.png)

The product's description was updated with the desired link. I visited the product's page and saw the challenge solved element.

![Challenge success](imgs/chellenge_success.png)

![Changed request href](imgs/href_changed.png)

This was possible due to the API vulnerability that allows sending requests with the `PUT` command. This kind of attack can lead to unauthorized access to external resources or the dissemination of misleading information.