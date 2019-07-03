# Google IoT
##[Introducing the Cloud IoT Device SDK: a new way for embedded IoT devices to connect to Google Cloud IoT Core](https://cloud.google.com/blog/products/iot-devices/introducing-cloud-iot-device-sdk-a-new-way-for-embedded-iot-devices-to-connect-to-google-cloud-iot-core)
##[Google Cloud IoT Device SDK for Embedded C](https://github.com/GoogleCloudPlatform/iot-device-sdk-embedded-c)


### Generating an RSA key
You can generate a 2048-bit RSA key pair with the following commands:
```
openssl genpkey -algorithm RSA -out rsa_private.pem -pkeyopt rsa_keygen_bits:2048  
openssl rsa -in rsa_private.pem -pubout -out rsa_public.pem
```
These commands create the following public/private key pair:

* rsa_private.pem: The private key that must be securely stored on the device and used to sign the authentication JWT.
* rsa_public.pem: The public key that must be stored in Cloud IoT Core and used to verify the signature of the authentication JWT.

# MQTT client example

This example uses the Google Cloud IoT Device SDK for Embedded C to connect a native Linux application to the [Google Cloud IoT Core MQTT bridge](https://cloud.google.com/iot/docs/how-tos/mqtt-bridge#iot-core-mqtt-auth-run-cpp).

## Getting started

Before you begin, generate a [public/private key pair](https://cloud.google.com/iot/docs/how-tos/credentials/keys), store the private key in the `examples/iot_core_mqtt_client/bin` directory, and name the key `ec_private.pem`.

1. Run `make` in the root directory of the repository.

2. From the root directory, generate the native example application.

```
cd examples/iot_core_mqtt_client \
make
```

3. Run the following commands, substituting in your device and project information.

<pre>
make \
cd bin \
./iot_core_mqtt_client -p <i><b>PROJECT_ID</b></i> -d projects/<i><b>PROJECT_ID</b></i>/locations/<i><b>REGION</b></i>/registries/<i><b>REGISTRY_ID</b></i>/devices/<i><b>DEVICE_ID</b></i> -t /devices/<i><b>DEVICE_ID</b></i>/state
</pre>
