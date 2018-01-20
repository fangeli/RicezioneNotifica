Vediamo come creare un progetto in Cordova che utilizzi la push notification.
Non utilizzeremo Visual Studio, ma faremo tutto da riga di comando
1. **Create an empty Cordova project ricezioneNotifica**
```
cd t :\
mkdir ricezioneNotifica
cd ricezioneNotifica
cordova create ricezioneNotifica
cd ricezioneNotifica
cordova platform add android
```
2. **Aggiungere il plugin: cordova-plugin-firebase**. Lo scaricheremo con NPM:
```
cordova plugin add cordova-plugin-firebase@0.1.25 --save
```
3. **Registrare il progetto in Firebase**
   - open the google firebase console
https://console.firebase.google.com/ and Add Project ( ba-
sically means create a new project ) e inserire
– pushSample
– italia
   - Once the project is created click on GROW >Notifications section
in left side panel.
   - Now click on the Android icon to add Android platform support
to our project.
– Android package name: ex: com.ricezioneNotifica.hello
– App nickname: ex: blank
– Debug signing certificate SHA-1: ex: blank
   - Cliccare su Registra App e scaricare il file google-services.json nella root del progetto
   - change widget id in config.xml of your project

```
<!--<widget id="io.cordova.hellocordova"-->
<widget id="com.ricezioneNotifica.hello"
```
 
4. **sottoscrivere l'app a un topic**:
   - aprire index.js
   - nella receivedEvent inserire
``` javascript
window.FirebasePlugin.subscribe("topic1");
```
5. **Build the project**
```
cordova build android
``` 
6. **avviare l'app su dispositivo** e una volta terminata l'installazione mettere l'app in background
```
cordova run android
```

NOTA1
Per fare la build del progetto  è stato necessario mettere nella vari-
abile PATH il percorso alla cartella Android
ANDROID HOME=C:/ProgramData/Microsoft/AndroidSDK/25

NOTA2
You cannot run push notifications in the simulator, you will need an
actual device. E' necessario permettere
l’accesso ai dati del device
 
