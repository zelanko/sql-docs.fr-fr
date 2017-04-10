---
title: "M&#233;thodes MSReportServer_ConfigurationSetting | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "MSReportServer_ConfigurationSetting Methods"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "fournisseur WMI [Reporting Services], classe MSReportServer_ConfigurationSetting"
  - "classe MSReportServer_ConfigurationSetting"
ms.assetid: a08c2476-5b8e-4792-94da-1360fe231c6e
caps.latest.revision: 45
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 45
---
# M&#233;thodes MSReportServer_ConfigurationSetting
  La classe MSReportServer_ConfigurationSetting du Fournisseur WMI Report Server fournit les méthodes publiques suivantes.  
  
## M&amp;#233;thodes publiques  
  
|||  
|-|-|  
|[BackupEncryptionKey](../../reporting-services/wmi-provider-library-reference/backupencryptionkey-method-wmi-msreportserver-configurationsetting.md)|Sauvegarde la clé de chiffrement pour l'instance. Un chiffrement par mot de passe est utilisé pour le stockage de la clé de chiffrement.|  
|[Méthode CreateSSLCertificateBinding &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/createsslcertificatebinding-method-wmi-msreportserver-configurationsetting.md)|Crée une liaison de certificat SSL.|  
|[DeleteEncryptedInformation](../../reporting-services/wmi-provider-library-reference/deleteencryptedinformation-method-wmi-msreportserver-configurationsetting.md)|Supprime les informations chiffrées de la base de données du serveur de rapports.|  
|[DeleteEncryptionKey](../../reporting-services/wmi-provider-library-reference/deleteencryptionkey-method-wmi-msreportserver-configurationsetting.md)|Supprime les clés de chiffrement de la base de données du serveur de rapports.|  
|[GenerateDatabaseCreationScript](../../reporting-services/wmi-provider-library-reference/generatedatabasecreationscript-method-wmi-msreportserver-configurationsetting.md)|Génère un script SQL qui peut être utilisé pour créer la base de données du serveur de rapports.|  
|[GenerateDatabaseRightsScript](../../reporting-services/wmi-provider-library-reference/generatedatabaserightsscript-method-wmi-msreportserver-configurationsetting.md)|Génère un script SQL pouvant être utilisé pour accorder des autorisations d'utilisateurs à la base de données du serveur de rapports.|  
|[GenerateDatabaseUpgradeScript](../../reporting-services/wmi-provider-library-reference/generatedatabaseupgradescript-method-wmi-msreportserver-configurationsetting.md)|Génère un script SQL qui peut être utilisé pour mettre à niveau une base de données du serveur de rapports.|  
|[Méthode GetAdminSiteUrl &#40;WMI&#41;](../../reporting-services/wmi-provider-library-reference/getadminsiteurl-method-wmi.md)|Obtient l'URL absolue vers le site Web Administration centrale.|  
|[GetDatabaseVersionDisplayName](../../reporting-services/wmi-provider-library-reference/getdatabaseversiondisplayname-method-wmi.md)|Obtient le nom complet de la chaîne de version d'une base de données de serveur de rapports spécifique.|  
|[InitializeReportServer](../../reporting-services/wmi-provider-library-reference/initializereportserver-method-wmi-msreportserver-configurationsetting.md)|Initialise l'instance de serveur de rapports spécifiée.|  
|[Méthode ListInstalledSharePointVersions &#40;WMI&#41;](../../reporting-services/wmi-provider-library-reference/listinstalledsharepointversions-method-wmi.md)|Retourne un ensemble de jetons qui représentent les versions de Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]ou [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installés sur le même ordinateur que le serveur de rapports.|  
|[Méthode ListIPAddresses &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/listipaddresses-method-wmi-msreportserver-configurationsetting.md)|Répertorie les adresses IP de l'ordinateur.|  
|[ListReportServersInDatabase](../../reporting-services/wmi-provider-library-reference/listreportserversindatabase-method-wmi-msreportserver-configurationsetting.md)|Retourne une liste des installations du serveur de rapports qui sont présentes dans la base de données du serveur de rapports, même si ces installations n'ont pas accès aux informations sécurisées.|  
|[Méthode ListReservedURLs &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/listreservedurls-method-wmi-msreportserver-configurationsetting.md)|Répertorie les URL réservées pour toutes les applications sur le serveur de rapports.|  
|[Méthode ListSSLCertificateBindings &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/listsslcertificatebindings-method-wmi-msreportserver-configurationsetting.md)|Répertorie les liaisons de certificats SSL qui existent dans HTTP.SYS et celles attendues de RSReportServer.config.|  
|[Méthode ListSSLCertificates &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/listsslcertificates-method-wmi-msreportserver-configurationsetting.md)|Répertorie les certificats SSL installés sur l'ordinateur.|  
|[ReencryptSecureInformation](../../reporting-services/wmi-provider-library-reference/reencryptsecureinformation-method-wmi-msreportserver-configurationsetting.md)|Génère une nouvelle clé de chiffrement et rechiffre toutes les informations sécurisées dans la base de données du serveur de rapports à l'aide de cette nouvelle clé.|  
|[Méthode RemoveSSLCertificateBindings &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/removesslcertificatebindings-method-wmi-msreportserver-configurationsetting.md)|Supprime une liaison de certificat SSL.|  
|[RemoveUnattendedExecutionAccount](../../reporting-services/wmi-provider-library-reference/removeunattendedexecutionaccount-method-wmi-msreportserver-configurationsetting.md)|Supprime l'entrée de compte d'exécution sans assistance de la configuration du serveur de rapports.|  
|[Méthode RemoveURL &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/removeurl-method-wmi-msreportserver-configurationsetting.md)|Supprime une URL réservée pour le serveur de rapports.|  
|[Méthode ReserveURL &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/reserveurl-method-wmi-msreportserver-configurationsetting.md)|Ajoute une réservation d'URL pour une application donnée.|  
|[RestoreEncryptionKey](../../reporting-services/wmi-provider-library-reference/restoreencryptionkey-method-wmi-msreportserver-configurationsetting.md)|Réapplique la clé de chiffrement spécifiée à la base de données du serveur de rapports.|  
|[SetDatabaseConnection](../../reporting-services/wmi-provider-library-reference/setdatabaseconnection-method-wmi-msreportserver-configurationsetting.md)|Définit la connexion à une base de données de serveur de rapports spécifique.|  
|[SetDatabaseLogonTimeout](../../reporting-services/wmi-provider-library-reference/setdatabaselogontimeout-method-wmi-msreportserver-configurationsetting.md)|Spécifie la valeur du délai d'attente par défaut pour les tentatives d'ouverture de session de base de données du serveur de rapports.|  
|[SetDatabaseQueryTimeout](../../reporting-services/wmi-provider-library-reference/setdatabasequerytimeout-method-wmi-msreportserver-configurationsetting.md)|Spécifie la valeur de délai par défaut pour les requêtes sur la base de données du serveur de rapports.|  
|[SetEmailConfiguration](../../reporting-services/wmi-provider-library-reference/setemailconfiguration-method-wmi-msreportserver-configurationsetting.md)|Configure l'extension de remise par messagerie utilisée par le serveur de rapports pour envoyer des messages électroniques.|  
|[SetSecureConnectionLevel](../../reporting-services/wmi-provider-library-reference/setsecureconnectionlevel-method-wmi-msreportserver-configurationsetting.md)|Définit le niveau de connexion sécurisée du serveur de rapports.|  
|[SetServiceState](../../reporting-services/wmi-provider-library-reference/setservicestate-method-wmi-msreportserver-configurationsetting.md)|Active ou désactive le service Report Server.|  
|[SetUnattendedExecutionAccount](../../reporting-services/wmi-provider-library-reference/setunattendedexecutionaccount-method-wmi-msreportserver-configurationsetting.md)|Spécifie le compte utilisé pour exécuter les rapports sans assistance.|  
|[Méthode SetVirtualDirectory &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/setvirtualdirectory-method-wmi-msreportserver-configurationsetting.md)|Définit le répertoire virtuel pour une application.|  
|[SetWindowsServiceIdentity](../../reporting-services/wmi-provider-library-reference/setwindowsserviceidentity-method-wmi-msreportserver-configurationsetting.md)|Fait en sorte que le service Report Server s'exécute en tant que l'utilisateur Windows spécifié et accorde des autorisations de système de fichiers suffisantes à ce compte pour permettre au serveur de rapports de fonctionner.|  
  
## Voir aussi  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
  