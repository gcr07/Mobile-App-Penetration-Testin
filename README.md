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













