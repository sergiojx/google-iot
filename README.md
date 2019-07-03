# Google IoT
##[Introducing the Cloud IoT Device SDK: a new way for embedded IoT devices to connect to Google Cloud IoT Core](https://cloud.google.com/blog/products/iot-devices/introducing-cloud-iot-device-sdk-a-new-way-for-embedded-iot-devices-to-connect-to-google-cloud-iot-core)
##[Google Cloud IoT Device SDK for Embedded C](https://github.com/GoogleCloudPlatform/iot-device-sdk-embedded-c)


Generating an RSA key
You can generate a 2048-bit RSA key pair with the following commands:
```
openssl genpkey -algorithm RSA -out rsa_private.pem -pkeyopt rsa_keygen_bits:2048  
openssl rsa -in rsa_private.pem -pubout -out rsa_public.pem
```
These commands create the following public/private key pair:

* rsa_private.pem: The private key that must be securely stored on the device and used to sign the authentication JWT.
* rsa_public.pem: The public key that must be stored in Cloud IoT Core and used to verify the signature of the authentication JWT.
