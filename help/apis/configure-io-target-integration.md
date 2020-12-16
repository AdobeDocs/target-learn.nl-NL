---
title: Verificatie configureren voor Adobe Target API's
keywords: recommendations;adobe recommendations;premium;api;apis
description: Adobe Target Recommendations bevat een specifieke set API's waarmee u uw catalogus met aanbevolen producten en/of inhoud kunt beheren. uw aanbevelingen, algoritmen en campagnes beheren; en aanbevelingen doen in JSON-, HTML- of XML-objecten die moeten worden weergegeven in webkanalen, mobiele apparaten, e-mail, IOT en andere kanalen.
kt: null
audience: developer
doc-type: tutorial
activity: use
feature: api
topics: recommendations;adobe recommendations;premium;api;apis
solution: Target
author: Judy Kim
translation-type: tm+mt
source-git-commit: 624172d4bc4bc2431ad8af0956c93d3bcc0b9870
workflow-type: tm+mt
source-wordcount: '1834'
ht-degree: 2%

---


# Verificatie voor Adobe Target API&#39;s configureren

De Adobe Target Admin API&#39;s, inclusief [!DNL Recommendations] Admin API&#39;s, worden via verificatie beveiligd om ervoor te zorgen dat alleen geautoriseerde gebruikers deze API&#39;s gebruiken om toegang te krijgen tot Adobe Target. Gebruik [Adobe Developer Console](https://console.adobe.io/) om deze verificatie te beheren voor alle Adobe Experience Cloud-oplossingen, inclusief [!DNL Target].

In deze les worden de voorafgaande stappen doorlopen die nodig zijn om verificatietokens te genereren die nodig zijn om te kunnen communiceren met Adobe Target API&#39;s. In de volgende secties gaat u:

1. Creeer een project (eerder genoemd integratie) in de Console van de Ontwikkelaar van de Adobe.
2. Exporteer projectdetails naar Postman.
3. Genereer een toegangstoken voor toonder.
4. Test het toegangstoken van de drager.

## Voorwaarden

| Resource | Details |
| --- | --- |
| Postman | Als u deze stappen met succes wilt uitvoeren, haalt u de [Postman-app](https://www.postman.com/downloads/) voor uw besturingssysteem op. Postman basic is free with account creation. Hoewel dit niet nodig is voor het gebruik van Adobe Target API&#39;s in het algemeen, maakt Postman API-workflows eenvoudiger en biedt Adobe Target verschillende Postman-verzamelingen om de API&#39;s van Postman uit te voeren en te leren hoe deze werken. De rest van deze zelfstudie gaat uit van praktische kennis van Postman. Raadpleeg de [Postman-documentatie](https://learning.getpostman.com/) voor hulp. |
| Verwijzingen | Gedurende de rest van deze zelfstudie wordt aangenomen dat u bekend bent met de volgende bronnen:<UL><li>[Adobe I/O Github](https://github.com/adobeio)</li><li>[Doeldocumentatie voor Adobe I/O](https://developers.adobetarget.com/api/#introduction)</li><li>[Recommendations API-documentatie](https://developers.adobetarget.com/api/recommendations/)</li></ul> |

## Een Adobe I/O-project maken

In deze sectie krijgt u toegang tot de Adobe Developer Console en maakt u een project voor [!DNL Adobe Target]. Raadpleeg de [documentatie over projecten](https://www.adobe.io/apis/experienceplatform/console/docs.html#!AdobeDocs/adobeio-console/master/projects.md) voor meer informatie.

<!--1. Generate your private key and public certificate, per the [documentation on authentication](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWTCertificate.md). //<!--as described in **Step 1** of [How to set up Adobe IO: Authentication - Step by Step](https://helpx.adobe.com/marketing-cloud-core/kb/adobe-io-authentication-step-by-step.html). After completing Step 1, return to this tutorial and resume with Step 2, below. // The outcome of this step should be the creation of a `private.key` file and a `certificate_pub.crt` file. Return to this tutorial once you have generated these two files.-->

1. Zorg er in [Adobe Admin Console](https://adminconsole.adobe.com/) voor dat uw Adobe-gebruikersaccount zowel [Product Admin](https://helpx.adobe.com/enterprise/using/admin-roles.html) als [Developer](https://helpx.adobe.com/enterprise/using/manage-developers.html) toegang tot [!DNL Target]-niveau heeft.

2. Selecteer in [Adobe Developer Console](https://console.adobe.io/) de Experience Cloud Organisatie waarvoor u deze integratie wilt maken. (Let op: u hebt waarschijnlijk slechts toegang tot één Experience Cloud-organisatie.)

   ![configure-io-target-create project2.png](assets/configure-io-target-createproject2.png)

3. Klik op **[!UICONTROL Create new project]**.

   ![configure-io-target-create project3.png](assets/configure-io-target-createproject3.png)

4. Klik **[!UICONTROL Add API]** om REST API aan uw project toe te voegen om tot de diensten en de producten van de Adobe toegang te hebben.

   ![API toevoegen](assets/configure-io-target-createproject4.png)

5. Selecteer **[!DNL Adobe Target]** als de service Adobe waarmee u wilt integreren. Klik op de knop **[!UICONTROL Next]** die wordt weergegeven.

   ![configure-io-target-create project5](assets/configure-io-target-createproject5.png)

6. Selecteer een optie voor het koppelen van openbare en persoonlijke sleutels aan de integratie van de de dienstrekening u voor Doel creeert. Selecteer **[!UICONTROL Option 1: Generate a key pair]** voor deze zelfstudie en klik op **[!UICONTROL Generate keypair]**.
   ![configure-io-target-createproject6](assets/configure-io-target-createproject6.png)

7. Noteer het resultaat! Zoals geïnstrueerd, neem nota van het automatisch gedownloade configuratiedossier (`config`), dat uw privé sleutel bevat. Klik op **[!UICONTROL Next]**.
   ![configure-io-target-createproject7](assets/configure-io-target-createproject7.png)
8. Controleer in uw bestandssysteem de locatie van `config`. Dit is het gecomprimeerde configuratiebestand dat in de vorige stap is gemaakt. Opnieuw bevat dit `config`-bestand uw persoonlijke sleutel, die u later nodig hebt. De exacte locatie in uw bestandssysteem kan afwijken van de locatie die u hier ziet.
   ![configure-io-target-createproject8](assets/configure-io-target-createproject8.png)
9. Selecteer vervolgens in de Adobe Developer Console het [productprofiel(en)](https://helpx.adobe.com/enterprise/using/manage-products-and-profiles.html) dat overeenkomt met de eigenschappen waarin u [!DNL Recommendations] gebruikt. (Als u geen eigenschappen gebruikt, selecteert u de optie Standaardwerkruimte.) Klik op **[!UICONTROL Save configured API]**.
   ![configure-io-target-create project9](assets/configure-io-target-createproject9.png)

10. Klik op **[!UICONTROL Create Integration]**. U ontvangt een tijdelijk bericht dat aangeeft dat de API is geconfigureerd.

11. Als laatste stap wijzigt u de naam van het project in een naam die betekenisvoller is dan de naam van het origineel. `Project 1` Om dit te doen, navigeer aan het project gebruikend de navigatiepad zoals getoond, klik **[!UICONTROL Edit project]** om tot **[!UICONTROL Edit Project] modaal toegang te hebben, en noem het project anders.

![configure-io-target-create project11](assets/configure-io-target-createproject11.png)

>[!NOTE]
> 
>In deze zelfstudie noemen we ons project &#39;Doelintegratie&#39;. Als u uw project voor meer dan enkel Adobe Target wilt gebruiken, kunt u het dienovereenkomstig willen noemen. U kunt er bijvoorbeeld voor kiezen om de naam &quot;Adobe API&#39;s&quot; of &quot;Experience Cloud API&#39;s&quot; te geven, omdat deze API&#39;s kunnen worden gebruikt met andere oplossingen in de Adobe Experience Cloud.

## Projectdetails exporteren

Nu u een Adobe project hebt u voor de toegang tot van [!DNL Target] kunt gebruiken, moet u ervoor zorgen om details van dat project samen met uw Adobe API verzoeken te verzenden. Deze gegevens zijn vereist voor interactie met verschillende API&#39;s voor Adobe, waaronder verschillende API&#39;s voor [!DNL Target]. De integratiegegevens bevatten bijvoorbeeld autorisatie- en verificatiegegevens die vereist zijn voor de Admin API&#39;s van [!DNL Target]. Als u de API&#39;s met Postman wilt gebruiken, moet u deze gegevens daarom naar Postman sturen.

Er zijn vele manieren om de details van uw project in Postman te specificeren, maar in deze sectie, profiteren wij van sommige pre-gebouwde eigenschappen en inzamelingen. Eerst (in deze sectie) exporteert u de details van uw integratie naar een Postman-omgeving. Daarna (in de volgende sectie), zult u een dragertoegangstoken produceren om u toegang tot de noodzakelijke middelen van Adobe te verlenen.

>[!NOTE]
>
>Zie [Postman gebruiken met Experience Platform-API&#39;s](https://docs.adobe.com/content/help/en/platform-learn/tutorials/apis/postman.html) voor video-instructies die van toepassing zijn op elke Experience Cloud-oplossing, inclusief [!DNL Target]. De volgende secties zijn relevant voor de [!DNL Target] APIs:
>
> 1. Adobe I/O Integration Details exporteren naar Postman
> 2. Een toegangstoken met Postman genereren

>
> 
Deze stappen worden ook hieronder gegeven.

1. Nog in [Adobe de Console van de Ontwikkelaar](https://console.adobe.io/), navigeer om de geloofsbrieven van **[!UICONTROL Service Account (JWT)]** van uw nieuw project te bekijken. Gebruik de linkernavigatie of de sectie **[!UICONTROL Credentials]** zoals getoond.
   ![JWT1](assets/configure-io-target-jwt1.png)
In  **[!UICONTROL Credential details]** kunt u uw  **openbare sleutel(s)**,  **Cliënt ID**, en andere informatie bekijken met betrekking tot uw de dienstrekening.
   ![JWT1a](assets/configure-io-target-jwt1a.png)
2. Klik om naar informatie over de **[!UICONTROL Adobe Target]** API te navigeren. Gebruik de linkernavigatie of de sectie **[!UICONTROL Connected products and services]** zoals getoond.
   ![JWT2](assets/configure-io-target-jwt2.png)
3. Klik op **[!UICONTROL Download for Postman]** > **[!UICONTROL Service Account (JWT)]** om een JSON-bestand te maken waarin uw verificatiegegevens voor een Postman-omgeving worden vastgelegd.
   ![JWT3](assets/configure-io-target-jwt3.png)
Noteer het JSON-bestand in uw bestandssysteem.
   ![JWT3a](assets/configure-io-target-jwt3a.png)
4. Klik in Postman op het tandwielpictogram om uw omgevingen te beheren en klik vervolgens op **Importeren** om het JSON-bestand (omgeving) te importeren.
   ![JWT4](assets/configure-io-target-jwt4.png)
5. Kies het bestand en klik op **Openen**.
   ![JWT5](assets/configure-io-target-jwt5.png)
6. Klik in het modaal Postman **Omgevingen beheren** op de naam van de nieuw geïmporteerde omgeving om deze te inspecteren. (De naam van uw omgeving kan verschillen van de naam die u hier ziet. Bewerk de naam naar wens. Dit hoeft niet noodzakelijkerwijs overeen te komen met de naam van het Adobe-project.)
   ![JWT6](assets/configure-io-target-jwt6.png)
7. Opmerking `CLIENT_SECRET` en `API_KEY` (samen met andere variabelen) hebben hun waarden vooraf ingevuld, ontleend aan uw integratie zoals gedefinieerd in de Adobe Developer Console. (De Postman `CLIENT_SECRET`-variabele moet overeenkomen met de `CLIENT SECRET` Adobe-referentie die wordt weergegeven in de Developer Console en `API_KEY` in Postman moet `CLIENT ID` in de Developer Console evenzo overeenkomen.) Notitie `PRIVATE_KEY`, `JWT_TOKEN` en `ACCESS_TOKEN` zijn daarentegen leeg. Laten we beginnen met het opgeven van de waarde `PRIVATE_KEY`.
   ![JWT7](assets/configure-io-target-jwt7.png)

   >[!NOTE]
   >
   >**Verrassend!**
   >
   >Pop-quiz! Kunt u zich herinneren waar uw persoonlijke sleutel is?
   >Dat klopt, het is in het `config` dossier eerder van de Console van de Ontwikkelaar van de Adobe wordt gedownload!

8. Open vanuit uw bestandssysteem het `config`-bestand en open het `private`-sleutelbestand.
   ![JWT8](assets/configure-io-target-jwt8.png)
9. Selecteer en kopieer de volledige inhoud van het `private` zeer belangrijke dossier.
   ![JWT9](assets/configure-io-target-jwt9.png)
10. Plak in Postman uw waarde voor de persoonlijke sleutel in de velden **INITIËLE WAARDE** en **HUIDIGE WAARDE**.
   ![JWT10](assets/configure-io-target-jwt10.png)
11. Klik op **[!UICONTROL Update]** en sluit het modaal milieu.


## Het toegangstoken voor toonder genereren

In deze sectie genereert u uw toegangstoken aan toonder, die nodig is voor het verifiëren van uw interactie met Adobe Target API&#39;s. Als u uw toegangstoken aan toonder wilt genereren, moet u uw integratiegegevens (die in de voorgaande secties zijn vastgelegd) naar de [Adobe Identity Management Service (IMS)](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/AuthenticationGuide.md) verzenden. Er zijn een paar verschillende manieren om dit te doen, maar in deze zelfstudie kunt u een verzoek voor een POST op maat maken voor de IMS API. Grapje. In deze zelfstudie maken we gebruik van een Postman-collectie met een vooraf gebouwde IMS-aanroep die het proces direct en eenvoudig maakt. Nadat u de verzameling hebt geïmporteerd, kunt u deze desgewenst opnieuw gebruiken om nieuwe tokens te genereren, niet alleen voor Adobe Target, maar ook voor andere Adobe-API&#39;s.

1. Navigeer naar de [Adobe Identity Management Service API voorbeeldaanroepen](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims).
   ![token1](assets/configure-io-target-generatetoken1.png)
2. Klik op de verzameling **Adobe I/O Access Token Generation Postman**.
   ![token2](assets/configure-io-target-generatetoken2.png)
3. Haal de onbewerkte JSON voor deze verzameling op door op **Raw** te klikken en de resulterende JSON vervolgens naar het klembord te kopiëren. (U kunt de onbewerkte JSON ook opslaan als een .json-bestand.)
   ![token3](assets/configure-io-target-generatetoken3.png)
4. Importeer de verzameling in Postman door de onbewerkte JSON vanaf het Klembord te plakken en in te dienen. (U kunt ook het .json-bestand uploaden dat u hebt opgeslagen.) Klik **Doorgaan**.
   ![token4](assets/configure-io-target-generatetoken4.png)
5. Selecteer **[!UICONTROL IMS: JWT Generate + Auth via User Token]** verzoek in de inzameling van Postman van de Generatie van de Token van de Toegang van Adobe I/O, zorg ervoor uw milieu wordt geselecteerd, en klik **Send** om het teken te produceren.

   ![token5](assets/configure-io-target-generatetoken5.png)

   >[!NOTE]
   >
   >Dit toegangsteken aan toonder is 24 uur geldig. Verzend het verzoek opnieuw wanneer u een nieuw teken moet produceren.

6. Open nogmaals het modaal van Milieu&#39;s beheren en selecteer uw milieu.
   ![token6](assets/configure-io-target-jwt11.png)
7. De waarden `ACCESS_TOKEN` en `JWT_TOKEN` zijn nu ingevuld.
   ![token7](assets/configure-io-target-generatetoken7.png)

>[!NOTE]
>
>V: Moet ik de inzameling van Postman van de Generatie van de Token van de Toegang van Adobe I/O gebruiken om de Token van het Web van JSON (JWT) en het toegangstoken van de tokentoken van de token van de Drager te produceren?
>
>A: Nee! De inzameling van Postman van de Generatie van de Token van de Toegang van Adobe I/O is beschikbaar als gemak om JWT en het toegangstoken van de toonder gemakkelijker te produceren in Postman. U kunt ook de mogelijkheden in de Adobe Developer Console gebruiken om het toegangstoken voor toonder handmatig te genereren.

## Test het toegangstoken aan toonder

In deze oefening, zult u uw nieuwe toegangstoken van de toonder gebruiken door een API verzoek te verzenden dat een lijst van activiteiten van uw [!DNL Target] rekening terugwint. Een geslaagde reactie geeft aan dat uw Adobe-project en -verificatie naar behoren werken om de API te kunnen gebruiken.

1. Importeer de [Adobe Target Admin API&#39;s Postman Collection](https://developers.adobetarget.com/api/#admin-postman-collection). Volg alle herinneringen tot de inzameling in Postman wordt ingevoerd.
   ![testtoken1](assets/configure-io-target-testtoken0.png)
1. Breid de inzameling uit, en neem nota van **[!UICONTROL List activities]** verzoek.
   ![testtoken1](assets/configure-io-target-testtoken1.png)
1. Variabelen zoals `{{access_token}}` zijn aanvankelijk niet opgelost. U kon dit op verscheidene verschillende manieren oplossen-voor voorbeeld, kon u een nieuwe inzamelingsvariabele genoemd `{{access_token}}`-maar in dit leerprogramma, zult u in plaats daarvan het API verzoek veranderen om hefboomwerking het milieu van Postman te gebruiken u eerder gebruikte. Hierdoor kan de omgeving blijven fungeren als één consistente consolidatie van alle variabelen die op Adobe-API&#39;s voorkomen.
   ![testtoken2](assets/configure-io-target-testtoken2.png)
1. Typ om `{{access_token}}` te vervangen door `{{ACCESS_TOKEN}}`.
   ![testtoken3](assets/configure-io-target-testtoken3.png)
1. Typ om `{{api_key}}` te vervangen door `{{API_KEY}}`.
   ![testtoken4](assets/configure-io-target-testtoken4.png)
1. Typ om `{{tenant}}` te vervangen door `{{TENANT_ID}}`. Opmerking `{{TENANT_ID}}` wordt nog niet herkend.
   ![testtoken4](assets/configure-io-target-testtoken4a.png)
1. Open het modaal beheer van milieu&#39;s, en selecteer uw milieu.
   ![JWT11](assets/configure-io-target-jwt11.png)
1. Typ om een nieuwe `{{TENANT_ID}}` omgevingsvariabele toe te voegen. Kopieer en plak uw waarde van identiteitskaart van de Huurder in **INITIËLE WAARDE** en **HUIDIGE WAARDE** gebieden voor uw nieuwe `TENANT_ID` omgevingsvariabele.

   ![testtoken5](assets/configure-io-target-testtoken5.png)

   >[!NOTE]
   >
   >De huurder-id verschilt van uw [!DNL Target] `clientcode`. De huurder-id bestaat in de URL wanneer u bent aangemeld bij [!DNL Target]. Om uw identiteitskaart van de Aannemer te verkrijgen, login aan [!DNL Adobe Experience Cloud], open [!DNL Target], en klik [!DNL Target] kaart. Gebruik de waarde van de huurder-id zoals vermeld in het URL-subdomein.
   >
   >Stel bijvoorbeeld dat uw URL bij aanmelding bij Adobe Target
   >
   >`<https://mycompany.experiencecloud.adobe.com/...>`
   >
   >Dan is je Tenant ID &quot;mijnbedrijf&quot;.

1. Verzend uw verzoek nadat u de juiste omgeving hebt geselecteerd. U ontvangt een reactie met uw lijst met activiteiten.
   ![testtoken6](assets/configure-io-target-testtoken6.png)

Gefeliciteerd! Nu u uw Adobe-verificatie hebt geverifieerd, kunt u deze gebruiken om te communiceren met Adobe Target API&#39;s (en andere Adobe API&#39;s). U kunt bijvoorbeeld [Recommendations API&#39;s](https://docs.adobe.com/content/help/en/target-learn/recommendations-api-tutorial/recs-api-overview.html) gebruiken om aanbevelingen te maken of te beheren.
