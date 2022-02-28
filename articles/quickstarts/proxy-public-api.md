---
title: Proxy a Public API
date: "2022-02-18"
embed: true
---

Zuplo isn't your average gateway. It's a **programmable gateway** that can be
used to protect and share your own API _and_ used as a simple orchestration
layer over SaaS APIs. Choose your getting started guide:

<QuickstartPicker />

Let's proxy the sample e-commerce API at `https://ecommerce-api.zuplo.io` with a
Zuplo gateway in 4 easy steps.

## 1

Open the **routes.json** file and add a new route.

![Untitled](/media/getting-started/add-route.png)

Change the **version** to be `v1` and the **path** of the new route to be
`/products/(.*)` - this uses a wildcard `(.*)` to match anything after
`/products/`.

![Untitled](/media/getting-started/path.png)

## 2

Set the mode of the **Request Handler** to be **URL Rewrite** and the rewrite
path to be `https://ecommerce-api.zuplo.io/v1/products/${params[0]}`. A
parameter `0` matches the wildcard on the incoming URL.

![Untitled](/media/getting-started/rewrite.png)

## 3

Use the route tester at the top of the screen to check your re-write logic. Open
the route tester (top right) and set the path to be `/v1/products/10000`. Verify
that your route was matched and the URL re-written appropriately.

![Untitled](/media/getting-started/route-tester.png)

![Untitled](/media/getting-started/route-matched.png)

## 4

Invoke your API using the Test Console. Click on the lightning tab and select
the first file. Change the path to `/v1/products/10000` and hit **Test**.

![Untitled](/media/getting-started/test-client.png)

## Congratulations

You should see the results of the product with `id:10000`.

Why not try one of the other getting started guides (above) or some of the
examples in our documentation:

- [Write your own policies](/policies)
- [Archive requests to storage](/guides/archiving-requests-to-storage)
- [Setting up JWT auth with Auth0](/guides/setup-jwt-auth-with-auth0)