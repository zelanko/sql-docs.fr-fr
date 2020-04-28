---
title: 'Liste de vérification : utiliser PowerShell pour vérifier PowerPivot pour SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 73a13f05-3450-411f-95f9-4b6167cc7607
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0dea40f9c4e4c0672db78ca7e841cb7cedca857e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "78174348"
---
# <a name="checklist-use-powershell-to-verify-powerpivot-for-sharepoint"></a>Liste de vérification : utiliser PowerShell pour vérifier PowerPivot pour SharePoint
  Aucune opération d'installation ou de récupération de [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] n'est terminée sans exécuter un test de vérification complet qui confirme que les services et les données sont opérationnels. Dans cet article, nous vous indiquons comment effectuer ces étapes avec Windows PowerShell. Nous avons consacré une section distincte à chaque étape afin que vous puissiez accéder directement aux tâches spécifiques. Par exemple, exécutez le script dans la section [Bases de données](#bkmk_databases) de cette rubrique pour vérifier le nom de l'application de service et des bases de données de contenu si vous souhaitez les planifier pour la maintenance ou la sauvegarde.

|||
|-|-|
|![Contenu relatif à PowerShell](../../../reporting-services/media/rs-powershellicon.jpg "Contenu relatif à PowerShell")|Un script PowerShell complet est inclus en bas de la rubrique. Utilisez le script dans sa totalité comme point de départ pour générer un script personnalisé afin de vérifier votre déploiement complet de [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] .|

||
|-|
|**[!INCLUDE[applies](../../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|

 **Dans cette rubrique**- Les lettres dans la table des matières qui suit correspondent aux zones du schéma. Le schéma illustre les points suivants :

|||
|-|-|
|[Préparer votre environnement PowerShell](#bkmk_prerequisites)<br /><br /> [Symptômes et actions recommandées](#bkmk_symptoms)<br /><br /> **(A)** [Service Windows Analysis Services](#bkmk_windows_service)<br /><br /> **(B)** [PowerPivotSystemService et PowerPivotEngineService](#bkmk_engine_and_system_service)<br /><br /> **(C)** [Application(s) et proxys du service PowerPivot](#bkmk_powerpivot_service_application)<br /><br /> **(D)** [Bases de données](#bkmk_databases)<br /><br /> [Fonctionnalités SharePoint](#bkmk_features)<br /><br /> [Travaux du minuteur](#bkmk_timer_jobs)<br /><br /> [Règles d'intégrité](#bkmk_health_rules)<br /><br /> **(E)** [Journaux Windows et ULS](#bkmk_logs)<br /><br /> [Fournisseur MSOLAP](#bkmk_msolap)<br /><br /> [Bibliothèque cliente ADOMD.NET](#bkmk_adomd)<br /><br /> [Règles de collecte de données d'intégrité](#bkmk_health_collection)<br /><br /> [Solutions](#bkmk_solutions)<br /><br /> [Étapes de vérification manuelle](#bkmk_manual)<br /><br /> [Plus de ressources](#bkmk_more_resources)<br /><br /> [Script PowerShell complet](#bkmk_full_script)|![contrôle powershell pour powerpivot](../../../sql-server/install/media/ssas-powershell-component-verification.png "contrôle powershell pour powerpivot")|

##  <a name="prepare-your-powershell-environment"></a><a name="bkmk_prerequisites"></a> Préparation de votre environnement PowerShell
 Les étapes de cette section préparent votre environnement PowerShell. Elles peuvent ne pas être requises, selon la façon dont votre environnement de script est actuellement configuré.

 **Autorisations PowerShell**

 Ouvrez une fenêtre Powershell ou PowerShell ISE (environnement d’écriture de scripts intégré) avec des **privilèges d’administrateur**. Sans privilèges d'administrateur, lorsque vous exécuterez les commandes, vous recevrez un message d'erreur similaire au suivant :

 Get-SPLogEvent : Vous devez disposer des **droits d’administrateur** de l’ordinateur pour exécuter cette applet de commande.

 Module **SharePoint et [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]**

 Si un message d'erreur semblable au suivant s'affiche lorsque vous exécutez des applets de commande associées à SharePoint, exécutez la commande Add-PSSnapin :

 Le terme « Get-PowerPivotSystemService » **n’est pas reconnu comme nom d’applet de commande**, fonction, fichier de script ou programme exécutable. Vérifiez l’orthographe du nom ou, si un chemin d’accès a été inclus, vérifiez que le chemin d’accès est correct et réessayez.

```
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0
```

 **Windows PowerShell**

 Pour plus d'informations sur PowerShell ISE, consultez [Introduction à Windows PowerShell ISE](https://technet.microsoft.com/library/dd315244.aspx) et [Utiliser Windows PowerShell pour administrer SharePoint 2013](https://technet.microsoft.com/library/ee806878\(v=office.15\).aspx).

|||
|-|-|
|![powerpivot dans l'ensemble général d'applications sharepoint](../../../sql-server/install/media/ssas-powerpivot-logo.png "powerpivot dans l'ensemble général d'applications sharepoint")|Vous pouvez éventuellement vérifier la plupart des composants dans l'Administration centrale, dans le tableau de bord de gestion de [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] . Pour ouvrir le tableau de bord dans l'Administration centrale, cliquez sur **Paramètres généraux de l'application**, puis cliquez sur **Tableau de bord de gestion** dans **PowerPivot**. Pour plus d'informations sur le tableau de bord, consultez [PowerPivot Management Dashboard and Usage Data](../../power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md).|

##  <a name="symptoms-and-recommended-actions"></a><a name="bkmk_symptoms"></a>Symptômes et actions recommandées
 Le tableau suivant répertorie les symptômes ou les problèmes et suggère la section correspondante de cette rubrique à consulter pour vous aider à résoudre le problème.

|Symptôme|Voir la section|
|-------------|-----------------|
|L'actualisation des données ne fonctionne pas|Consultez la section [Timer Jobs](#bkmk_timer_jobs) et vérifiez que le **Travail du minuteur d'actualisation des données PowerPivot** est en ligne.|
|Les données du tableau de bord de gestion sont obsolètes|Consultez la section [Travaux du minuteur](#bkmk_timer_jobs) et vérifiez que le **Travail du minuteur pour le traitement du tableau de bord de gestion** est en ligne.|
|Certaines parties du tableau de bord de gestion ne sont pas accessibles|Si vous installez PowerPivot pour SharePoint dans une batterie de serveurs qui présente la topologie d'Administration centrale, sans Excel Services ou PowerPivot pour SharePoint, vous devez télécharger et installer la bibliothèque cliente Microsoft ADOMD.NET si vous voulez disposer d'un accès total aux rapports intégrés dans le tableau de bord de gestion PowerPivot. Certains rapports du tableau de bord utilisent ADOMD.NET pour accéder aux données internes qui fournissent les données de création de rapports sur le traitement des requêtes PowerPivot et l'intégrité des serveurs de la batterie. Consultez la section [Bibliothèque cliente ADOMD.NET](#bkmk_adomd) et la rubrique [Installer ADOMD.NET sur des serveurs web frontaux exécutant l’Administration centrale](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md).|
|\<> de contenu future||

##  <a name="analysis-services-windows-service"></a><a name="bkmk_windows_service"></a> Service Windows Analysis Services
 Le script de cette section vérifie l'instance d' [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] en mode SharePoint. Vérifiez que le service est **en cours d’exécution**.

```powershell
Get-Service | Select name, displayname, status | Where {$_.Name -eq "msolap`$powerpivot"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name              DisplayName                                Status
----              -----------                                ------
MSOLAP$POWERPIVOT SQL Server Analysis Services (POWERPIVOT) Running
```

##  <a name="powerpivotsystemservice-and-powerpivotengineservice"></a><a name="bkmk_engine_and_system_service"></a>PowerPivotSystemService et PowerPivotEngineService
 Les scripts de cette section vérifient les services système de [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] . Il existe un seul service système pour un déploiement SharePoint 2013 et deux services pour un déploiement SharePoint 2010.

 **PowerPivotSystemService**

 Vérifiez que l’État est **en ligne**.

```powershell
Get-PowerPivotSystemService | Select typename, status, applications, farm | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName                                  Status Applications                             Farm
--------                                  ------ ------------                             ----
SQL Server PowerPivot Service Application Online {Default PowerPivot Service Application} SPFarm Name=SharePoint_Config_77d8ab0744a34e8aa27c806a2b8c760c
```

 **PowerPivotEngineService**

> [!NOTE]
>  **Ignorez ce script si** vous utilisez SharePoint 2013. Le service PowerPivotEngineService ne fait pas partie d'un déploiement SharePoint 2013. Si vous exécutez l'applet de commande Get-PowerPivot**Engine**Service sur SharePoint 2013, vous verrez s'afficher un message d'erreur semblable au suivant. Ce message d'erreur est retourné même si vous avez exécuté la commande Add-PSSnapin décrite dans la section des conditions préalables requises de cette rubrique.
> 
>  Le terme « Get-PowerPivotEngineService » n'est pas reconnu comme nom d'une applet de commande

 Dans un déploiement SharePoint 2010, vérifiez que l'état est **En ligne**.

```powershell
Get-PowerPivotEngineService | Select typename, status, name, instances, farm | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName  : SQL Server Analysis Services
Status    : Online
Name      : MSOLAP$POWERPIVOT
Instances : {POWERPIVOT}
Farm      : SPFarm Name=SharePoint_Config
```

##  <a name="powerpivot-service-applications-and-proxies"></a><a name="bkmk_powerpivot_service_application"></a>Application (s) et proxys du service PowerPivot
 Vérifiez que l'état est **En ligne**. L'application Excel Services n'utilise pas une base de données d'application de service et par conséquent l'applet de commande ne retourne aucun nom de base de données. Notez la base de données utilisée par l'application de service de [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] , afin de pouvoir vérifier que la base de données est en ligne dans la section traitant des bases de données plus loin dans cette rubrique.

 **Application(s) PowerPivot et Excel Service**

 Pour un déploiement SharePoint 2010, vérifiez que l'état est **En ligne**.

```powershell
Get-PowerPivotServiceApplication | Select typename,name, status, unattendedaccount, applicationpool, farm, database
Get-SPExcelServiceApplication | Select typename, DisplayName, status
```

```Output
TypeName          : PowerPivot Service Application
Name              : PowerPivotServiceApplication1
Status            : Online
UnattendedAccount : PowerPivotUnattendedAccount
ApplicationPool   : SPIisWebServiceApplicationPool Name=sqlbi_serviceapp
Farm              : SPFarm Name=SharePoint_Config
Database          : GeminiServiceDatabase Name=PowerPivotServiceApplication1_19648f3f2c944e27acdc6c20aab8487a

TypeName    : Excel Services Application Web Service Application
DisplayName : Excel Services Application
Status      : Online
```

 **Pool d’applications de service**

> [!NOTE]
>  L'exemple de code suivant retourne tout d'abord la propriété applicationpool de l'application de service [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] par défaut. Le nom est analysé à partir de la chaîne et est utilisé pour obtenir l'état de l'objet de pool d'applications.
> 
>  Vérifiez que l’État est **en ligne**. Si l’État n’est pas en ligne ou si vous voyez « erreur http » lorsque [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] vous parcourez le site, vérifiez que les informations d’identification de l’identité dans les pools d’applications IIS sont toujours correctes. Le nom du pool d'applications IIS est la valeur de la propriété d'ID retournée par la commande Get-SPServiceApplicationPool.

```powershell
$poolname = [string](Get-PowerPivotServiceApplication | Select -Property applicationpool)
$position = $poolname.lastindexof("=")
$poolname = $poolname.substring($position+1)
$poolname = $poolname.substring(0,$poolname.length-1)

Get-SPServiceApplicationPool | Select name, status, processaccountname, id | Where {$_.Name -eq $poolname} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                           Status ProcessAccountName Id
----                           ------ ------------------ ------- 
SharePoint Web Services System Online DOMAIN\account     89b50ec3-49e3-4de7-881a-2cec4b8b73ea
```

 ![Remarque](../../../reporting-services/media/rs-fyinote.png "remarque") Le pool d’applications peut également être vérifié sur la page Administration centrale **gérer les applications de service**. Cliquez sur le nom de l'application de service et cliquez sur **Propriétés** dans le ruban.

 **Proxys d'application PowerPivot et Excel Service**

 Vérifiez que l’État est **en ligne**.

```powershell
Get-SPServiceApplicationProxy | Select typename, status, unattendedaccount, displayname | Where {$_.TypeName -Like "*powerpivot*" -Or $_.TypeName -Like "*excel services*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName                                                 Status UnattendedAccount           DisplayName
--------                                                 ------ -----------------           -----------
PowerPivot Service Application Proxy                     Online PowerPivotUnattendedAccount PowerPivotServiceApplication1
Excel Services Application Web Service Application Proxy Online                             Excel Services Application
```

##  <a name="databases"></a><a name="bkmk_databases"></a> Bases de données
 Le script suivant retourne l'état des bases de données d'application de service et de toutes les bases de données de contenu. Vérifiez que l'état est **En ligne**.

```powershell
Get-SPDatabase | Select name, status, server, typename | Where {$_.TypeName -eq "content database" -Or $_.TypeName -Like "*Gemini*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                                                                       Status Server                  TypeName 
----                                                                       ------ ------                  -------- 
DefaultPowerPivotServiceApplicationDB-38422181-2b68-4ab2-b2bb-9c00c39e5a5e Online SPServer Name=TESTSERVER Microsoft.AnalysisServices.SPAddin.GeminiServiceDatabase
DefaultWebApplicationDB-f0db1a8e-4c22-408c-b9b9-153bd74b0312               Online TESTSERVER\POWERPIVOT    Content Database 
SharePoint_Admin_3cadf0b098bf49e0bb15abd487f5c684                          Online TESTSERVER\POWERPIVOT    Content Database
```

##  <a name="sharepoint-features"></a><a name="bkmk_features"></a>Fonctionnalités SharePoint
 Vérifiez que le site Web et les fonctionnalités de la batterie sont en ligne.

```powershell
Get-SPFeature | Select displayname, status, scope, farm | Where {$_.displayName -Like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
DisplayName     Status Scope Farm                         
-----------     ------ ----- ----                         
PowerPivotSite  Online  Site SPFarm Name=SharePoint_Config
PowerPivotAdmin Online   Web SPFarm Name=SharePoint_Config
PowerPivot      Online  Farm SPFarm Name=SharePoint_Config
```

##  <a name="timer-jobs"></a><a name="bkmk_timer_jobs"></a>Travaux du minuteur
 Vérifiez que les travaux du minuteur sont **En ligne**. Le [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] EngineService n'est pas installé sur SharePoint 2013, par conséquent le script ne répertorie pas les travaux du minuteur EngineService dans un déploiement SharePoint 2013.

```powershell
Get-SPTimerJob | Where {$_.service -Like "*power*" -Or $_.service -Like "*mid*"} | Select status, displayname, LastRunTime, service | Format-Table -Property * -AutoSize | Out-Default
```

```Output
      Status DisplayName                                                                          LastRunTime          Service                             
------ -----------                                                                          -----------          -------                             
Online Health Analysis Job (Daily, SQL Server Analysis Services, All Servers)               4/9/2014 12:00:01 AM EngineService Name=MSOLAP$POWERPIVOT
Online Health Analysis Job (Hourly, SQL Server Analysis Services, All Servers)              4/9/2014 1:00:01 PM  EngineService Name=MSOLAP$POWERPIVOT
Online Health Analysis Job (Weekly, SQL Server Analysis Services, All Servers)              4/6/2014 12:00:10 AM EngineService Name=MSOLAP$POWERPIVOT
Online PowerPivot Management Dashboard Processing Timer Job                                 4/8/2014 3:45:38 AM  MidTierService
Online PowerPivot Health Statistics Collector Timer Job                                     4/9/2014 1:00:12 PM  MidTierService
Online PowerPivot Data Refresh Timer Job                                                    4/9/2014 1:09:36 PM  MidTierService
Online Health Analysis Job (Daily, SQL Server PowerPivot Service Application, All Servers)  4/9/2014 12:00:00 AM MidTierService
Online Health Analysis Job (Daily, SQL Server PowerPivot Service Application, Any Server)   4/9/2014 12:00:00 AM MidTierService
Online Health Analysis Job (Weekly, SQL Server PowerPivot Service Application, All Servers) 4/6/2014 12:00:03 AM MidTierService
Online Health Analysis Job (Weekly, SQL Server PowerPivot Service Application, Any Server)  4/6/2014 12:00:03 AM MidTierService
Online PowerPivot Setup Extension Timer Job                                                 4/1/2014 1:40:31 AM  MidTierService
```

##  <a name="health-rules"></a><a name="bkmk_health_rules"></a>Règles d’intégrité
 Il y a moins de règles dans un déploiement SharePoint 2013. Pour obtenir une liste complète des règles pour chaque environnement SharePoint et une explication de l’utilisation des règles, consultez la page relative aux [règles d’intégrité PowerPivot-configurer](../../power-pivot-sharepoint/configure-power-pivot-health-rules.md).

```powershell
Get-SPHealthAnalysisRule | Select name, enabled, summary | Where {$_.summary -Like "*power*"}  | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                          Enabled Summary
----                          ------- -------         
SecondaryLogonHealthRule         True PowerPivot:  Secondary Logon service (seclogon) is disabled
DataRefreshTimerJobHealthRule    True PowerPivot: The PowerPivot Data Refresh timer job is disabled.
ASUsageLoadHealthRule            True PowerPivot: The ratio of load events to connections is too high.
ASMiniDumpHealthRule             True PowerPivot: One or more minidump files were found in the Logs directory, indicating a program crash
ASUsageCubeRule                  True PowerPivot: Usage data is not getting updated at the expected frequency.
ASADOMDNETHealthRule             True PowerPivot: ADOMD.NET is not installed on a standalone WFE that is configured for central admin
MidTierAcctReadPermissionRule    True PowerPivot: MidTier process account should have 'Full Read' permission on all associated SPWebApplications.
```

##  <a name="windows-and-uls-logs"></a><a name="bkmk_logs"></a>Journaux Windows et ULS
 **Journal des événements Windows**

 La commande suivante recherche le journal des événements Windows pour les événements associés à l'instance d' [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] en mode SharePoint. Pour plus d’informations sur la désactivation des événements ou la modification du niveau d’événement, consultez [configurer et afficher les fichiers journaux SharePoint et la journalisation des diagnostics &#40;PowerPivot pour SharePoint&#41;](../../power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging.md).

 **Nom du service :** MSOLAP$POWERPIVOT

 **Afficher le nom dans les services Windows :** SQL Server Analysis Services (POWERPIVOT)

```powershell
Get-EventLog "application" | Where-Object {$_.source -Like "msolap`$powerpivot*"}  | Select timegenerated, entrytype , source, message | Format-Table -property * -AutoSize | Out-Default
```

```Output
TimeGenerated           EntryType Source            Message
-------------           --------- ------            -------
4/16/2014 1:45:19 PM  Information MSOLAP$POWERPIVOT Software usage metrics are disabled.
4/16/2014 1:45:19 PM  Information MSOLAP$POWERPIVOT Service started. Microsoft SQL Server Analysis Services 64 Bit Evaluation (x64) RTM 12.0.1997.5.
4/16/2014 1:45:18 PM  Information MSOLAP$POWERPIVOT The flight recorder was started.
4/14/2014 6:45:37 PM  Information MSOLAP$POWERPIVOT Software usage metrics are disabled.
```

 **Journaux ULS SharePoint, dernières 48 heures**

 La commande suivante retourne les messages de [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] du journal ULS créés au cours des dernières 48 heures. Ajustez le paramètre addhours selon vos besoins.

```powershell
Get-SPLogEvent -StartTime(Get-Date).AddHours(-48) | Where-Object {$_.Area -eq "powerpivot service" -and $_.level -eq "high"} | Select timestamp, area, category, eventid,level, message | Format-Table -Property * -AutoSize | Out-Default
```

 La variante suivante de la commande retourne uniquement les journaux d'événements de la catégorie **Actualisation des données** .

```powershell
Get-SPLogEvent -starttime(Get-Date).addhours(-48) | Where-Object {$_.category -eq "data refresh" -and $_.level -eq "high"} | Select timestamp, area, category, eventid, level, correlation, message
```

```Output
Timestamp   : 4/14/2014 7:15:01 PM
Area        : PowerPivot Service
Category    : Data Refresh
EventID     : 43
Level       : High
Correlation : 5755879c-7cab-e097-8f80-f27895d44a77
Message     : The following error occurred when working with the service application, Default PowerPivot Service Application. Skipping the service application..

Timestamp   : 4/14/2014 7:15:02 PM
Area        : PowerPivot Service
Category    : Data Refresh
EventID     : 99
Level       : High
Correlation : 5755879c-7cab-e097-8f80-f27895d44a77
Message     : EXCEPTION: System.TimeoutException: The request channel timed out while waiting for a reply after 00:00:47.0625313. Increase the timeout value passed to 
              the call to Request or increase the SendTimeout value on the Binding. The time allotted to this operation may have been a portion of a longer timeout. 
              ---> System.TimeoutException: The HTTP request to 'http://localhost:32843/SecurityTokenServiceApplication/securitytoken.svc/actas' has exceeded the 
              allotted timeout of 00:00:54.5930000. The time allotted to this operation may have been a portion of a longer timeout. ---> System.Net.WebException: The 
              operation has timed out     at System.Net.HttpWebRequest.GetResponse()     at 
              System.ServiceModel.Channels.HttpChannelFactory`1.HttpRequestChannel.HttpChannelRequest.WaitForReply(TimeSpan timeout...
```

##  <a name="msolap-provider"></a><a name="bkmk_msolap"></a>Fournisseur MSOLAP
 Vérifiez le fournisseur MSOLAP. [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]et [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] requièrent MSOLAP. 5.

```powershell
$excelApp = Get-SPExcelServiceApplication
Get-SPExcelDataProvider -ExcelServiceApplication $excelApp | Select providerid, providertype, description | Where {$_.providerid -like "msolap*" } | Format-Table -Property * -AutoSize | Out-Default
```

```Output
ProviderId ProviderType Description
---------- ------------ -----------
MSOLAP     Oledb        Microsoft OLE DB Provider for OLAP Services     
MSOLAP.3   Oledb        Microsoft OLE DB Provider for OLAP Services 9.0 
MSOLAP.4   Oledb        Microsoft OLE DB Provider for OLAP Services 10.0
MSOLAP.5   Oledb        Microsoft OLE DB Provider for OLAP Services 11.0
```

 Pour plus d’informations, voir [Installer le fournisseur OLE DB Analysis Services sur les serveurs SharePoint](../../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md) et [Ajouter MSOLAP.5 en tant que fournisseur de données approuvé dans Excel Services](https://technet.microsoft.com/library/hh758436.aspx).

##  <a name="adomdnet-client-library"></a><a name="bkmk_adomd"></a>Bibliothèque cliente ADOMD.Net

```powershell
Get-WMIObject -Class win32_product | Where-Object {$_.name -Like "*ado*"} | Select name, version, vendor | Format-Table -Property * -AutoSize | out-default
```

```Output
name                                                  version      vendor
----                                                  -------      ------
Microsoft SQL Server 2008 Analysis Services ADOMD.NET 10.1.2531.0  Microsoft Corporation
Microsoft SQL Server 2005 Analysis Services ADOMD.NET 9.00.1399.06 Microsoft Corporation
```

 Pour plus d’informations, consultez [Installer ADOMD.NET sur des serveurs web frontaux exécutant l’Administration centrale](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md).

##  <a name="health-data-collection-rules"></a><a name="bkmk_health_collection"></a>Règles de collecte des données d’intégrité
 Vérifiez que l' **État** est en ligne et que la valeur **Activé** est True.

```powershell
Get-SPUsageDefinition | Select name, status, enabled, tablename, DaysToKeepDetailedData | Where {$_.name -Like "powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                         Status Enabled TableName                   DaysToKeepDetailedData
----                         ------ ------- ---------                   ----------------------
PowerPivot Connections       OnlineTrue AnalysisServicesConnections  14
PowerPivot Load Data Usage   Online    True AnalysisServicesLoads                           14
PowerPivot Query Usage       Online    True AnalysisServicesRequests                        14
PowerPivot Unload Data Usage Online    True AnalysisServicesUnloads                         14
```

 Pour plus d'informations, consultez [PowerPivot Usage Data Collection](../../power-pivot-sharepoint/power-pivot-usage-data-collection.md).

##  <a name="solutions"></a><a name="bkmk_solutions"></a>Elles
 Si les autres composants sont en ligne, vous pouvez ignorer la vérification des solutions. Toutefois, si les règles d'intégrité sont absentes, vérifiez que les deux solutions existent et sont affichées, puis vérifiez que les deux solutions PowerPivot sont **En ligne** et **Déployées**.

```powershell
Get-SPSolution | Select name, status, deployed, DeploymentState, DeployedServers | Where {$_.Name -Like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

SharePoint 2013 :

```Output
Name                                 Status Deployed        DeploymentState DeployedServers
----                                 ------ --------        --------------- ---------------
powerpivotfarm14solution.wsp         Online     True         GlobalDeployed {UETESTA00}
powerpivotfarmsolution.wsp           Online     True         GlobalDeployed {UETESTA00}
powerpivotwebapplicationsolution.wsp Online     True WebApplicationDeployed {UETESTA00}
```

SharePoint 2010 :

```Output
Name                 Status Deployed        DeploymentState DeployedServers 
----                 ------ --------        --------------- --------------- 
powerpivotfarm.wsp   Online     True         GlobalDeployed {uesql11spoint2}
powerpivotwebapp.wsp Online     True WebApplicationDeployed {uesql11spoint2}
```

 Pour plus d’informations sur le déploiement des solutions SharePoint, consultez [Déployer des packages de solutions (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262995\(v=office.14\).aspx).

##  <a name="manual-verification-steps"></a><a name="bkmk_manual"></a> Étapes manuelles de contrôle
 Cette section décrit les étapes de vérification qui ne peuvent pas être effectuées par des applets de commande PowerShell.

 **Actualisation de données planifiée :** configurez la planification d'actualisation d'un classeur sur **Aussi actualiser dès que possible**.  Pour plus d’informations, consultez la section « vérifier l’actualisation des données » de planification de l' [actualisation des données et des sources de données qui ne prennent pas en charge l’authentification Windows &#40;PowerPivot pour SharePoint&#41;](../../power-pivot-sharepoint/schedule-data-refresh-and-data-sources-no-windows-authentication.md).

##  <a name="more-resources"></a><a name="bkmk_more_resources"></a>Plus de ressources
 [Applets de commande de l’administration du serveur Web (IIS) dans Windows PowerShell](https://technet.microsoft.com/library/ee790599.aspx).

 [PowerShell pour activer les services, les sites IIS et l'état du pool d'applications dans SharePoint](https://gallery.technet.microsoft.com/office/PowerShell-to-check-a6ed72a0).

 [Référence Windows PowerShell pour SharePoint 2013](https://technet.microsoft.com/library/ee890108\(v=office.15\).aspx)

 [Référence Windows PowerShell pour SharePoint Foundation 2010](https://technet.microsoft.com/library/ee890105\(v=office.14\).aspx)

 [Gérer Excel Services avec Windows PowerShell (SharePoint Server 2010)](https://technet.microsoft.com/library/ff191201\(v=office.14\).aspx)

 [Afficher et lire les fichiers journaux d'installation de SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)

 [Utiliser l'applet de commande Get-EvenLog](https://technet.microsoft.com/library/ee176846.aspx)

##  <a name="full-powershell-script"></a><a name="bkmk_full_script"></a>Script PowerShell complet
 Le script suivant contient toutes les commandes des sections précédentes. Il exécute les commandes dans l'ordre dans lequel elles sont présentées dans cette rubrique. Le script contient les variantes facultatives des commandes, indiquées dans cette rubrique au cas où vous auriez besoin d'un filtrage supplémentaire. Les variantes sont désactivées par un caractère de commentaire (#). Le script inclut également des instructions pour vérifier le mode SharePoint de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] . Les instructions [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] sont désactivées par un caractère de commentaire (#).

```powershell
# This script audits services related to PowerPivot for SharePoint
$starttime = Get-Date
write-host -foregroundcolor DarkGray StartTime $starttime

Write-Host  "Import the SharePoint PowerShell snappin"
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0

Write-Host -ForegroundColor Green "Analysis Services Windows Service"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-Service | Select name, displayname, status | Where {$_.Name -eq "msolap`$powerpivot"} | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "PowerPivotEngineService and PowerPivotSystemService"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"

Get-PowerPivotSystemService | Select typename, status, applications, farm | Format-Table -property * -AutoSize | Out-Default
# If needed, you can run the following to compare job definitions specific to the service against the results of the timer job definition section
#Get-PowerPivotSystemService | select -ExpandProperty jobdefinitions | select displayname, schedule, service | format-table -property * -autosize | out-default

Get-PowerPivotEngineService | Select typename, status, name, instances, farm | Format-Table -property * -AutoSize | Out-Default
# If needed, you can run the following to compare job definitions specific to the service against the results of the timer job definition section
#Get-PowerPivotEngineService | select -ExpandProperty jobdefinitions | select displayname, schedule, service | format-table -property * -autosize | out-default

#Write-Host -ForegroundColor Green "Service Instances - optional if you want to associate services with the server"
#Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
#Get-SPServiceInstance | select typename, status, server, service, instance | where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*excel*" -or $_.TypeName -like "*Analysis Services*"} | format-table -property * -autosize | out-default
#Get-PowerPivotEngineServiceInstance  | select typename, ASServername, status, server, service, instance
#Get-PowerPivotSystemServiceInstance  | select typename, ASSServerName, status, server, service, instance

Write-Host -ForegroundColor Green "PowerPivot And Excel Service Applications"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-PowerPivotServiceApplication | Select typename,name, status, unattendedaccount, applicationpool, farm, database
Get-SPExcelServiceApplication | Select typename,  DisplayName, status

#Write-Host ""
Write-Host -ForegroundColor Green "PowerPivot Service Application pool"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
# the following assumes there is only 1 PowerPivot Service Application, and returns that application's pool name.  if you have more than one, use the 2nd version
$poolname = [string](Get-PowerPivotServiceApplication | Select -Property applicationpool)
$position = $poolname.lastindexof("=")
$poolname = $poolname.substring($position+1)
$poolname = $poolname.substring(0,$poolname.length-1)
Get-SPServiceApplicationPool | Select name, status, processaccountname, id | Where {$_.Name -eq $poolname} | Format-Table -Property * -AutoSize | Out-Default

#Write-Host ""
Write-Host -ForegroundColor Green "PowerPivot and Excel Service Application Proxy"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPServiceApplicationProxy |  Select typename, status, unattendedaccount, displayname | Where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*excel services*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPServiceApplicationProxy |  select typename, status, unattendedaccount, displayname | where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*Reporting Services*" -or $_.TypeName -like "*excel services*"} | format-table -property * -autosize | out-default

Write-Host -ForegroundColor Green "DATABASES"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPDatabase | Select name, status, server, typename | Where {$_.TypeName -eq "content database" -or $_.TypeName -like "*Gemini*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPDatabase | select name, status, server, typename | where {$_.TypeName -eq "content database" -or $_.TypeName -like "*Gemini*" -or $_.TypeName -like "*ReportingServices*"}

Write-Host -ForegroundColor Green "features"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPFeature | Select displayname, status, scope, farm | Where {$_.displayName -like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPFeature | select displayname, status, scope, farm | where {$_.displayName -like "*powerpivot*" -or $_.displayName -like "*ReportServer*"}  | format-table -property * -autosize | out-default

Write-Host -ForegroundColor Green "Timer Jobs (Job Definitions) -- list is the same as seen in the 'Review timer job definitions' section of the management dashboard"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPTimerJob | Where {$_.service -like "*power*" -or $_.service -like "*mid*"} | Select status, displayname, LastRunTime, service | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "health rules"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPHealthAnalysisRule | Select name, enabled, summary | Where {$_.summary -Like "*power*"}  | Format-Table -Property * -AutoSize | Out-Default

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time

Write-Host -ForegroundColor Green "Windows Event Log data MSSQL$POWERPIVOT and "
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-EventLog "application" | Where-Object {$_.source -like "msolap`$powerpivot*"}  | Select timegenerated, entrytype , source, message | Format-Table -Property * -autosize | Out-Default
#The following is the same command but with the Inforamtion events filtered out.
#Get-EventLog "application" | Where-Object {$_.source -like "msolap`$powerpivot*" -and ($_.entrytype -match "error" -or $_.entrytype -match "critical" -or $_.entrytype -match "warning")}  |select timegenerated, entrytype , source, message | format-table -property * -autosize | out-default

#Write-Host ""
Write-Host -ForegroundColor Green "ULS Log data"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPLogEvent -StartTime(Get-Date).AddHours(-48) | Where-Object {$_.Area -eq "powerpivot service" -and $_.level -eq "high"} | Select timestamp, area, category, eventid, level, correlation, message | Format-Table -Property * -AutoSize | Out-Default
#the following example filters for the category 'data refresh'
#Get-SPLogEvent -starttime(get-date).addhours(-48) | Where-Object {$_.category -eq "data refresh" -and $_.level -eq "high"} | select timestamp, area, category, eventid, level, correlation, message

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time

Write-Host -ForegroundColor Green "MSOLAP data provider for Excel Servivces, service application"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
$excelApp = Get-SPExcelServiceApplication
Get-SPExcelDataProvider -ExcelServiceApplication $excelApp | Select providerid, providertype, description | Where {$_.providerid -like "msolap*" } | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "ADOMD.net client library"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-WMIObject -Class win32_product | Where-Object {$_.name -like "*ado*"} | Select name, version, vendor | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "Usage Data Rules"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPUsageDefinition | Select name, status, enabled, tablename, DaysToKeepDetailedData | Where {$_.name -like "powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "Solutions"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPSolution | Select name, status, deployed, DeploymentState, DeployedServers | Where {$_.Name -like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time
