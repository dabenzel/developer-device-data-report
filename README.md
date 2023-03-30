# zendure-developer-device-report

## About
The current version supports subscribing to device uplink data，Subscribe to device data for Zendure products. To receive information from the device, Developers can obtain the same device information as the official App by subscribing to Zendure MQTT Broker。

Purpose：Open device data for all zendure App users, developers can obtain device information through the following steps

### The project provides
  1、Apply to become a developer Api call example.  
  
  2、Create Mqtt client and device message subscription example. 
  
  3、Mqtt Broker endpoint configuration information.  

## Steps for Subscribe to device data

### Apply to be a developer
  1、First you need to register an account in Zendure App.  
  
  iOS: https://apps.apple.com/us/app/zendure/id1592645038  
  
  Android: https://play.google.com/store/apps/details?id=com.zendure.iot&pli=1  
  
  Web: https://app.zendure.com/download/  
  
  
  2、Familiar with MQTT protocol and client message subscription.  
  
  * MQTT Endpoint：<span style="border-bottom:2px dashed yellow;">tcp://mqtt.zen-iot.com:1883</span>
  
  3、To call the Rest Api to get the client configuration, you need to provide the device SN and Zendure App account.(Connect your device to WiFi and use the official mobile app to register a Zendure account and bind your device,If multiple devices are bound, randomly select the sn of one of them)  
  
  Endpoint: https://app.zendure.tech/v2/developer/api/apply  
  
  Request Method: POST  
  
  Required parameterized:  
    snNumber - the device serial number  
    account - Zendure App account username  
```java
curl -H "Content-Type: application/json" -X POST -d "{\"snNumber\":\"VA6DKKCKKU00068\",\"account\":\"zentest01@163.com\"}" "https://app.zendure.tech/v2/developer/api/apply"
```
```java  
{  
  "snNumber":"VU5D99F74021B04",  
  "account":"dev@zendure.com"
}

```
Api Response:
```java
{  
  "code":200,  
  "success":true,  
  "data":{  
    "appKey":"zendure",  
    "secret":"zendureSecret",  
    "mqttUrl":"mqtt.zen-iot.com",  
    "port":1883  
   },
   "msg":"Successful operation"  
}  
```

  
### Integrated Home Assistant
  1、Select devices and services in Home Assistant, add mqtt integration services,You can use appKey as username and appSecret as password to connect mqtt broker.  For 
  2、For more information about the mqtt protocol, please refer to：https://mqtt.org/.  
  3、Home Assistant, please refer to https://www.home-assistant.io/.  
  4、All possible metric names and their values sent by the device to the MQTT Zendure Broker. Data reporting via JSON object key/value. For example: device power, remaining discharge time.  
  ```java
  {  
    "electricLevel": 99,  
    "remainOutTime": 9999,  
    "socSet": 80  
  }  
  ```
 
 ### Device report data list
 
 | Field | Description |
| --- | --- |
| electricLevel | Device battery percentage |
| remainOutTime | Remaining discharge time |
| remainInputTime | Remaining charging time |
| socSet | Charge Capacity Limitation |
| batterCapacity | battery capacity |
| acInputLimit | AC input limit |
| slowChargePower | Slow charging power |
| inputPower | total input power |
| acSwitch | AC switch |
| acInputMode | AC input mode(1: Power grid 2: Charging cable) |
| acInputPower | AC input power |
| acHz | AC input frequency |
| acInputVoltage | ac input voltage |
| acOutputMode | AC output mode（1:UPS 2:120V 3:120V和240V） |
| acOutputPower | AC output power |
| acOutputVoltage | AC output voltage |
| acOutputFactor | AC output load factor |
| dcSwitch | DC switch |
| dcInputMode | DC input mode(1: car charger 2: solar energy) |
| dcInputPower | DC input power |
| outputPower | total output power |
| dcOutputPower | DC output power |
| circleOutputPower | circle output power |
| usb1OutputPower | USB1 output power |
| usb2OutputPower | USB2 output power |
| typec1Power | TypeC1 output power |
| typec2Power | TypeC2 output power |
| typec3Power | TypeC3 output power |
| typec4Power | TypeC4 output power |
| andersonPower | Anderson output power |
| ambientSwitch | Ambient light switch |
| ambientLightMode | Ambient light mode |
| ambientLightColor | Ambient light color |
| ambientLightNess | Ambient light brightness |
| buzzerSwitch | buzzer switch |
| masterSwitch | master switch |
| childLock | child lock switch |
| assistSwitch | power wheel switch |
| assistAngle | Power wheel angle |
| lampSwitch | light switch |
| lampMode | light mode |
| upsMode | UPS mode |
| machineStandTime | automatic shutdown time |
| screenStandTime | automatic screen off time |
| wifiSwitch | wifi switch |
| wifiSignalLevel | wifi signal level |
| blueState | blue state |
| wifiState | wifi state |
| silentInput | Silent charging mode (sleep mode) |
| ampUp | constant power mode |
| dcHardwareVersion | DC Hardware version |
| acHardwareVersion | AC hardware version |
| bmsHardwareVersion | BMS hardware version |
| masterHardwareVersion | MASTER hardware version |
| typecHardwareVersion | TYPEC hardware version |
| electricFanState | fan status |
| batteryNum | battery num |
| temperature | device temperature |
| solarWorkMode | Solar working mode |
| solarWorkOutputVoltage | Solar output voltage |
| solarOutputPower | Solar output power |
| assistDoubleFlash | Power wheel double flash switch |
| seriesMode | series mode |
| parallelMode | parallel mode |

## Future plan
1、Support data downlink and device control.  
2、Support device LAN communication.

## contact us
This project is only for reference, you can contact us by email: dev@zendure.com
