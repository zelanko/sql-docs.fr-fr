---
title: Page Avancé des Propriétés du serveur | Microsoft Docs
description: Utilisez la page Avancé des Propriétés du serveur pour définir des propriétés système sur le serveur de rapports. Cet outil fournit une interface utilisateur graphique afin que vous puissiez définir des propriétés sans écrire du code.
author: maggiesMSFT
ms.author: maggies
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
ms.date: 01/28/2020
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: d1bfbb7a1abb13df05ce402fa79a1598ee04ca1f
ms.sourcegitcommit: ff1bd69a8335ad656b220e78acb37dbef86bc78a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78340391"
---
# <a name="server-properties-advanced-page---power-bi-report-server--reporting-services"></a>Page Avancé des Propriétés du serveur - Serveur de rapports Power BI et Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

Utilisez cette page pour définir des propriétés système sur le serveur de rapports. Il existe plusieurs façons de définir des propriétés système. Cet outil fournit une interface utilisateur graphique afin que vous puissiez définir des propriétés sans devoir écrire du code.

Pour ouvrir cette page, démarrez SQL Server Management Studio, connectez-vous à une instance de serveur de rapports, cliquez avec le bouton droit sur le nom du serveur de rapports, puis sélectionnez **Propriétés**. Sélectionnez **Avancé** pour ouvrir cette page.

## <a name="options"></a>Options

### <a name="accesscontrolallowcredentials"></a>AccessControlAllowCredentials
(Serveur de rapports Power BI, Reporting Services 2017 et versions ultérieures uniquement) Indique si la réponse à la demande du client peut être exposée lorsque l’indicateur `credentials` a la valeur true. La valeur par défaut est **false**.

### <a name="accesscontrolallowheaders"></a>AccessControlAllowHeaders
(Serveur de rapports Power BI, Reporting Services 2017 et versions ultérieures uniquement) Liste séparée par des virgules des en-têtes autorisés par le serveur quand un client soumet une requête. Cette propriété peut être une chaîne vide. Spécifiez * pour autoriser tous les en-têtes.

### <a name="accesscontrolallowmethods"></a>AccessControlAllowMethods
(Serveur de rapports Power BI, Reporting Services 2017 et versions ultérieures uniquement) Liste séparée par des virgules des méthodes HTTP autorisées par le serveur quand un client soumet une requête. Les valeurs par défaut sont GET, PUT, POST, PATCH, DELETE. Spécifiez * pour autoriser toutes les méthodes.

### <a name="accesscontrolalloworigin"></a>AccessControlAllowOrigin
(Serveur de rapports Power BI, Reporting Services 2017 et versions ultérieures uniquement) Liste séparée par des virgules des origines autorisées par le serveur quand un client soumet une requête. La valeur par défaut est vide, ce qui empêche toutes les requêtes. Spécifiez * pour autoriser toutes les origines quand les informations d’identification ne sont pas définies. Si les informations d’identification sont spécifiées, une liste explicite d’origines doit être indiquée.

### <a name="accesscontrolexposeheaders"></a>AccessControlExposeHeaders
(Serveur de rapports Power BI, Reporting Services 2017 et versions ultérieures uniquement) Liste séparée par des virgules des en-têtes que le serveur exposera aux clients. La valeur par défaut est vide.

### <a name="accesscontrolmaxage"></a>AccessControlMaxAge
(Serveur de rapports Power BI, Reporting Services 2017 et versions ultérieures uniquement) Indique le nombre de secondes pendant lequel les résultats de la demande préliminaire peuvent être mis en cache. La valeur par défaut est 600 (10 minutes).

### <a name="allowedresourceextensionsforupload"></a>AllowedResourceExtensionsForUpload
(Serveur de rapports Power BI, Reporting Services 2017 et versions ultérieures uniquement) Définit des extensions de ressources qui peuvent être chargées sur le serveur de rapports. Les extensions pour les types de fichiers intégrés comme &ast;.rdl et &ast;.pbix ne doivent pas obligatoirement être incluses. La valeur par défaut est « &ast;, &ast;.xml, &ast;.xsd, &ast;.xsl, &ast;.png, &ast;.gif, &ast;.jpg, &ast;.tif, &ast;.jpeg, &ast;.tiff, &ast;.bmp, &ast;.pdf, &ast;.svg, &ast;.rtf, &ast;.txt, &ast;.doc, &ast;.docx, &ast;.pps, &ast;.ppt, &ast;.pptx ».

### <a name="customheaders"></a>CustomHeaders 

(Serveur de rapports Power BI Janvier 2020, Reporting Services 2019 et versions ultérieures uniquement)

Définit des valeurs d’en-tête pour toutes les URL correspondant au modèle d’expression régulière spécifié. Les utilisateurs peuvent mettre à jour la valeur CustomHeaders avec du code XML valide pour définir les valeurs d’en-tête des URL de demande sélectionnées. Les administrateurs peuvent ajouter n’importe quel nombre d’en-têtes dans le code XML. Par défaut, il n’y a pas d’en-tête personnalisé et la valeur est vide. 

> [!NOTE]
> Le fait d’avoir trop d’en-têtes peut avoir un impact sur les performances. 

Nous vous recommandons de valider la configuration de votre topologie pour vous assurer que l’ensemble des en-têtes est compatible avec votre déploiement de Reporting Services. Il est possible de choisir des paramètres qui provoquent des erreurs dans les navigateurs qui n’ont pas non plus les paramètres appropriés. Par exemple, vous ne devez pas ajouter de configuration HSTS si votre serveur n’est pas configuré pour le protocole https. Les en-têtes incompatibles peuvent entraîner des erreurs de rendu du navigateur.

#### <a name="customheaders-xml-format"></a>Format XML CustomHeaders

```xml
<CustomHeaders>
    <Header>
        <Name>{Name of the header}</Name>
        <Pattern>{Regex pattern to match URLs}</Pattern>
        <Value>{Value of the header}</Value>
    </Header>
</CustomHeaders>
```

#### <a name="setting-the-customheaders-property"></a>Définition de la propriété CustomHeaders

- Vous pouvez la définir à l’aide du point de terminaison SOAP [SetSystemProperties](https://docs.microsoft.com/dotnet/api/reportservice2010.reportingservice2010.setsystemproperties) en passant la propriété CustomHeaders comme paramètre.
- Vous pouvez utiliser le point de terminaison REST [UpdateSystemProperties](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0#/System/UpdateSystemProperties) : `/System/Properties` passant la propriété CustomHeaders

#### <a name="example"></a>Exemple

L’exemple ci-dessous montre comment définir HSTS et d’autres en-têtes personnalisés pour les URL avec un modèle d’expression régulière correspondant.

```xml
<CustomHeaders>
    <Header>
        <Name>Strict-Transport-Security</Name>
        <Pattern>\/Reports\/mobilereport</Pattern>
        <Value>max-age=86400</Value>
    </Header>
    <Header>
        <Name>Embed</Name>
        <Pattern>(.+)(/reports/)(.+)(rs:embed=true)</Pattern>
        <Value>True</Value>
    </Header>
</CustomHeaders>
```

Le premier en-tête dans le code XML ci-dessus ajoute l’en-tête `Strict-Transport-Security: max-age=86400` aux demandes correspondantes.
- http://adventureworks/Reports/mobilereport/New%20Mobile%20Report - L’expression régulière correspond et va définir l’en-tête HSTS
- http://adventureworks/ReportServer/mobilereport/New%20Mobile%20Report - Échec de la correspondance

Le deuxième en-tête dans le code XML ci-dessus ajoute l’en-tête `Embed: True` pour l’URL qui contient les paramètres de requête `/reports/` et `rs:embed=true`.
- https://adventureworks/reports/mobilereport/New%20Mobile%20Report?rs:embed=true - Correspondance
- https://adventureworks/reports/mobilereport/New%20Mobile%20Report?rs:embed=false - Échec de la correspondance

### <a name="editsessioncachelimit"></a>EditSessionCacheLimit
Spécifie le nombre des entrées de cache de données qui peuvent être actives dans une session d'édition de rapport. La valeur par défaut est 5.  

### <a name="editsessiontimeout"></a>EditSessionTimeout
Spécifie le nombre de secondes jusqu'à l'expiration d'une session d'édition de rapport. La valeur par défaut est 7 200 secondes (deux heures). 

### <a name="enablecdnvisuals"></a>EnableCDNVisuals 
(Serveur de rapports Power BI uniquement) Lorsque cette option est activée, les rapports Power BI chargent les derniers visuels personnalisés certifiés à partir d’un réseau de distribution de contenu (CDN) hébergé par Microsoft. Si votre serveur n’a pas accès aux ressources Internet, vous pouvez désactiver cette option. Dans ce cas, les visuels personnalisés sont chargés à partir du rapport qui a été publié sur le serveur. La valeur par défaut est **True**.  

###  <a name="enableclientprinting"></a>EnableClientPrinting  
Détermine si le contrôle ActiveX RSClientPrint peut être téléchargé à partir du serveur de rapports. Les valeurs valides sont **true** et **false**. La valeur par défaut est **true**. Pour plus d’informations sur les paramètres supplémentaires nécessaires pour ce contrôle, consultez [Activer et désactiver l’impression côté client pour Reporting Services](../../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  

### <a name="enablecustomvisuals"></a>EnableCustomVisuals 
(Serveur de rapports Power BI uniquement) Pour activer l’affichage des visuels personnalisés Power BI. Les valeurs sont True/False. *La valeur par défaut est True.*  

###  <a name="enableexecutionlogging"></a>EnableExecutionLogging  
Indique si la journalisation de l'exécution des rapports est activée. La valeur par défaut est **true**. Pour plus d’informations sur le journal des exécutions du serveur de rapports, consultez [Journal des exécutions du serveur de rapports et vue ExecutionLog3](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md).  

### <a name="enableintegratedsecurity"></a>EnableIntegratedSecurity
Détermine si la sécurité intégrée de Windows est prise en charge pour les connexions à la source de données de rapports. La valeur par défaut est **True**. Les valeurs valides sont les suivantes :

|Valeurs|Description|
|---------|---------|
|**True**|La sécurité intégrée de Windows est activée.|
|**False**|La sécurité intégrée de Windows n’est pas activée. Les sources de données de rapports qui sont configurées de manière à utiliser la sécurité intégrée de Windows ne seront pas exécutées.|

### <a name="enableloadreportdefinition"></a>EnableLoadReportDefinition
Sélectionnez cette option pour spécifier si les utilisateurs peuvent effectuer une exécution de rapport non planifiée à partir d’un rapport du Générateur de rapports. La définition de cette option spécifie la propriété **EnableLoadReportDefinition** sur le serveur de rapports.  

Si vous désactivez cette option, la propriété a la valeur False. Le serveur de rapports ne crée pas de rapports générés interactifs pour les rapports utilisant un modèle de rapport comme source de données. Tout appel à la méthode LoadReportDefinition est bloqué.  

La désactivation de cette option atténue la menace qu'un utilisateur malveillant lance une attaque par déni de service en surchargeant le serveur de rapports avec les demandes LoadReportDefinition.  

### <a name="enablemyreports"></a>EnableMyReports  
Indique si la fonctionnalité Mes rapports est activée. La valeur **true** indique que la fonctionnalité est activée.  

### <a name="enablepowerbireportexportdata"></a>EnablePowerBIReportExportData 
(Serveur de rapports Power BI uniquement) Activez l’exportation des données du serveur de rapports Power BI à partir des visuels Power BI. Les valeurs sont True, False.  La valeur par défaut est True. 

### <a name="enablepowerbireportexportunderlyingdata"></a>EnablePowerBIReportExportUnderlyingData 
(Power BI Report Server uniquement) Indique si un client peut exporter des données sous-jacentes à partir de visuels Power BI dans Power BI Report Server. La valeur true indique que la fonctionnalité est activée.

### <a name="enableremoteerrors"></a>EnableRemoteErrors
Inclut les informations externes sur l'erreur (par exemple, les informations d'erreur relatives aux sources de données de rapport) avec les messages d'erreur retournés pour les utilisateurs qui demandent des rapports à partir d'ordinateurs distants. Les valeurs valides sont **true** et **false**. La valeur par défaut est **false**. Pour plus d’informations, consultez [Activer les erreurs distantes &#40;Reporting Services&#41;](../../reporting-services/report-server/enable-remote-errors-reporting-services.md).  

### <a name="enabletestconnectiondetailederrors"></a>EnableTestConnectionDetailedErrors
Indique si les messages d’erreur détaillés sont envoyés à l’ordinateur client quand des utilisateurs testent des connexions de la source des données à l’aide du serveur de rapports. La valeur par défaut est **true**. Si l’option est définie sur **false**, seuls les messages d’erreur génériques sont envoyés.

###  <a name="executionlogdayskept"></a>ExecutionLogDaysKept  
Nombre de jours pendant lesquels conserver les informations sur l'exécution du rapport dans le journal des exécutions. Les valeurs valides pour cette propriété sont comprises entre **-1** et **2** **147** **483** **647**. Si la valeur est **-1**, les entrées ne sont pas supprimées de la table du journal des exécutions. La valeur par défaut est **60**.  

> [!NOTE]
> La définition d’une valeur égale à **0** *supprime* toutes les entrées du journal d’exécution. Une valeur **-1** conserve les entrées du journal d’exécution et ne les supprime pas.

### <a name="executionloglevel"></a>ExecutionLogLevel
Définissez le niveau du journal d’exécution. *La valeur par défaut est Normal.*

### <a name="externalimagestimeout"></a>ExternalImagesTimeout
Détermine la période pendant laquelle un fichier image externe doit être récupéré avant l'expiration du délai de connexion. La valeur par défaut est **600** secondes.  

### <a name="interprocesstimeoutminutes"></a>InterProcessTimeoutMinutes
(Serveur de rapports Power BI, Reporting Services 2019 et versions ultérieures uniquement) Définissez le délai d’expiration du processus en minutes. *La valeur par défaut est 30.*

### <a name="maxfilesizemb"></a>MaxFileSizeMb
Définissez la taille de fichier maximale du rapport en Mo. *La valeur par défaut est 1 000.  La valeur maximale est 2 000.*

### <a name="modelcleanupcycleminutes"></a>ModelCleanupCycleMinutes 
(Serveur de rapports Power BI uniquement) Définissez en minutes la fréquence de vérification des modèles inutilisés en mémoire. *La valeur par défaut est 15.*

### <a name="modelexpirationminutes"></a>ModelExpirationMinutes 
(Serveur de rapports Power BI uniquement) Définissez en minutes la fréquence d’éviction de la mémoire des modèles inutilisés. *La valeur par défaut est 60.*

###  <a name="myreportsrole"></a>MyReportsRole  
Nom du rôle utilisé lors de la création des stratégies de sécurité sur le dossier Mes rapports de l'utilisateur. La valeur par défaut est **Rôle de mes rapports**.  

### <a name="officeaccesstokenexpirationseconds"></a>OfficeAccessTokenExpirationSeconds 
(Serveur de rapports Power BI, Reporting Services 2019 et versions ultérieures uniquement) Définissez en secondes la durée au terme de laquelle vous souhaitez que le jeton d’accès Office expire. *La valeur par défaut est 60.*

### <a name="officeonlinediscoveryurl"></a>OfficeOnlineDiscoveryURL 
(Serveur de rapports Power BI uniquement) Définissez l’adresse de votre instance Office Online Server pour voir les classeurs Excel.

### <a name="rdlxreporttimetout"></a>RDLXReportTimetout
Valeur d’expiration, en secondes, du traitement du rapport RDLX *(rapports Power View dans un serveur SharePoint)* pour tous les rapports gérés dans l’espace de noms du serveur de rapports. Cette valeur peut être remplacée au niveau du rapport. Si cette propriété est définie, le serveur de rapports essaie d'arrêter le traitement d'un rapport lorsque le délai spécifié est expiré. Les valeurs valides sont comprises entre **-1** et **2** **147** **483** **647**. Si la valeur est égale à **-1**, les rapports de l’espace de noms ne spécifient pas de délai d’exécution pendant le traitement. La valeur par défaut est **1800**.

### <a name="requireintune"></a>RequireIntune
(Serveur de rapports Power BI, Reporting Services 2017 et versions ultérieures uniquement) Intune doit accéder aux rapports de votre organisation via l’application mobile Power BI. *La valeur par défaut est False.*

### <a name="restrictedresourcemimetypeforupload"></a>RestrictedResourceMimeTypeForUpload
(Serveur de rapports Power BI Janvier 2019, Reporting Services 2017 et versions ultérieures uniquement) Ensemble de types MIME avec lesquels les utilisateurs ne sont pas autorisés à charger du contenu. Toutes les ressources qui sont déjà stockées avec un type MIME restreint peuvent uniquement être téléchargées en tant que flux application/octet au lieu d’être ouvertes/exécutées par le navigateur.  Par défaut, il n’y a pas d’éléments restreints dans cette liste, mais nous recommandons aux organisations de renseigner cette liste pour offrir l’expérience la plus sécurisée.

### <a name="schedulerefreshtimeoutminutes"></a>ScheduleRefreshTimeoutMinutes 
(Serveur de rapports Power BI uniquement) Délai d’expiration, en minutes, de l’actualisation des données pour l’actualisation planifiée des rapports Power BI avec des modèles AS incorporés. La valeur par défaut est 120 minutes.

### <a name="sessiontimeout"></a>SessionTimeout
Durée (en secondes) pendant laquelle une session demeure active. La valeur par défaut est **600**.  

### <a name="sharepointintegratedmode"></a>SharePointIntegratedMode
Cette propriété en lecture seule indique le mode du serveur. Si cette valeur est False, le serveur de rapports s'exécute en mode natif.  

### <a name="showdownloadmenu"></a>ShowDownloadMenu
(Serveur de rapports Power BI, Reporting Services 2017 et versions ultérieures uniquement) Active le menu de téléchargement des outils clients. *La valeur par défaut est true.*

### <a name="sitename"></a>SiteName
Nom du site du serveur de rapports affiché dans le titre de la page du portail web. La valeur par défaut est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Cette propriété peut être une chaîne vide. La longueur maximale autorisée s’élève à 8 000 caractères.  

### <a name="snapshotcompression"></a>SnapshotCompression
Définit le mode de compression des instantanés. La valeur par défaut est **SQL**. Les valeurs valides sont les suivantes :

|Valeurs|Description|
|---------|---------|
|**SQL**|Les instantanés sont compressés quand ils sont stockés dans la base de données du serveur de rapports. Cette compression est le comportement actuel.|
|**Aucun**|Les instantanés ne sont pas compressés.|
|**Tout**|Les instantanés sont compressés pour toutes les options de stockage, qui incluent la base de données du serveur de rapports ou le système de fichiers.|

### <a name="storedparameterslifetime"></a>StoredParametersLifetime
Nombre maximal de jours pendant lesquels un paramètre stocké peut être stocké. Les valeurs valides sont comprises entre **-1**, **+1** et **2147483647**. La valeur par défaut est **180** jours.  

### <a name="storedparametersthreshold"></a>StoredParametersThreshold
Nombre maximal de valeurs de paramètres qui peuvent être stockées par le serveur de rapports. Les valeurs valides sont comprises entre **-1**, **+1** et **2147483647**. La valeur par défaut est de **1500**.  

### <a name="supportedhyperlinkschemes"></a>SupportedHyperlinkSchemes 
(Serveur de rapports Power BI Janvier 2019, Reporting Services 2019 et versions ultérieures uniquement) Définit une liste de schémas d’URI séparés par des virgules et pouvant être définis sur des actions de lien hypertexte dont la restitution est autorisée ou « &ast; » pour activer toutes les schémas de lien hypertexte. Par exemple, le paramètre « http, https » autoriserait les liens hypertexte vers « https://www. contoso.com », mais supprimerait les liens hypertextes vers « mailto:bill@contoso.com » ou « javascript:window.open(‘ www.contoso.com’, ‘_blank’) ». La valeur par défaut est « &ast; ».

### <a name="systemreporttimeout"></a>SystemReportTimeout
Valeur (en secondes) du délai d'exécution du traitement du rapport par défaut pour tous les rapports gérés dans l'espace de noms du serveur de rapports. Cette valeur peut être remplacée au niveau du rapport. Si cette propriété est définie, le serveur de rapports essaie d'arrêter le traitement d'un rapport lorsque le délai spécifié est expiré. Les valeurs valides sont comprises entre **-1** et **2** **147** **483** **647**. Si la valeur est égale à **-1**, les rapports de l’espace de noms ne spécifient pas de délai d’exécution pendant le traitement. La valeur par défaut est **1800**.  

### <a name="systemsnapshotlimit"></a>SystemSnapshotLimit
Nombre maximal d'instantanés stockées pour un rapport. Les valeurs valides sont comprises entre **-1** et **2** **147** **483** **647**. Si la valeur est égale à **-1**, il n’existe aucune limite sur le nombre d’instantanés.  

### <a name="timerinitialdelayseconds"></a>TimerInitialDelaySeconds
(Serveur de rapports Power BI, Reporting Services 2017 et versions ultérieures uniquement) Définissez en secondes la durée pendant laquelle vous souhaitez que l’heure initiale soit retardée. *La valeur par défaut est 60.*

### <a name="trustedfileformat"></a>TrustedFileFormat
(Serveur de rapports Power BI, Reporting Services 2017 et versions ultérieures uniquement) Définissez tous les formats de fichiers externes qui s’ouvrent dans le navigateur sur le site du portail Reporting Services. Les formats de fichiers externes non répertoriés invitent l’utilisateur à télécharger l’option dans le navigateur. Les valeurs par défaut sont jpg, jpeg, jpe, wav, bmp, pdf, img, gif, json, mp4, web, png.

### <a name="usesessioncookies"></a>UseSessionCookies
Indique si le serveur de rapports doit utiliser les cookies de session lors la communication avec les navigateurs clients. La valeur par défaut est **true**.  

## <a name="see-also"></a>Voir aussi

[Définir les propriétés du serveur de rapports &#40;Management Studio&#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
[Se connecter à un serveur de rapports dans Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
[Propriétés de Reporting Services](../../reporting-services/report-server-web-service/net-framework/reporting-services-properties.md)   
[Aide du serveur de rapports dans Management Studio accessible par la touche F1](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
[Propriétés système de Report Server](../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)   
[Écrire des scripts pour les tâches d'administration et de déploiement](../../reporting-services/tools/script-deployment-and-administrative-tasks.md)   
[Activer et désactiver Mes rapports](../../reporting-services/report-server/enable-and-disable-my-reports.md)  

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)
