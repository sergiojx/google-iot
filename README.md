
# Google IoT
![picture](https://bitbucket.org/sergiojx/google-iot/downloads/1__WSqG1NE4ofI_dM6eSOfuA.png)
![picture](https://bitbucket.org/sergiojx/google-iot/downloads/1_J1_fM45SqgReqZBy-IDy_Q.png)
![picture](https://bitbucket.org/sergiojx/google-iot/downloads/f5ipnmevrxc0fnbjilg9xlqf1ng.jpeg)
![picture](https://bitbucket.org/sergiojx/google-iot/downloads/overview.png)
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

```
make

```

```
cd bin 
```

```
./iot_core_mqtt_client -p PROJECT_ID -d projects/PROJECT_ID/locations/REGION/registries/REGISTRY_ID/devices/DEVICE_ID -t /devices/DEVICE_ID/state
```
## gcloud
[Connect and Manage IoT Devices at Scale with Cloud IoT Core | Google Cloud Labs](https://www.youtube.com/watch?reload=9&v=iRZzqpvARbc)
[Quickstart](https://cloud.google.com/iot/docs/quickstart)
```
sergio (master) mqtt_example $ gcloud pubsub subscriptions create projects/involuted-smile-246201/subscriptions/my-subscription --topic=projects/involuted-smile-246201/topics/variables-proton  
. . .  
Created subscription [projects/involuted-smile-246201/subscriptions/my-subscription].

```

```
sergio (master) mqtt_example $ node cloudiot_mqtt_example_nodejs.js \
>     mqttDeviceDemo \
>     --projectId=involuted-smile-246201 \
>     --cloudRegion=us-central1 \
>     --registryId=proton-registry \
>     --deviceId=my-device \
>     --privateKeyFile=rsa_private.pem \
>     --numMessages=25 \
>     --algorithm=RS256
Google Cloud IoT Core MQTT example.
connect
Publishing message: proton-registry/my-device-payload-1
Config message received: 
Config message received: 
Publishing message: proton-registry/my-device-payload-2
Publishing message: proton-registry/my-device-payload-3
Publishing message: proton-registry/my-device-payload-4
Publishing message: proton-registry/my-device-payload-5
Publishing message: proton-registry/my-device-payload-6
Publishing message: proton-registry/my-device-payload-7
Publishing message: proton-registry/my-device-payload-8
Publishing message: proton-registry/my-device-payload-9
Publishing message: proton-registry/my-device-payload-10
Publishing message: proton-registry/my-device-payload-11
Publishing message: proton-registry/my-device-payload-12
Publishing message: proton-registry/my-device-payload-13
Publishing message: proton-registry/my-device-payload-14
Publishing message: proton-registry/my-device-payload-15
Publishing message: proton-registry/my-device-payload-16
Publishing message: proton-registry/my-device-payload-17
Publishing message: proton-registry/my-device-payload-18
Publishing message: proton-registry/my-device-payload-19
Publishing message: proton-registry/my-device-payload-20
Publishing message: proton-registry/my-device-payload-21
Publishing message: proton-registry/my-device-payload-22
Publishing message: proton-registry/my-device-payload-23
Publishing message: proton-registry/my-device-payload-24
Publishing message: proton-registry/my-device-payload-25
Closing connection to MQTT. Goodbye!
close

```


```
sergio (master) mqtt_example $ gcloud pubsub subscriptions pull --auto-ack \
>     projects/involuted-smile-246201/subscriptions/my-subscription
┌─────────────────────────────────────┬─────────────────┬────────────────────────────────────┐
│                 DATA                │    MESSAGE_ID   │             ATTRIBUTES             │
├─────────────────────────────────────┼─────────────────┼────────────────────────────────────┤
│ proton-registry/my-device-payload-5 │ 610622344257536 │ deviceId=my-device                 │
│                                     │                 │ deviceNumId=2685979480751018       │
│                                     │                 │ deviceRegistryId=proton-registry   │
│                                     │                 │ deviceRegistryLocation=us-central1 │
│                                     │                 │ projectId=involuted-smile-246201   │
│                                     │                 │ subFolder=                         │
└─────────────────────────────────────┴─────────────────┴────────────────────────────────────┘
sergio (master) mqtt_example $ gcloud pubsub subscriptions pull --auto-ack     projects/involuted-smile-246201/subscriptions/my-subscription
┌─────────────────────────────────────┬─────────────────┬────────────────────────────────────┐
│                 DATA                │    MESSAGE_ID   │             ATTRIBUTES             │
├─────────────────────────────────────┼─────────────────┼────────────────────────────────────┤
│ proton-registry/my-device-payload-9 │ 610625453427657 │ deviceId=my-device                 │
│                                     │                 │ deviceNumId=2685979480751018       │
│                                     │                 │ deviceRegistryId=proton-registry   │
│                                     │                 │ deviceRegistryLocation=us-central1 │
│                                     │                 │ projectId=involuted-smile-246201   │
│                                     │                 │ subFolder=                         │
└─────────────────────────────────────┴─────────────────┴────────────────────────────────────┘
sergio (master) mqtt_example $ gcloud pubsub subscriptions pull --auto-ack     projects/involuted-smile-246201/subscriptions/my-subscription
┌─────────────────────────────────────┬─────────────────┬────────────────────────────────────┐
│                 DATA                │    MESSAGE_ID   │             ATTRIBUTES             │
├─────────────────────────────────────┼─────────────────┼────────────────────────────────────┤
│ proton-registry/my-device-payload-4 │ 610625263851045 │ deviceId=my-device                 │
│                                     │                 │ deviceNumId=2685979480751018       │
│                                     │                 │ deviceRegistryId=proton-registry   │
│                                     │                 │ deviceRegistryLocation=us-central1 │
│                                     │                 │ projectId=involuted-smile-246201   │
│                                     │                 │ subFolder=                         │
└─────────────────────────────────────┴─────────────────┴────────────────────────────────────┘


```

```
sergio (master *) bin $ gcloud pubsub subscriptions pull --limit 5  --auto-ack projects/involuted-smile-246201/subscriptions/my-subscription
┌──────────────────────────────┬─────────────────┬────────────────────────────────────┐
│             DATA             │    MESSAGE_ID   │             ATTRIBUTES             │
├──────────────────────────────┼─────────────────┼────────────────────────────────────┤
│ Hello From Your IoTC client! │ 613723517315222 │ deviceId=nano                      │
│                              │                 │ deviceNumId=2687375433246373       │
│                              │                 │ deviceRegistryId=proton-registry   │
│                              │                 │ deviceRegistryLocation=us-central1 │
│                              │                 │ projectId=involuted-smile-246201   │
│                              │                 │ subFolder=                         │
│ Hello From Your IoTC client! │ 613728186857675 │ deviceId=nano                      │
│                              │                 │ deviceNumId=2687375433246373       │
│                              │                 │ deviceRegistryId=proton-registry   │
│                              │                 │ deviceRegistryLocation=us-central1 │
│                              │                 │ projectId=involuted-smile-246201   │
│                              │                 │ subFolder=                         │
│ Hello From Your IoTC client! │ 613724937068260 │ deviceId=nano                      │
│                              │                 │ deviceNumId=2687375433246373       │
│                              │                 │ deviceRegistryId=proton-registry   │
│                              │                 │ deviceRegistryLocation=us-central1 │
│                              │                 │ projectId=involuted-smile-246201   │
│                              │                 │ subFolder=alerts                   │
│ Hello From Your IoTC client! │ 613730472563410 │ deviceId=nano                      │
│                              │                 │ deviceNumId=2687375433246373       │
│                              │                 │ deviceRegistryId=proton-registry   │
│                              │                 │ deviceRegistryLocation=us-central1 │
│                              │                 │ projectId=involuted-smile-246201   │
│                              │                 │ subFolder=alerts                   │
│ Hello From Your IoTC client! │ 613724445726125 │ deviceId=nano                      │
│                              │                 │ deviceNumId=2687375433246373       │
│                              │                 │ deviceRegistryId=proton-registry   │
│                              │                 │ deviceRegistryLocation=us-central1 │
│                              │                 │ projectId=involuted-smile-246201   │
│                              │                 │ subFolder=alerts                   │
└──────────────────────────────┴─────────────────┴────────────────────────────────────┘

```

## C Mqtt example execition
### Events
Messages published to this MQTT topic are forwarded to the corresponding registry's default telemetry topic. The default telemetry topic is the Cloud Pub/Sub topic specified in the eventNotificationConfigs[i].pubsubTopicName field in the registry resource. If no default Pub/Sub topic exists, published telemetry data will be lost
```
./iot_core_mqtt_client -p involuted-smile-246201 -d projects/involuted-smile-246201/locations/us-central1/registries/proton-registry/devices/nano -t /devices/nano/events
```
### State
```
./iot_core_mqtt_client -p involuted-smile-246201 -d projects/involuted-smile-246201/locations/us-central1/registries/proton-registry/devices/nano -t /devices/nano/state
```

### subFolder/Alerts
```
./iot_core_mqtt_client -p involuted-smile-246201 -d projects/involuted-smile-246201/locations/us-central1/registries/proton-registry/devices/nano -t /devices/nano/events/alerts

```
### subFolder/Warnings
```
sergio (master *) bin $ ./iot_core_mqtt_client -p involuted-smile-246201 -d projects/involuted-smile-246201/locations/us-central1/registries/proton-registry/devices/nano -t /devices/nano/events/warnings
```

## libiotc.so compilation 4 Proton
```
sergio (master *) giot-device-sdk-embedded-c4Proton $ make TARGET=linux-shared-debug
```
#### mt-linux.mk
```
# Copyright 2018-2019 Google LLC
#
# This is part of the Google Cloud IoT Device SDK for Embedded C.
# It is licensed under the BSD 3-Clause license; you may not use this file
# except in compliance with the License.
#
# You may obtain a copy of the License at:
#  https://opensource.org/licenses/BSD-3-Clause
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

CC = /opt/codesourcery/arm-2011.09/bin/arm-none-linux-gnueabi-gcc
CXX = /opt/codesourcery/arm-2011.09/bin/arm-none-linux-gnueabi-g++
AR = /opt/codesourcery/arm-2011.09/bin/arm-none-linux-gnueabi-ar

IOTC_COMMON_COMPILER_FLAGS += -fPIC
IOTC_LIB_FLAGS += $(IOTC_TLS_LIBFLAGS) -lpthread -lm -lrt -lcrypto

include make/mt-os/mt-os-common.mk

ifdef IOTC_SHARED
  AR = /opt/codesourcery/arm-2011.09/bin/arm-none-linux-gnueabi-gcc
  XI = $(IOTC_BINDIR)/libiotc.so
  IOTC_ARFLAGS += -fPIC -DIOTC_SHARED -shared -o $(XI)
else
  IOTC_ARFLAGS += -rs -c $(XI)
endif

# Temporarily disable these warnings until the code gets changed.
IOTC_COMMON_COMPILER_FLAGS += -Wno-format

IOTC_CONFIG_FLAGS += -DIOTC_MULTI_LEVEL_DIRECTORY_STRUCTURE
IOTC_CONFIG_FLAGS += -DIOTC_LIBCRYPTO_AVAILABLE
IOTC_LIBCRYPTO_AVAILABLE := 1

```
#### buid-mbedtls.sh
```
#!/bin/bash
# Copyright 2018-2019 Google LLC
#
# This is part of the Google Cloud IoT Device SDK for Embedded C.
# It is licensed under the BSD 3-Clause license; you may not use this file
# except in compliance with the License.
#
# You may obtain a copy of the License at:
#  https://opensource.org/licenses/BSD-3-Clause
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

echo
echo "--------------------------"
echo "| mbedTLS LICENSE Notice |"
echo "--------------------------"
echo
echo "Unless specifically indicated otherwise in a file, files are licensed"
echo "under the Apache 2.0 license, as can be found in: apache-2.0.txt"
echo
echo "the apache-2.0.txt file can be accessed here:"
echo "   https://www.apache.org/licenses/LICENSE-2.0"
echo
echo "For more information about the mbedTLS license, please check the LICENSE"
echo "file of the mbedTLS directory after this auto-checkout procedure"
echo "completes, or check their github repository at the following address:"
echo "  https://github.com/ARMmbed/mbedtls"
echo
read -p "Continue to auto-download and build mbedTLS? [Y/N] " -n 1 -r
echo
if [[ ! $REPLY =~ ^[Yy]$ ]]
then
    echo
    echo "exiting build."
    echo
    exit 1
fi

mkdir -p ../../third_party/tls
cd ../../third_party/tls

git clone -b mbedtls-2.12.0 https://github.com/ARMmbed/mbedtls.git
cd mbedtls
# "-O2" comes from mbedtls/library/Makefile "CFLAGS ?= -O2" define
make CC="/opt/codesourcery/arm-2011.09/bin/arm-none-linux-gnueabi-gcc" CFLAGS="-O2 -DMBEDTLS_PLATFORM_MEMORY $1"
echo "mbedTLS Build Complete."


```

```
sergio ((mbedtls-2.12.0) *) mbedtls $ make CC=/opt/codesourcery/arm-2011.09/bin/arm-none-linux-gnueabi-gcc AR=/opt/codesourcery/arm-2011.09/bin/arm-none-linux-gnueabi-ar SHARED=1
```