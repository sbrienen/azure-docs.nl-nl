---
author: mikben
ms.service: azure-communication-services
ms.topic: include
ms.date: 9/1/2020
ms.author: mikben
ms.openlocfilehash: c015561e66d77e6df352e601bf1a67da5996d4d5
ms.sourcegitcommit: 230d5656b525a2c6a6717525b68a10135c568d67
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94915549"
---
## <a name="prerequisites"></a>Vereisten

- Een Azure-account met een actief abonnement. [Gratis een account maken](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) 
- Een geïmplementeerde Communication Services-resource. [Een Communication Services-resource maken](../../create-communication-resource.md).
- Een `User Access Token` om de aanroepende client in te schakelen. Voor meer informatie over het [verkrijgen van een `User Access Token`](../../access-tokens.md)
- Optioneel: Voltooi de Snelstartgids om aan de [slag te gaan met het toevoegen van een oproep aan uw toepassing](../getting-started-with-calling.md)

## <a name="setting-up"></a>Instellen

### <a name="install-the-package"></a>Het pakket installeren

<!-- TODO: update with instructions on how to download, install and add package to project -->
Zoek de build.gradle op projectniveau op en vergeet niet `mavenCentral()` toe te voegen aan de lijst met opslagplaatsen onder `buildscript` en `allprojects`
```groovy
buildscript {
    repositories {
    ...
        mavenCentral()
    ...
    }
}
```

```groovy
allprojects {
    repositories {
    ...
        mavenCentral()
    ...
    }
}
```
Voeg vervolgens in het module niveau build. gradle de volgende regels toe aan de sectie Dependencies

```groovy
dependencies {
    ...
    implementation 'com.azure.android:azure-communication-calling:1.0.0-beta.2'
    ...
}

```

## <a name="object-model"></a>Objectmodel

De volgende klassen en interfaces verwerken enkele van de belangrijkste functies van de Azure Communication Services-clientbibliotheek voor aanroepen:

| Naam                                  | Beschrijving                                                  |
| ------------------------------------- | ------------------------------------------------------------ |
| CallClient| De CallClient is het belangrijkste ingangspunt voor de clientbibliotheek voor oproepen.|
| CallAgent | De CallAgent wordt gebruikt om oproepen te starten en te beheren. |
| CommunicationUserCredential | De CommunicationUserCredential wordt als de tokenreferentie gebruikt om de CallAgent te instantiëren.|

## <a name="initialize-the-callclient-create-a-callagent-and-access-the-devicemanager"></a>Initialiseer de CallClient, maak een CallAgent en open de DeviceManager

Als u een `CallAgent` exemplaar wilt maken, moet u de methode aanroepen `createCallAgent` voor een `CallClient` exemplaar. Hiermee wordt een `CallAgent` object Instance asynchroon geretourneerd.
De `createCallAgent` methode heeft een `CommunicationUserCredential` als argument, waarmee een [toegangs token](../../access-tokens.md)wordt ingekapseld.
Als u toegang wilt krijgen tot de `DeviceManager` , moet u eerst een callAgent-exemplaar maken. vervolgens kunt u de `CallClient.getDeviceManager` methode gebruiken om de DeviceManager op te halen.

```java
String userToken = '<user token>';
CallClient callClient = new CallClient();
CommunicationUserCredential tokenCredential = new CommunicationUserCredential(userToken);
android.content.Context appContext = this.getApplicationContext(); // From within an Activity for instance
CallAgent callAgent = await callClient.createCallAgent((appContext, tokenCredential).get();
DeviceManage deviceManager = await callClient.getDeviceManager().get();
```

## <a name="place-an-outgoing-call-and-join-a-group-call"></a>Een uitgaande oproep plaatsen en toevoegen aan een groeps oproep

Als u een gesprek wilt maken en starten, moet u de-methode aanroepen `CallAgent.call()` en het van de genodigden opgeven `Identifier` .
Als u lid wilt worden van een groeps oproep, moet u de methode aanroepen `CallAgent.join()` en de groupid opgeven. Groeps-Id's moeten de GUID-of UUID-indeling hebben.

Het maken van aanroepen en starten synchroon zijn. Met het gesprek exemplaar kunt u zich abonneren op alle gebeurtenissen in de aanroep.

### <a name="place-a-11-call-to-a-user"></a>Een 1:1-aanroep naar een gebruiker plaatsen
Als u een aanroep naar een andere communicatie Services-gebruiker wilt plaatsen, roept u de- `call` methode aan `callAgent` en geeft u een object met de `communicationUserId` sleutel door.
```java
StartCallOptions startCallOptions = new StartCallOptions();
Context appContext = this.getApplicationContext();
CommunicationUser acsUserId = new CommunicationUser(<USER_ID>);
CommunicationUser participants[] = new CommunicationUser[]{ acsUserId };
call oneToOneCall = callAgent.call(appContext, participants, startCallOptions);
```

### <a name="place-a-1n-call-with-users-and-pstn"></a>Een aanroep van 1: n met gebruikers en PSTN plaatsen
> [!WARNING]
> Het aanroepen van de PSTN is niet beschikbaar voor het plaatsen van een 1: n-aanroep naar een gebruiker en een PSTN-nummer. u moet het telefoon nummer van de beller opgeven.
Uw communicatie service-resource moet worden geconfigureerd om PSTN-aanroepen mogelijk te maken:
```java
CommunicationUser acsUser1 = new CommunicationUser(<USER_ID>);
PhoneNumber acsUser2 = new PhoneNumber("<PHONE_NUMBER>");
CommunicationIdentifier participants[] = new CommunicationIdentifier[]{ acsUser1, acsUser2 };
StartCallOptions startCallOptions = new StartCallOptions();
Context appContext = this.getApplicationContext();
Call groupCall = callAgent.call(participants, startCallOptions);
```

### <a name="place-a-11-call-with-video-camera"></a>Een 1:1-oproep met video camera plaatsen
> [!WARNING]
> Momenteel wordt slechts één uitgaande lokale video stroom ondersteund om een gesprek met video te plaatsen die u nodig hebt om lokale camera's op te sommen met behulp van de `deviceManager` `getCameraList` API.
Wanneer u een gewenste camera hebt geselecteerd, gebruikt u deze om een instantie te maken `LocalVideoStream` en door `videoOptions` te geven als een item in de `localVideoStream` matrix naar een `call` methode.
Zodra de oproep verbinding maakt, begint automatisch met het verzenden van een video stroom van de geselecteerde camera naar een andere deel nemer (s).

> [!NOTE]
> Vanwege privacy-problemen wordt video niet gedeeld met de aanroep als deze niet lokaal wordt weer gegeven.
Zie de [voor beeld van een lokale camera](#local-camera-preview) voor meer informatie.
```java
Context appContext = this.getApplicationContext();
VideoDeviceInfo desiredCamera = callClient.getDeviceManager().get().getCameraList().get(0);
LocalVideoStream currentVideoStream = new LocalVideoStream(desiredCamera, appContext);
VideoOptions videoOptions = new VideoOptions(currentVideoStream);

// Render a local preview of video so the user knows that their video is being shared
Renderer previewRenderer = new Renderer(currentVideoStream, appContext);
View uiView = previewRenderer.createView(new RenderingOptions(ScalingMode.Fit));
// Attach the uiView to a viewable location on the app at this point
layout.addView(uiView);

CommunicationUser[] participants = new CommunicationUser[]{ new CommunicationUser("<acs user id>") };
StartCallOptions startCallOptions = new StartCallOptions();
startCallOptions.setVideoOptions(videoOptions);
Call call = callAgent.call(context, participants, startCallOptions);
```

### <a name="join-a-group-call"></a>Deelnemen aan een groepsgesprek
Als u een nieuwe groeps oproep wilt starten of lid wilt worden van een doorlopende groeps oproep, moet u de methode ' samen voegen ' aanroepen en een object door geven aan een `groupId` eigenschap. De waarde moet een GUID zijn.
```java
Context appContext = this.getApplicationContext();
GroupCallContext groupCallContext = new groupCallContext("<GUID>");
JoinCallOptions joinCallOptions = new JoinCallOptions();

call = callAgent.join(context, groupCallContext, joinCallOptions);
```

## <a name="push-notifications"></a>Pushmeldingen

### <a name="overview"></a>Overzicht
Mobiele push meldingen zijn de pop-upmeldingen die u op mobiele apparaten ziet. We richten zich op de push meldingen van VoIP (Voice-over Internet Protocol). U kunt registreren voor push meldingen, Push meldingen verwerken en vervolgens de registratie van push meldingen ongedaan maken.

### <a name="prerequisites"></a>Vereisten

Een Firebase-account dat is ingesteld met Cloud Messa ging (FCM) ingeschakeld en met uw Firebase Cloud Messa ging-service verbonden met een Azure notification hub-exemplaar. Zie [communicatie Services-meldingen](../../../concepts/notifications.md) voor meer informatie.
Daarnaast wordt door de zelf studie aangenomen dat u Android Studio versie 3,6 of hoger gebruikt om uw toepassing te bouwen.

Er is een set machtigingen vereist voor de Android-toepassing om meldings berichten te kunnen ontvangen van Firebase Cloud Messa ging. Voeg in uw `AndroidManifest.xml` bestand de volgende machtigingen toe na het *manifest<... >* of onder het *</application>* label

```XML
    <uses-permission android:name="android.permission.INTERNET"/>
    <uses-permission android:name="android.permission.GET_ACCOUNTS"/>
    <uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />
```

### <a name="register-for-push-notifications"></a>Registreren voor push meldingen

Als u zich wilt registreren voor push meldingen, moet de toepassing `registerPushNotification()` een *CallAgent* -exemplaar aanroepen met een apparaat registratie token.

Om het token voor apparaatregistratie te verkrijgen, voegt u de Firebase-client bibliotheek toe aan het bestand *Build. gradle* van uw toepassings module door de volgende regels toe te voegen in de `dependencies` sectie als deze nog niet bestaat:

```
    // Add the client library for Firebase Cloud Messaging
    implementation 'com.google.firebase:firebase-core:16.0.8'
    implementation 'com.google.firebase:firebase-messaging:20.2.4'
```

Voeg in het bestand *Build. gradle* van het project het volgende toe in de `dependencies` sectie als dit nog niet is gebeurd:

```
    classpath 'com.google.gms:google-services:4.3.3'
```

Voeg de volgende invoeg toepassing toe aan het begin van het bestand als dit nog niet is gebeurd:

```
apply plugin: 'com.google.gms.google-services'
```

Selecteer *Nu synchroniseren* in de werk balk. Voeg het volgende code fragment toe om het token voor apparaatregistratie op te halen dat door de Firebase Cloud Messa ging-client bibliotheek voor het exemplaar van de client toepassing wordt gegenereerd, en voeg de onderstaande import toe aan de koptekst van de hoofd activiteit voor het exemplaar. Ze zijn vereist voor het fragment om het token op te halen:

```
import com.google.android.gms.tasks.OnCompleteListener;
import com.google.android.gms.tasks.Task;
import com.google.firebase.iid.FirebaseInstanceId;
import com.google.firebase.iid.InstanceIdResult;
```

Voeg dit fragment toe om het token op te halen:

```
        FirebaseInstanceId.getInstance().getInstanceId()
                .addOnCompleteListener(new OnCompleteListener<InstanceIdResult>() {
                    @Override
                    public void onComplete(@NonNull Task<InstanceIdResult> task) {
                        if (!task.isSuccessful()) {
                            Log.w("PushNotification", "getInstanceId failed", task.getException());
                            return;
                        }

                        // Get new Instance ID token
                        String deviceToken = task.getResult().getToken();
                        // Log
                        Log.d("PushNotification", "Device Registration token retrieved successfully");
                    }
                });
```
Registreer het token voor apparaatregistratie met de aanroepende Services-client bibliotheek voor push meldingen voor inkomende oproepen:

```java
String deviceRegistrationToken = "<Device Token from previous section>";
try {
    callAgent.registerPushNotification(deviceRegistrationToken).get();
}
catch(Exception e) {
    System.out.println("Something went wrong while registering for Incoming Calls Push Notifications.")
}
```

### <a name="push-notification-handling"></a>Afhandeling van push meldingen

Als u push meldingen voor inkomende oproepen wilt ontvangen, roept u *handlePushNotification ()* aan voor een *CallAgent* -exemplaar met een payload.

Als u de payload van Firebase Cloud Messa ging wilt verkrijgen, begint u met het maken van een nieuwe service (bestand > nieuwe > service >-service) die de klasse *FirebaseMessagingService* Firebase-client bibliotheek uitbreidt en de methode overschrijft `onMessageReceived` . Deze methode is de gebeurtenis-handler die wordt aangeroepen wanneer Firebase Cloud Messa ging de push melding naar de toepassing levert.

```java
public class MyFirebaseMessagingService extends FirebaseMessagingService {
    private java.util.Map<String, String> pushNotificationMessageDataFromFCM;

    @Override
    public void onMessageReceived(RemoteMessage remoteMessage) {
        // Check if message contains a notification payload.
        if (remoteMessage.getNotification() != null) {
            Log.d("PushNotification", "Message Notification Body: " + remoteMessage.getNotification().getBody());
        }
        else {
            pushNotificationMessageDataFromFCM = remoteMessage.getData();
        }
    }
}
```
Voeg de volgende service definitie toe aan het `AndroidManifest.xml` bestand in de- <application> Tag:

```
        <service
            android:name=".MyFirebaseMessagingService"
            android:exported="false">
            <intent-filter>
                <action android:name="com.google.firebase.MESSAGING_EVENT" />
            </intent-filter>
        </service>
```

- Zodra de payload is opgehaald, kan deze worden door gegeven aan de *communicatie Services* -client bibliotheek die moet worden verwerkt door de methode *handlePushNotification* aan te roepen voor een *CallAgent* -exemplaar. Er `CallAgent` wordt een exemplaar gemaakt door de `createCallAgent(...)` methode aan te roepen voor de `CallClient` klasse.

```java
try {
    callAgent.handlePushNotification(pushNotificationMessageDataFromFCM).get();
}
catch(Exception e) {
    System.out.println("Something went wrong while handling the Incoming Calls Push Notifications.");
}
```

Wanneer de verwerking van het push meldings bericht is geslaagd en de handlers voor alle gebeurtenissen correct zijn geregistreerd, wordt de toepassing geringt.

### <a name="unregister-push-notifications"></a>Registratie van push meldingen ongedaan maken

Toepassingen kunnen de registratie van push meldingen op elk gewenst moment ongedaan maken. Roep de `unregisterPushNotification()` methode op callAgent aan om de registratie ongedaan te maken.

```java
try {
    callAgent.unregisterPushNotifications().get();
}
catch(Exception e) {
    System.out.println("Something went wrong while un-registering for all Incoming Calls Push Notifications.")
}
```

## <a name="call-management"></a>Oproep beheer
U hebt toegang tot de oproep eigenschappen en kunt verschillende bewerkingen uitvoeren tijdens een aanroep om instellingen te beheren die betrekking hebben op video en audio.

### <a name="call-properties"></a>Eigenschappen van oproep

De unieke ID voor deze aanroep ophalen:

```java
String callId = call.getCallId();
```

Voor meer informatie over andere deel nemers in de verzameling aanroep inspectie `remoteParticipant` op het `call` exemplaar:

```java
List<RemoteParticipant> remoteParticipants = call.getRemoteParticipants();
```

De identiteit van de aanroeper als de aanroep inkomend is:

```java
CommunicationIdentifier callerId = call.getCallerId();
```

De status van de aanroep ophalen: 

```java
CallState callState = call.getState();
```

Er wordt een teken reeks geretourneerd die de huidige status van een aanroep vertegenwoordigt:
* Geen '-initiële gespreks status
* ' Binnenkomend ': geeft aan dat de aanroep inkomend moet worden geaccepteerd of geweigerd
* ' Verbinding maken '-initiële overgangs status zodra de aanroep is geplaatst of geaccepteerd
* ' Rinkelend ': voor een uitgaande oproep wordt aangegeven dat de aanroep wordt opgeroepen voor externe deel nemers, het is een incoming-zijde
* ' EarlyMedia ': geeft een status aan waarin een aankondiging wordt afgespeeld voordat de aanroep is verbonden
* Verbonden: de oproep is verbonden
* Hold-aanroep is in de wacht stand gezet, geen medium loopt tussen het lokale eind punt en de externe deel nemer (s)
* ' Verbinding verbreken van '-de status van de overgang voor de aanroep is verbroken
* ' Verbinding verbroken '-laatste gespreks status


Inspecteer de eigenschap om te zien waarom een aanroep is beëindigd `callEndReason` . Het bevat code/subcode: 

```java
CallEndReason callEndReason = call.getCallEndReason();
int code = callEndReason.getCode();
int subCode = callEndReason.getSubCode();
```

Als u wilt zien of de huidige aanroep een binnenkomende oproep is, controleert u de `isIncoming` eigenschap:

```java
boolean isIncoming = call.getIsIncoming();
```

Als u wilt zien of de huidige microfoon is gedempt, inspecteert u de `muted` eigenschap:

```java
boolean muted = call.getIsMicrophoneMuted();
```

Als u actieve video stromen wilt controleren, controleert u de `localVideoStreams` verzameling:

```java
List<LocalVideoStream> localVideoStreams = call.getLocalVideoStreams();
```

### <a name="mute-and-unmute"></a>Dempen en dempen opheffen

U kunt de `mute` en asynchrone api's gebruiken om het lokale eind punt te dempen of te dempen `unmute` :

```java
call.mute().get();
call.unmute().get();
```

### <a name="start-and-stop-sending-local-video"></a>Verzenden van lokale video starten en stoppen

Als u een video wilt starten, moet u camera's opsommen met behulp `getCameraList` van de API voor het `deviceManager` object. Maak vervolgens een nieuw exemplaar van `LocalVideoStream` het door geven van de gewenste camera en geef deze door `startVideo` als een argument in de API:

```java
VideoDeviceInfo desiredCamera = <get-video-device>;
Context appContext = this.getApplicationContext();
currentVideoStream = new LocalVideoStream(desiredCamera, appContext);
videoOptions = new VideoOptions(currentVideoStream);
Future startVideoFuture = call.startVideo(currentVideoStream);
startVideoFuture.get();
```

Zodra u de video hebt verzonden, `LocalVideoStream` wordt een exemplaar toegevoegd aan de `localVideoStreams` verzameling op het aanroep exemplaar.

```java
currentVideoStream == call.getLocalVideoStreams().get(0);
```

Als u lokale video wilt stoppen, geeft u het `localVideoStream` exemplaar dat beschikbaar is in de `localVideoStreams` verzameling door.

```java
call.stopVideo(localVideoStream).get();
```

U kunt overschakelen naar een ander camera apparaat terwijl de video wordt verzonden door aan te roepen `switchSource` op een `localVideoStream` exemplaar:
```java
localVideoStream.switchSource(source).get();
```

## <a name="remote-participants-management"></a>Beheer van externe deel nemers

Alle externe deel nemers worden weer gegeven op `RemoteParticipant` type en zijn beschikbaar via de `remoteParticipants` verzameling op een aanroep exemplaar.

### <a name="list-participants-in-a-call"></a>Deel nemers in een gesprek weer geven
De `remoteParticipants` verzameling retourneert een lijst met externe deel nemers in de gegeven aanroep:
```java
List<RemoteParticipant> remoteParticipants = call.getRemoteParticipants(); // [remoteParticipant, remoteParticipant....]
```

### <a name="remote-participant-properties"></a>Eigenschappen van externe deel nemer
Aan alle gegeven externe deel nemers is een set eigenschappen en verzamelingen gekoppeld:

* De id voor deze externe deel nemer ophalen.
Identiteit is een van de typen ' identifier '
```java
CommunicationIdentifier participantIdentity = remoteParticipant.getIdentifier();
```

* De status van deze externe deel nemer ophalen.
```java
ParticipantState state = remoteParticipant.getState();
```
Status kan een van
* ' Inactief '-initiële status
* ' Verbinding maken '-transitie status terwijl deel nemer verbinding maakt met de aanroep
* Verbonden: de deel nemer is verbonden met de oproep
* Hold-deel nemer is in de wacht stand
* ' EarlyMedia ': de aankondiging wordt afgespeeld voordat de deel nemer is verbonden met de oproep
* ' Verbinding verbroken ': eind status-de deel nemer is losgekoppeld van de aanroep


* Als u wilt weten waarom een deel nemer de oproep heeft verlaten, inspecteert u de `callEndReason` eigenschap:
```java
CallEndReason callEndReason = remoteParticipant.getCallEndReason();
```

* Als u wilt controleren of deze externe deel nemer is gedempt of niet, inspecteert u de `isMuted` eigenschap:
```java
boolean isParticipantMuted = remoteParticipant.getIsMuted();
```

* Als u wilt controleren of deze externe deel nemer spreekt of niet, inspecteert u de `isSpeaking` eigenschap:
```java
boolean isParticipantSpeaking = remoteParticipant.getIsSpeaking();
```

* Als u alle video stromen wilt controleren die een bepaalde deel nemer in deze oproep verzendt, controleert u de `videoStreams` verzameling:
```java
List<RemoteVideoStream> videoStreams = remoteParticipant.getVideoStreams(); // [RemoteVideoStream, RemoteVideoStream, ...]
```


### <a name="add-a-participant-to-a-call"></a>Een deel nemer aan een gesprek toevoegen

Als u een deel nemer wilt toevoegen aan een aanroep (een gebruiker of een telefoon nummer), kunt u deze aanroepen `addParticipant` . Hiermee wordt het exemplaar van de externe deel nemer synchroon geretourneerd.

```java
const acsUser = new CommunicationUser("<acs user id>");
const acsPhone = new PhoneNumber("<phone number>");
RemoteParticipant remoteParticipant1 = call.addParticipant(acsUser);
RemoteParticipant remoteParticipant2 = call.addParticipant(acsPhone);
```

### <a name="remove-participant-from-a-call"></a>Deel nemer uit een gesprek verwijderen
Als u een deel nemer wilt verwijderen uit een aanroep (een gebruiker of een telefoon nummer), kunt u deze aanroepen `removeParticipant` .
Dit wordt asynchroon opgelost zodra de deel nemer is verwijderd uit de aanroep.
De deel nemer wordt ook uit de `remoteParticipants` verzameling verwijderd.
```java
RemoteParticipant remoteParticipant = call.getParticipants().get(0);
call.removeParticipant(acsUser).get();
call.removeParticipant(acsPhone).get();
```

## <a name="render-remote-participant-video-streams"></a>Video stromen voor externe deel nemers weer geven
Als u de video stromen en de streams voor het delen van externe deel nemers wilt weer geven, inspecteert u de `videoStreams` verzamelingen:
```java
RemoteParticipant remoteParticipant = call.getRemoteParticipants().get(0);
RemoteVideoStream remoteParticipantStream = remoteParticipant.getVideoStreams().get(0);
MediaStreamType streamType = remoteParticipantStream.getType(); // of type MediaStreamType.Video or MediaStreamType.ScreenSharing
```
 
Als u een `RemoteVideoStream` van een externe deel nemer wilt renderen, moet u zich abonneren op een `OnVideoStreamsUpdated` gebeurtenis.

In het geval geeft de eigenschap wijzigen `isAvailable` in waar aan dat de deel nemer momenteel een stroom verzendt. Als dit het geval is, maakt u een nieuw exemplaar van a en `Renderer` vervolgens maakt u een nieuwe sessie `RendererView` met asynchrone `createView` API en koppelt u deze `view.target` overal in de gebruikers interface van uw toepassing.

Wanneer de beschik baarheid van een externe stroom verandert, kunt u ervoor kiezen om de volledige renderer te vernietigen, een specifieke `RendererView` of te blijven gebruiken, maar dit resulteert in het weer geven van een leeg video frame.

```java
Renderer remoteVideoRenderer = new Renderer(remoteParticipantStream, appContext);
View uiView = remoteVideoRenderer.createView(new RenderingOptions(ScalingMode.Fit));
layout.addView(uiView);

remoteParticipant.addOnVideoStreamsUpdatedListener(e -> onRemoteParticipantVideoStreamsUpdated(p, e));

void onRemoteParticipantVideoStreamsUpdated(RemoteParticipant participant, RemoteVideoStreamsEvent args) {
    for(RemoteVideoStream stream : args.getAddedRemoteVideoStreams()) {
        if(stream.getIsAvailable()) {
            startRenderingVideo();
        } else {
            renderer.dispose();
        }
    }
}
```

### <a name="remote-video-stream-properties"></a>Eigenschappen van externe video-stream
De externe video stroom heeft een aantal eigenschappen

* `Id` -ID van een externe video stroom
```java
int id = remoteVideoStream.getId();
```

* `MediaStreamType` -Kan ' video ' of ' ScreenSharing ' zijn
```java
MediaStreamType type = remoteVideoStream.getType();
```

* `isAvailable` -Geeft aan of het eind punt van de externe deel nemer actief stroom verzendt
```java
boolean availability = remoteVideoStream.getIsAvailable();
```

### <a name="renderer-methods-and-properties"></a>Methoden en eigenschappen van renderer
Renderer-object na Api's

* Maak een `RendererView` exemplaar dat later kan worden gekoppeld in de gebruikers interface van de toepassing om externe video stroom weer te geven.
```java
// Create a view for a video stream
renderer.createView()
```
* De renderer en alle `RendererView` aan deze renderer verwijderen. Moet worden aangeroepen wanneer u alle gekoppelde weer gaven uit de gebruikers interface hebt verwijderd.
```java
renderer.dispose()
```

* `StreamSize` -grootte (breedte/hoogte) van een externe video stroom
```java
StreamSize renderStreamSize = remoteVideoStream.getSize();
int width = renderStreamSize.getWidth();
int height = renderStreamSize.getHeight();
```


### <a name="rendererview-methods-and-properties"></a>RendererView methoden en eigenschappen
Bij het maken van een `RendererView` kunt u `scalingMode` de `mirrored` Eigenschappen en opgeven die van toepassing zijn op deze weer gave: de schaal modus kan de waarde stretch hebben | ' Bijsnijden ' | ' Fit ' als `mirrored` is ingesteld op `true` , wordt de gerenderde stroom verticaal gespiegeld.

```java
Renderer remoteVideoRenderer = new Renderer(remoteVideoStream, appContext);
RendererView rendererView = remoteVideoRenderer.createView(new RenderingOptions(ScalingMode.Fit));
```

De gemaakte RendererView kan vervolgens worden gekoppeld aan de gebruikers interface van de toepassing met behulp van het volgende code fragment:
```java
layout.addView(rendererView);
```

U kunt de schaal modus later bijwerken door de API aan te roepen `updateScalingMode` voor het object RendererView met een van ScalingMode. Stretch | ScalingMode. gewas | ScalingMode. fit als een argument.
```java
// Update the scale mode for this view.
rendererView.updateScalingMode(ScalingMode.Crop)
```


## <a name="device-management"></a>Apparaatbeheer

`DeviceManager` Hiermee kunt u lokale apparaten opsommen die kunnen worden gebruikt in een aanroep om uw audio/video-streams te verzenden. U kunt hiermee ook machtigingen aanvragen van een gebruiker om toegang te krijgen tot hun microfoon en camera met behulp van de systeem eigen browser-API.

U kunt toegang krijgen `deviceManager` door middel van een aanroep `callClient.getDeviceManager()` methode.
> [!WARNING]
> Momenteel `callAgent` moet een object eerst worden geïnstantieerd om toegang te krijgen tot DeviceManager

```java
DeviceManager deviceManager = callClient.getDeviceManager().get();
```

### <a name="enumerate-local-devices"></a>Lokale apparaten opsommen

Voor toegang tot lokale apparaten kunt u inventarisatie methoden gebruiken op de Apparaatbeheer. Opsomming is een synchrone actie.

```java
//  Get a list of available video devices for use.
List<VideoDeviceInfo> localCameras = deviceManager.getCameraList(); // [VideoDeviceInfo, VideoDeviceInfo...]

// Get a list of available microphone devices for use.
List<AudioDeviceInfo> localMicrophones = deviceManager.getMicrophoneList(); // [AudioDeviceInfo, AudioDeviceInfo...]

// Get a list of available speaker devices for use.
List<AudioDeviceInfo> localSpeakers = deviceManager.getSpeakerList(); // [AudioDeviceInfo, AudioDeviceInfo...]
```

### <a name="set-default-microphonespeaker"></a>Standaard microfoon/-spreker instellen

Met Apparaatbeheer kunt u een standaard apparaat instellen dat wordt gebruikt bij het starten van een aanroep.
Als de standaard waarden van de client niet zijn ingesteld, worden de standaard instellingen van het besturings systeem hersteld door communicatie Services.

```java

// Get the microphone device that is being used.
AudioDeviceInfo defaultMicrophone = deviceManager.getMicrophoneList().get(0);

// Set the microphone device to use.
deviceManager.setMicrophone(defaultMicrophone);

// Get the speaker device that is being used.
AudioDeviceInfo defaultSpeaker = deviceManager.getSpeakerList().get(0);

// Set the speaker device to use.
deviceManager.setSpeaker(defaultSpeaker);
```

### <a name="local-camera-preview"></a>Voor beeld van lokale camera

U kunt `DeviceManager` en gebruiken `Renderer` om streams van uw lokale camera te renderen. Deze stroom wordt niet naar andere deel nemers verzonden. het is een lokale preview-feed. Dit is een asynchrone actie.

```java
VideoDeviceInfo videoDevice = <get-video-device>;
Context appContext = this.getApplicationContext();
currentVideoStream = new LocalVideoStream(videoDevice, appContext);
videoOptions = new VideoOptions(currentVideoStream);

Renderer previewRenderer = new Renderer(currentVideoStream, appContext);
View uiView = previewRenderer.createView(new RenderingOptions(ScalingMode.Fit));

// Attach the uiView to a viewable location on the app at this point
layout.addView(uiView);
```

## <a name="eventing-model"></a>Gebeurtenis model
U kunt zich abonneren op de meeste eigenschappen en verzamelingen om te worden gewaarschuwd wanneer waarden worden gewijzigd.

### <a name="properties"></a>Eigenschappen
Abonneren op `property changed` gebeurtenissen:

```java
// subscribe
PropertyChangedListener callStateChangeListener = new PropertyChangedListener()
{
    @Override
    public void onPropertyChanged(PropertyChangedEvent args)
    {
        Log.d("The call state has changed.");
    }
}
call.addOnCallStateChangedListener(callStateChangeListener);

//unsubscribe
call.removeOnCallStateChangedListener(callStateChangeListener);
```

### <a name="collections"></a>Verzamelingen
Abonneren op `collection updated` gebeurtenissen:

```java
LocalVideoStreamsChangedListener localVideoStreamsChangedListener = new LocalVideoStreamsChangedListener()
{
    @Override
    public void onLocalVideoStreamsUpdated(LocalVideoStreamsEvent localVideoStreamsEventArgs) {
        Log.d(localVideoStreamsEventArgs.getAddedStreams().size());
        Log.d(localVideoStreamsEventArgs.getRemovedStreams().size());
    }
}
call.addOnLocalVideoStreamsChangedListener(localVideoStreamsChangedListener);
// To unsubscribe
call.removeOnLocalVideoStreamsChangedListener(localVideoStreamsChangedListener);
```