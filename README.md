# VisaPay

VisaPay is a flutter payment app with features like generating links and QR code for payments.


### Installation:

Clone this repository

```bash
git clone https://github.com/mikal09/Visa-Pay
```

## For Visa Pay Mobile Application

#### To Run:
1) Install and setup flutter using [Install flutter](https://flutter.dev/docs/get-started/install).
2) Navigate to the project directory Visa-Pay
3) Remove the folder VisaPaymentRESTService folder
4) Install the required flutter extension and packages in VS Code or Android studio.
5) Launch Emulator or run on real device
6) Run the app from terminal using ```flutter run```.

## For Visa Pay Web Service

#### To Run:
1) Navigate to the project directory Visa-Pay
1) Create a fat jar out of Spring Boot Application (VisaPaymentRESTService folder only) using ``` mvn clean install```. An embedded Tomcat Server is also built-in.
2) If you wish to deploy the application as WAR, change the packaging property inside pom.xml to war.
3) Run the jar file using ``` java -jar <artifact-name>```

## Instructions on generating the payment link:

1) First the merchant alias is taken (which is mostly his phone or mobile number) and the amount that is supposed to be paid is taken


  String = XXXXXXXXX : YYYY : ZZZZ


Here,

XXXXXXXX denotes the merchant alias
YYYY denotes the amount to be paid in double type
ZZZZ denotes the current system time in milli seconds

2) Now , a random 10 length key is generated consisting of only alphanumeric characters and the String is encrypted using this key and using ‘AES/ECB/PKCS5PADDING’

  *New string = encryption(string) using key*

3)  Now , this new String is converted to base 16 value so as to avoid characters like %, / that are not URL safe. Once this is done, the key is appended to this value as it is without any separation and that is the final link. 

4) Example of a link on a service hosted on local host:-

  http://localhost:8080/payments/b8b038a41b89d0662d591bd4380261c58e6bd7b82a9faef25b33a90af589d5791a2f4d3s2d

