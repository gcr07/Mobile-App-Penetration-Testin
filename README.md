# Mobile-App-Penetration-Testing


# Android Architecture

Android software contains an open-source Linux Kernel having collection of number of
C/C++ libraries which are exposed through an application framework services.

The main components of android architecture are following:

• Applications
• Application Framework
• Android Runtime (core libraries and the Dalvik virtual machine(DVM))
• Platform Libraries ( s such as Media, Graphics, Surface Manager, OpenGL etc.)
• Linux Kernel

Seria de abajo hacia arriba.

## Maquina virtual 

Dalvik Virtual Machine (DVM) provide platform for running an
android application. Permite correr las apps.


# Android Versions

Google launched the first version of the Android platform on Nov 5, 2007. Since then, Google
released a lot of android versions such as Apple Pie, Banana Bread, Cupcake, Donut, Éclair,
Froyo, Gingerbread, Jellybeans, Kitkat, Lollipop, marshmallow, Nougat, Oreo, etc. with extra
functionalities and new features

## Historico Wikipedia

> https://en.wikipedia.org/wiki/Android_version_history


Se programan en java y kotlin. ( n using Kotlin is preferred by Google, as Kotlin is made an
official language for Android Development)

# Partes de una App 

## View

A View is defined as the user interface which is used to create interactive UI
components such as TextView, ImageView, EditText, RadioButton, etc., and is
responsible for event handling and drawing. They are Generally Called Widgets.

## ViewGroup

The Android framework will allow us to use UI elements or widgets in two ways:
• Use UI elements in the XML file
• Create elements in the Kotlin file dynamically


# Android packets 

An Android package , which is a .apk. APK files contain all the content of an Android app and are the files
that devices built for Android use to install the app.


# Hack Whatsapp

Aqui esta el porque no es tan facil solo leer archivos de whatsapp y  desencriptar las bases de datos

> Each Android app is activated in its own security sandbox, protected by the following Android
security features:

> • The Android operating system is a multi-user Linux system where each application is a
different user.

> • By default, the system assigns each application a unique Linux user code (the code is
used only by the system and is unknown to the application). The system sets
permissions for all files in an application so that only the user code assigned to that
application can access them.

> • Each process has its own virtual machine (VM), so an application's code runs in
isolation from other applications.

>• By default, each application runs in its own Linux process. Android starts the process
when it needs to run some application component. It then shuts it down when it is no
longer needed or when the system needs to reclaim memory for other applications.
The Android system implements the principle of least privilege . That is, each application, by
default, has access only to the components it needs to do its job and nothing else. This creates
a very secure environment where the application cannot access parts of the system that it
does not have permission to. However, there is always a way for an app to share data with
other apps and access system services:

>• It is possible to have two applications share the same Linux user code, in which case
they are able to access each other's files. To preserve system resources, applications
with the same user code can also be combined to run in the same Linux process and
share the same VM. You must also assign the same certificate to the applications.

> • An app may request permission to access device data such as user contacts, SMS
messages, mountable storage (SD card), camera, Bluetooth, etc. The user must
explicitly grant these permissions. To learn more, see Working with System
Permissions.

# Archivos dentro de un apk 

The remainder of this document introduces the following concepts:

• Fundamental library components that define the application.

• The manifest file where you declare the required device components and features for
the application.

• Separate app code features that allow you to optimize the behavior of a variety of
device configurations.

## app features ( o aka recursos imagenes videos musica etc)

> Android apps are made up of more than just code — they require resources separate from the
source code, such as images, audio files, and anything else related to the visual presentation of
the app. For example, you need to define animations, menus, styles, colors, and the layout of
activity UIs with XML files. Using application features makes it easy to update many features of
the application without having to modify the code. Providing the alternate feature sets allows
you to optimize the application for various device configurations such as different languages
and screen sizes.

> For every resource included in the Android project, the SDK programming tools define a
unique integer ID that the programmer can use to reference the resource from application
code or other resources defined in XML. For example, if the app contains an image file
named logo.png(saved in the directory res/drawable/), the SDK tools will generate a feature
code called R.drawable.logo. This code maps to an application-specific integer value, which
you can use to query the image and insert it into your UI.

> Android supports multiple qualifiersfor alternative resources. The qualifier is a short string
added to the name of resource directories to define the device configuration on which these
resources will be used. Another example: it is important to create different layouts for
activities depending on the device's screen size and orientation. When the device screen is in
portrait (vertical) orientation, a layout with vertical buttons can be useful, but when the screen
is in landscape (horizontal) orientation, the buttons need to be aligned horizontally. To change
the layout as per the orientation, you can define two different layouts and apply the
appropriate qualifier to the directory name of each layout. Then the system automatically
applies the proper layout as per the current device orientation.


## Application components

• Activities 

An activity is the entry point for user interaction. It represents a single screen with a user
interface. 

• Services

The serviceit's an entry point to keep an app running in the background, whatever the
reason. For example, a service can play music in
the background while the user is in a different application or fetch data on the network
without blocking the user's interaction with an activity


• Broadcast receivers

• Content providers

## Activation of components

Activities, services, and broadcast receivers — are
activated by an asynchronous message called an intent.

. Think of them as messengers that request an action
from other components, whether the component belongs to the application or not


>Para actividades y servicios, las intenciones definen la acción a realizar (por ejemplo, ver o enviar algo) y pueden especificar el URI de los datos utilizados en la acción, entre otras cosas que el componente iniciador necesita saber. Por ejemplo, una intención podría transmitir una solicitud de actividad para mostrar una imagen o abrir una página web. En algunos casos, debe iniciar una actividad para recibir un resultado. En este caso, la actividad también devuelve el resultado en un Intent. Por ejemplo, puede emitir una intención para que el usuario seleccione un contacto personal y se lo devuelva. La intención de devolución contiene un URI que apunta al contacto seleccionado.

# Tipos de Dispositivos 

Existen varios dispositivos desarrollados para Android y no todos tienen las mismas prestaciones y características. Para evitar que la aplicación se instale en dispositivos que no contienen las características que requiere la aplicación, es importante definir un perfil para los tipos de dispositivos admitidos por la aplicación. Debe declarar los requisitos del dispositivo y el software en el archivo de manifiesto. La mayoría de estas declaraciones son solo informativas y el sistema no las lee, pero los servicios externos como Google Play las leen para proporcionar un filtro a los usuarios cuando buscan estas aplicaciones para su dispositivo.


> For example, if your app requires a camera and uses APIs introduced in Android 2.1 ( API
level 7), you would need to declare those requirements in the manifest file as follows:

```
<manifest ... >
<usesfeatureandroid:name="android.hardware.camera.any"android:required="true"/><usessdkandroid:minSdkVersion="7"android:targetSdkVersion="19"/> .
..</manifest>

```

Every app project needs to have a file AndroidManifest.xml(with that exact name) at the root
of the project's source set . The manifest file describes essential app information for the
Android build tools, the Android operating system, and Google Play.


***If you're using Android Studio to build the app, the manifest file is built for you, and most of
the essential elements of the manifest are added during that build, particularly when
using code templates .***

## file resources

### Package name and Application ID

The root element of the manifest file requires an attribute for the application's package name
(which typically corresponds to the project's directory structure, the Java namespace).
For example, the following snippet shows the <manifest>root element with the package
 
```
  
name "com.example.myapp":
<?xml version="1.0" encoding="utf8"?><manifestxmlns:android="http://schemas.android.com/apk/res/android"package="com.e
xample.myapp"android:versionCode="1"android:versionName="1.0"> ...</manifest>

```
  
### application components ( Osea lo que va dentro del archivo manifest)
  
  
  For each application component that is created in your application, you need to declare a
corresponding XML element in the manifest file:
  
```
• <activity> for each subclass of Activity.
• <service> for each subclass of Service.
• <receiver> for each subclass of BroadcastReceiver.
• <provider> for each subclass of ContentProvider.
  
```
  
If you subclass any of these components without declaring it in the manifest file, the system
will not be able to launch it.

### Intent filters
  
Application activities, services, and broadcast receivers are enabled by intents . The intent is a
message defined by an object Intentthat describes an action to be performed, including data
used in actions, the category of component that will perform the action, and other
instructions.
  
  
### Icons and Labels
  
Several manifest elements have iconand attributes labelto display, respectively, a small icon
and a text label to users for the corresponding application component.
In all cases, the icon and label defined on a parent element become the default values icon
for labelall child elements. For example, the icon and label defined on the
  
```
element <application>are the default for all application components (like all activities).
```
  
### permissions
  
Android apps need to ask for permission to access sensitive user data (like contacts and SMS)
or certain system features (like camera and internet access). Each permission is identified by a
unique label. For example, an application that needs to send SMS messages needs to have the
following line in the manifest.
  
```
<manifest ... ><usespermissionandroid:name="android.permission.SEND_SMS"/> ...</manifest>
  
```
  
> But regardless of which version of Android your app supports, you
need to declare all permissions requests with an element <uses-permission>in the manifest. If
the permission is granted, the app will be able to use the protected resources. Otherwise, the
attempt to access these resources will fail.
  
  
### device compatibility
  
The manifest file is also where you can declare what types of hardware or software resources
the application requires and what types of devices it supports. The Google Play Store does not
allow your app to be installed on devices that do not provide the required features or system
version
  
### <uses-feature>
  
  Te dice si alguna funcion se puede o no correr en este dispoditivo.
  
  > The element allows you to declare the hardware and software resources that the application
needs. For example, if your app is unable to perform basic functionality on a device that does
not have a compass sensor, you can declare the compass sensor as mandatory with the
following manifest tag: <uses-feature>

 
 ### <uses-sdk>
  
> Each successive version of the platform often adds new APIs not available in the previous
version. To indicate the minimum version supported by the application, the manifest must
include the tag <uses-sdk>and the minSdkVersion.
  
Ejemplo de archivo Manifest 
  
  
```
  
<?xml version="1.0" encoding="utf-8"?>
<manifest
xmlns:android="http://schemas.android.com/apk/res/android"
android:versionCode="1"
android:versionName="1.0"
package="com.example.myapp">
<!-- Beware that these values are overridden by the build.gradle file -->
<uses-sdk android:minSdkVersion="15" android:targetSdkVersion="26" />
<application
android:allowBackup="true"
android:icon="@mipmap/ic_launcher"
android:roundIcon="@mipmap/ic_launcher_round"
android:label="@string/app_name"
android:supportsRtl="true"
android:theme="@style/AppTheme">
<!-- This name is resolved to com.example.myapp.MainActivity
based upon the package attribute -->
<activity android:name=".MainActivity">
<intent-filter>
<action android:name="android.intent.action.MAIN" />
<category android:name="android.intent.category.LAUNCHER" />
</intent-filter>
</activity>
<activity
android:name=".DisplayMessageActivity"
android:parentActivityName=".MainActivity" />
</application>
</manifest>  
  
  
```
  
# Tipos de Apps
  
Three main types of the mobile apps are divided: Mobile Web Apps, Native (Pure native) Apps,
and Hybrid Apps
  
  
## Mobile Web application,
 
In fact, is the website opened in the gadget (smartphone or tablet)
with the help of the mobile browser.

 No offline capabilities support.
• Limited functionality in the comparison with Hybrid and Native Apps. (no access to the
file system and local resources).
• Problems with redistribution: Google Play and App Store don’t support redistribution
of the Mobile Web Apps.
 
 
 ## Native App
 
 Is the application, which has been developed specifically for one platform
(Android, iOS, Tizen, Windows 10 M0bile, BlackBerry).
 
 Some merits of the Native Apps:
• Native app works offline.
• It can use all features of its device.
• Advanced user experience.
• Push notifications can be used for users alert.

 ## Hybrid App 
 
 Is the mix of the Native App and Mobile Web App. It can be defined like mobile
website content exposition in the application format.
Some merits of the Hybrid Apps:
• More cost effective in comparison to the Native App.
• Easy distribution.
• Embedded browser.
• Device features.
Some demerits of the Hybrid Apps:
• It works not so fast as Native App.
• Graphics are less accustomed to the OS in comparison to Native App.
 
 Some demerits of the Native Apps:
• Native Apps creation is expensive in comparison to the Mobile Web apps.
• It requires high costs for the maintenance.
 
 

# Testing
 
 ## Emulador
 
 De hecho, un emulador es el reemplazo del dispositivo original. Aunque puede ejecutar programas y aplicaciones en su dispositivo, no tiene la capacidad de modificarlos
 
 ## Simulador
 
 El simulador no replica el hardware del dispositivo, pero tiene la capacidad de configurar un entorno similar al del sistema operativo del dispositivo original.
 
 ## Cloud-based testing of the mobile application
 
 Probar aplicaciones móviles con herramientas basadas en la nube parece ser la opción óptima. Puede ayudarlo a superar las desventajas de los dispositivos y simuladores reales.
 
 




