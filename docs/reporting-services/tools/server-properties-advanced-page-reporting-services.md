---
title: Propriétés du serveur (page Avancé) - Reporting Services | Microsoft Docs
author: maggiesMSFT
ms.author: maggies
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
ms.date: 01/15/2019
ms.openlocfilehash: 079565c813e0b66f09881039ea3d6509bdf6cf54
ms.sourcegitcommit: 75fe364317a518fcf31381ce6b7bb72ff6b2b93f
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908263"
---
# <a name="server-properties-advanced-page---reporting-services"></a>Propriétés du serveur (page Avancé) - Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)])

Utilisez cette page pour définir des propriétés système sur le serveur de rapports. Il existe plusieurs façons de définir des propriétés système. Cet outil fournit une interface utilisateur graphique afin que vous puissiez définir des propriétés sans devoir écrire du code.

Pour ouvrir cette page, démarrez SQL Server Management Studio, connectez-vous à une instance de serveur de rapports, cliquez avec le bouton droit sur le nom du serveur de rapports, puis sélectionnez **Propriétés**. Sélectionnez **Avancé** pour ouvrir cette page.

## <a name="options"></a>Options

**EnableMyReports**  
Indique si la fonctionnalité Mes rapports est activée. La valeur **true** indique que la fonctionnalité est activée.  

**MyReportsRole**  
Nom du rôle utilisé lors de la création des stratégies de sécurité sur le dossier Mes rapports de l'utilisateur. La valeur par défaut est **Rôle de mes rapports**.  

**EnableClientPrinting**  
Détermine si le contrôle ActiveX RSClientPrint peut être téléchargé à partir du serveur de rapports. Les valeurs valides sont **true** et **false**. La valeur par défaut est **true**. Pour plus d’informations sur les paramètres supplémentaires nécessaires pour ce contrôle, consultez [Activer et désactiver l’impression côté client pour Reporting Services](../../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  

**EnableExecutionLogging**  
Indique si la journalisation de l'exécution des rapports est activée. La valeur par défaut est **true**. Pour plus d’informations sur le journal des exécutions du serveur de rapports, consultez [Journal des exécutions du serveur de rapports et vue ExecutionLog3](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md).  

**ExecutionLogDaysKept**  
Nombre de jours pendant lesquels conserver les informations sur l'exécution du rapport dans le journal des exécutions. Les valeurs valides pour cette propriété sont comprises entre **-1** et **2** **147** **483** **647**. Si la valeur est **-1**, les entrées ne sont pas supprimées de la table du journal des exécutions. La valeur par défaut est **60**.  

> [!NOTE]
> La définition d’une valeur égale à **0** *supprime* toutes les entrées du journal d’exécution. Une valeur **-1** conserve les entrées du journal d’exécution et ne les supprime pas.

Valeur d’expiration du traitement du rapport RDLX **RDLXReportTimetout** *(rapports Power View dans un serveur SharePoint)* , en secondes, pour tous les rapports gérés dans l’espace de noms du serveur de rapports. Cette valeur peut être remplacée au niveau du rapport. Si cette propriété est définie, le serveur de rapports essaie d'arrêter le traitement d'un rapport lorsque le délai spécifié est expiré. Les valeurs valides sont comprises entre **-1** et **2** **147** **483** **647**. Si la valeur est égale à **-1**, les rapports de l’espace de noms ne spécifient pas de délai d’exécution pendant le traitement. La valeur par défaut est **1800**.

**SessionTimeout** Durée (en secondes) pendant laquelle une session demeure active. La valeur par défaut est **600**.  

**SharePointIntegratedMode**  
Cette propriété en lecture seule indique le mode du serveur. Si cette valeur est False, le serveur de rapports s'exécute en mode natif.  

**SiteName**  
Nom du site du serveur de rapports affiché dans le titre de la page du portail web. La valeur par défaut est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Cette propriété peut être une chaîne vide. La longueur maximale autorisée s’élève à 8 000 caractères.  

**StoredParametersLifetime** Nombre maximal de jours pendant lesquels un paramètre stocké peut être stocké. Les valeurs valides sont comprises entre **-1**, **+1** et **2147483647**. La valeur par défaut est **180** jours.  

**StoredParametersThreshold**  
Nombre maximal de valeurs de paramètres qui peuvent être stockées par le serveur de rapports. Les valeurs valides sont comprises entre **-1**, **+1** et **2147483647**. La valeur par défaut est de **1500**.  

**UseSessionCookies**  
Indique si le serveur de rapports doit utiliser les cookies de session lors la communication avec les navigateurs clients. La valeur par défaut est **true**.  

**ExternalImagesTimeout**  
Détermine la période pendant laquelle un fichier image externe doit être récupéré avant l'expiration du délai de connexion. La valeur par défaut est **600** secondes.  

**SnapshotCompression** Instantané du serveur de rapports à ce moment-là.

**SnapshotCompression**  
Définit le mode de compression des instantanés. La valeur par défaut est **SQL**. Les valeurs valides sont les suivantes :

|Valeurs|Description|
|---------|---------|
|**SQL**|Les instantanés sont compressés quand ils sont stockés dans la base de données du serveur de rapports. Cette compression est le comportement actuel.|
|**Aucun**|Les instantanés ne sont pas compressés.|
|**Tous**|Les instantanés sont compressés pour toutes les options de stockage, qui incluent la base de données du serveur de rapports ou le système de fichiers.|

**SystemReportTimeout**  
Valeur (en secondes) du délai d'exécution du traitement du rapport par défaut pour tous les rapports gérés dans l'espace de noms du serveur de rapports. Cette valeur peut être remplacée au niveau du rapport. Si cette propriété est définie, le serveur de rapports essaie d'arrêter le traitement d'un rapport lorsque le délai spécifié est expiré. Les valeurs valides sont comprises entre **-1** et **2** **147** **483** **647**. Si la valeur est égale à **-1**, les rapports de l’espace de noms ne spécifient pas de délai d’exécution pendant le traitement. La valeur par défaut est **1800**.  

**SystemSnapshotLimit**  
Nombre maximal d'instantanés stockées pour un rapport. Les valeurs valides sont comprises entre **-1** et **2** **147** **483** **647**. Si la valeur est égale à **-1**, il n’existe aucune limite sur le nombre d’instantanés.  

**AccessControlAllowCredentials**  
Indique si la réponse à la requête du client peut être exposée quand l’indicateur 'credentials' a la valeur true. La valeur par défaut est **false**.

**AccessControlAllowHeaders** Liste séparée par des virgules des en-têtes autorisés par le serveur quand un client soumet une requête. Cette propriété peut être une chaîne vide. Spécifiez * pour autoriser tous les en-têtes.

**AccessControlAllowMethods** Liste séparée par des virgules des méthodes HTTP autorisées par le serveur quand un client soumet une requête. Les valeurs par défaut sont GET, PUT, POST, PATCH, DELETE. Spécifiez * pour autoriser toutes les méthodes.

**AccessControlAllowMethods** Liste séparée par des virgules des méthodes HTTP autorisées par le serveur quand un client soumet une requête. La valeur par défaut est vide, ce qui empêche toutes les requêtes. Spécifiez * pour autoriser toutes les origines quand les informations d’identification ne sont pas définies. Si les informations d’identification sont spécifiées, une liste explicite d’origines doit être indiquée.

**AccessControlExposeHeaders** Liste séparée par des virgules des en-têtes que le serveur expose aux clients. La valeur par défaut est vide.

**AccessControlMaxAge** Spécifie le nombre de secondes pendant lesquelles les résultats de la requête préliminaire peuvent être mis en cache. La valeur par défaut est 600 (10 minutes).

**AllowedResourceExtensionsForUpload (Power BI Report Server et Reporting Services 2017 et versions ultérieures uniquement)** Ensemble d’extensions de ressources qui peuvent être chargées sur le serveur de rapports. Les extensions pour les types de fichiers intégrés comme &ast;.rdl et &ast;.pbix ne doivent pas obligatoirement être incluses. La valeur par défaut est « &ast;, &ast;.xml, &ast;.xsd, &ast;.xsl, &ast;.png, &ast;.gif, &ast;.jpg, &ast;.tif, &ast;.jpeg, &ast;.tiff, &ast;.bmp, &ast;.pdf, &ast;.svg, &ast;.rtf, &ast;.txt, &ast;.doc, &ast;.docx, &ast;.pps, &ast;.ppt, &ast;.pptx ».

**RestrictedResourceMimeTypeForUpload** Ensemble de types MIME que les utilisateurs ne sont pas autorisés à télécharger du contenu avec. Toutes les ressources qui sont déjà stockées avec un type MIME restreint peuvent uniquement être téléchargées en tant qu’application/octet-stream au lieu d’être ouvertes/exécutées par le navigateur.  Par défaut, il n’y a pas d’éléments restreints dans cette liste, mais nous recommandons aux organisations de les alimenter pour offrir l’expérience la plus sécurisée.

**EditSessionCacheLimit**  
Spécifie le nombre des entrées de cache de données qui peuvent être actives dans une session d'édition de rapport. La valeur par défaut est 5.  

**EditSessionTimeout**  
Spécifie le nombre de secondes jusqu'à l'expiration d'une session d'édition de rapport. La valeur par défaut est 7 200 secondes (deux heures).  

**EnableIntegratedSecurity**  
Détermine si la sécurité intégrée de Windows est prise en charge pour les connexions à la source de données de rapports. La valeur par défaut est **True**. Les valeurs valides sont les suivantes :

|Valeurs|Description|
|---------|---------|
|**True**|La sécurité intégrée de Windows est activée.|
|**False**|La sécurité intégrée de Windows n’est pas activée. Les sources de données de rapports qui sont configurées de manière à utiliser la sécurité intégrée de Windows ne seront pas exécutées.|

**EnableLoadReportDefinition**  
Sélectionnez cette option pour spécifier si les utilisateurs peuvent effectuer une exécution de rapport non planifiée à partir d’un rapport du Générateur de rapports. La définition de cette option spécifie la propriété **EnableLoadReportDefinition** sur le serveur de rapports.  

Si vous désactivez cette option, la propriété a la valeur False. Le serveur de rapports ne crée pas de rapports générés interactifs pour les rapports utilisant un modèle de rapport comme source de données. Tout appel à la méthode LoadReportDefinition est bloqué.  

La désactivation de cette option atténue la menace qu'un utilisateur malveillant lance une attaque par déni de service en surchargeant le serveur de rapports avec les demandes LoadReportDefinition.  

**EnableRemoteErrors**  
Inclut les informations externes sur l'erreur (par exemple, les informations d'erreur relatives aux sources de données de rapport) avec les messages d'erreur retournés pour les utilisateurs qui demandent des rapports à partir d'ordinateurs distants. Les valeurs valides sont **true** et **false**. La valeur par défaut est **false**. Pour plus d’informations, consultez [Activer les erreurs distantes &#40;Reporting Services&#41;](../../reporting-services/report-server/enable-remote-errors-reporting-services.md).  

**EnableCustomVisuals** ***(Power BI Report Server uniquement)*** Activez l’affichage des visuels personnalisés Power BI. Les valeurs sont True/False. *La valeur par défaut est True.*  

**ExecutionLogLevel** Définissez le niveau du journal d’exécution. *La valeur par défaut est Normal.*

**InterProcessTimeoutMinutes** Définissez le délai d’expiration du processus en minutes. *La valeur par défaut est 30.*

**MaxFileSizeMb** Définissez la taille de fichier maximale du rapport en Mo. *La valeur par défaut est 1 000.  La valeur maximale est 2 000.*

**ModelCleanupCycleminutes** Définissez le cycle de nettoyage du modèle en minutes. *La valeur par défaut est 15.*

**OfficeAccessTokenExpirationSeconds** ***(Power BI Report Server uniquement)*** Définissez la durée au terme de laquelle vous souhaitez que le jeton d’accès Office expire, en secondes. *La valeur par défaut est 60.*

**OfficeOnlineDiscoveryURL** ***(Power BI Report Server uniquement)*** Définissez l’adresse de votre instance Office Online Server pour voir les classeurs Excel.

**RequireIntune** Demande à Intune d’accéder aux rapports de votre organisation via l’application mobile Power BI. *La valeur par défaut est False.*

**ScheduleRefreshTimeoutMinutes** ***(Power BI Report Server uniquement)*** Définissez la durée au terme de laquelle vous souhaitez que l’actualisation planifiée expire. *La valeur par défaut est 120.*

**ShowDownloadMenu** Active le menu de téléchargement des outils du client. *La valeur par défaut est true.*

**SupportedHyperlinkSchemes** ***(Power BI Report Server uniquement)*** Définit une liste de schémas d’URI séparés par des virgules et pouvant être définis sur des actions de lien hypertexte dont la restitution est autorisée ou « &ast; » pour activer toutes les schémas de lien hypertexte. Par exemple, le paramètre « http, https » autoriserait les liens hypertexte vers « https://www. contoso.com », mais supprimerait les liens hypertextes vers « mailto:bill@contoso.com » ou « javascript:window.open(‘www.contoso.com’, ‘_blank’) ». La valeur par défaut est « &ast; ».

**TimeInitialDelaySeconds** Définissez la durée pendant laquelle vous souhaitez que l’heure initiale soit différée, en secondes. *La valeur par défaut est 60.*

**TrustedFileFormat** Définissez tous les formats de fichiers externes qui s’ouvrent dans le navigateur sur le site du portail Reporting Services. Les formats de fichiers externes non répertoriés invitent l’utilisateur à télécharger l’option dans le navigateur. Les valeurs par défaut sont jpg, jpeg, jpe, wav, bmp, pdf, img, gif, json, mp4, web, png.

**EnablePowerBIReportExportData** ***(Power BI Report Server uniquement)***  
Activez l’exportation des données Power BI Report Server à partir des visuels Power BI. Les valeurs sont True, False.  La valeur par défaut est True.  

**ScheduleRefreshTimeoutMinutes** ***(Power BI Report Server uniquement)***  
Délai d’expiration de l’actualisation des données, en minutes, pour l’actualisation planifiée des rapports Power BI avec des modèles AS incorporés. La valeur par défaut est 120 minutes.

**EnableTestConnectionDetailedErrors**  
Indique si les messages d’erreur détaillés sont envoyés à l’ordinateur client quand des utilisateurs testent des connexions de la source des données à l’aide du serveur de rapports. La valeur par défaut est **true**. Si l’option est définie sur **false**, seuls les messages d’erreur génériques sont envoyés.

## <a name="see-also"></a>Voir aussi

[Définir les propriétés du serveur de rapports &#40;Management Studio&#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
[Se connecter à un serveur de rapports dans Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
[Propriétés de Reporting Services](../../reporting-services/report-server-web-service/net-framework/reporting-services-properties.md)   
[Aide du serveur de rapports dans Management Studio accessible par la touche F1](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
[Propriétés système de Report Server](../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)   
[Écrire des scripts pour les tâches d'administration et de déploiement](../../reporting-services/tools/script-deployment-and-administrative-tasks.md)   
[Activer et désactiver Mes rapports](../../reporting-services/report-server/enable-and-disable-my-reports.md)  

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)
