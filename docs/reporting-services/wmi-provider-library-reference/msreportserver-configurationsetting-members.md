---
title: "Membres MSReportServer_ConfigurationSetting | Microsoft Docs"
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
  - "MSReportServer_ConfigurationSetting Members"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "fournisseur WMI [Reporting Services], classe MSReportServer_ConfigurationSetting"
  - "classe MSReportServer_ConfigurationSetting"
ms.assetid: 5e21a53a-a2f8-4b35-a8d9-5483519e3857
caps.latest.revision: 46
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 46
---
# Membres MSReportServer_ConfigurationSetting
  La classe MSReportServer_ConfigurationSetting contient les propriétés et méthodes suivantes.  
  
## Propri&amp;#233;t&amp;#233;s publiques  
  
|||  
|-|-|  
|[ConnectionPoolSize](../../reporting-services/wmi-provider-library-reference/connectionpoolsize-property-wmi-msreportserver-configurationsetting.md)|Retourne la taille du pool de connexions qu'utilise le serveur de rapports pour communiquer avec l'instance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui héberge la base de données du serveur de rapports. En lecture seule.|  
|[DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/databaselogonaccount-property-wmi-msreportserver-configurationsetting.md)|Spécifie le compte de connexion utilisé par le serveur de rapports pour se connecter à l'instance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui héberge la base de données du serveur de rapports. En lecture seule.|  
|[DatabaseLogonTimeout](../../reporting-services/wmi-provider-library-reference/databaselogontimeout-property-wmi-msreportserver-configurationsetting.md)|Spécifie le délai d'attente, en secondes, avant l'échec d'une tentative de connexion à la base de données du serveur de rapports. En lecture seule.|  
|[DatabaseLogonType](../../reporting-services/wmi-provider-library-reference/databaselogontype-property-wmi-msreportserver-configurationsetting.md)|Spécifie si le serveur de rapports utilise un compte de service Windows, un compte d'utilisateur Windows ou un compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour accéder à la base de données du serveur de rapports. En lecture seule.|  
|[DatabaseName](../../reporting-services/wmi-provider-library-reference/databasename-property-wmi-msreportserver-configurationsetting.md)|Spécifie le nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge la base de données du serveur de rapports.|  
|[DatabaseQueryTimeout](../../reporting-services/wmi-provider-library-reference/databasequerytimeout-property-wmi-msreportserver-configurationsetting.md)|Spécifie le délai, en secondes, au terme duquel la commande échoue ou expire. Le serveur de rapports établit la valeur de minutage du processus par rapport à la base de données du serveur de rapports, et non par rapport à une source de données du rapport.|  
|[DatabaseServerName](../../reporting-services/wmi-provider-library-reference/databaseservername-property-wmi-msreportserver-configurationsetting.md)|Spécifie le nom du serveur sur lequel la base de données du serveur de rapports est installée.|  
|[Propriété InstallationID](../../reporting-services/wmi-provider-library-reference/installationid-property-wmi-msreportserver-configurationsetting.md)|Retourne un identificateur unique pour une instance de serveur de rapports spécifique.|  
|[InstanceName](../../reporting-services/wmi-provider-library-reference/instancename-property-wmi-msreportserver-configurationsetting.md)|Spécifie le nom d'une instance de serveur de rapports sur un ordinateur spécifique.|  
|[IsInitialized](../../reporting-services/wmi-provider-library-reference/isinitialized-property-wmi-msreportserver-configurationsetting.md)|Indique si l'instance de serveur de rapports est initialisée. En lecture seule.|  
|[IsSharePointIntegrated](../../reporting-services/wmi-provider-library-reference/issharepointintegrated-property-wmi.md)|Indique si le serveur de rapports est configuré pour le mode intégré SharePoint.|  
|[IsWebServiceEnabled](../../reporting-services/wmi-provider-library-reference/iswebserviceenabled-property-wmi-msreportserver-configurationsetting.md)|Indique si le service Web Report Server est activé. En lecture seule.|  
|[IsWindowsServiceEnabled](../../reporting-services/wmi-provider-library-reference/iswindowsserviceenabled-property-wmi-msreportserver-configurationsetting.md)|Indique si le service Windows Report Server est activé. En lecture seule.|  
|[Propriété MachineAccountIdentity &#40;WMI&#41;](../../reporting-services/wmi-provider-library-reference/machineaccountidentity-property-wmi.md)|Obtient l'identité du compte d'ordinateur de l'ordinateur sur lequel le serveur de rapports est installé.|  
|[PathName](../../reporting-services/wmi-provider-library-reference/pathname-property-wmi-msreportserver-configurationsetting.md)|Spécifie le chemin d'installation d'une instance de serveur de rapports.|  
|[SecureConnectionLevel](../../reporting-services/wmi-provider-library-reference/secureconnectionlevel-property-wmi-msreportserver-configurationsetting.md)|Retourne le niveau de connexion sécurisée qui est spécifié dans le fichier RSReportServer.config.|  
|[SenderEmailAddress](../../reporting-services/wmi-provider-library-reference/senderemailaddress-property-wmi-msreportserver-configurationsetting.md)|Obtient l'adresse utilisée pour l'envoi de messages électroniques à partir du serveur de rapports. En lecture seule.|  
|[SendUsingSMTPServer](../../reporting-services/wmi-provider-library-reference/sendusingsmtpserver-property-wmi-msreportserver-configurationsetting.md)|Spécifie si la propriété SendUsing dans la configuration de la messagerie a la valeur TRUE.|  
|[SMTPServer](../../reporting-services/wmi-provider-library-reference/smtpserver-property-wmi-msreportserver-configurationsetting.md)|Obtient la propriété du serveur SMTP à partir du fichier RSReportServer.config. En lecture seule.|  
|[UnattendedExecutionAccount](../../reporting-services/wmi-provider-library-reference/unattendedexecutionaccount-property-wmi-msreportserver-configurationsetting.md)|Spécifie le compte d'utilisateur de connexion dont le serveur de rapports emprunte l'identité lorsqu'il exécute des rapports sans assistance. En lecture seule.|  
|[Version](../../reporting-services/wmi-provider-library-reference/version-property-wmi-msreportserver-configurationsetting.md)|Retourne la version du serveur de rapports.|  
|[Propriété VirtualDirectoryReportManager &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/virtualdirectoryreportmanager-property-wmi-msreportserver-configurationsetting.md)|Retourne le répertoire virtuel de l'application Gestionnaire de rapports.|  
|[Propriété VirtualDirectoryReportServer &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/virtualdirectoryreportserver-property-wmi-msreportserver-configurationsetting.md)|Retourne le répertoire virtuel de l'application de service Web Report Server.|  
|[WindowsServiceIdentityActual](../../reporting-services/wmi-provider-library-reference/windowsserviceidentityactual-property-wmi-msreportserver-configurationsetting.md)|Retourne l'identité sous laquelle le service Windows Report Server s'exécute en réalité. En lecture seule.|  
|[WindowsServiceIdentityConfigured](../../reporting-services/wmi-provider-library-reference/windowsserviceidentityconfigured-property.md)|Retourne l'identité sous laquelle le service Windows Report Server a été configuré la dernière fois pour son exécution. En lecture seule.|  
  
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
|[Méthode ListInstalledSharePointVersions &#40;WMI&#41;](../../reporting-services/wmi-provider-library-reference/listinstalledsharepointversions-method-wmi.md)|Retourne un ensemble de jetons qui représentent les versions de [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]ou [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installées sur le même ordinateur que le serveur de rapports.|  
|[Méthode ListIPAddresses &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/listipaddresses-method-wmi-msreportserver-configurationsetting.md)|Répertorie les adresses IP de l'ordinateur.|  
|[ListReportServersInDatabase](../../reporting-services/wmi-provider-library-reference/listreportserversindatabase-method-wmi-msreportserver-configurationsetting.md)|Retourne une liste des installations du serveur de rapports qui sont présentes dans la base de données du serveur de rapports, même si ces installations n'ont pas accès aux informations sécurisées.|  
|[Méthode ListReservedURLs &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/listreservedurls-method-wmi-msreportserver-configurationsetting.md)|Répertorie les URL réservées pour toutes les applications sur le serveur de rapports.|  
|[Méthode ListSSLCertificateBindings &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/listsslcertificatebindings-method-wmi-msreportserver-configurationsetting.md)|Répertorie les liaisons de certificats SSL qui existent dans HTTP.SYS et celles attendues de rsreportserver.config.|  
|[Méthode ListSSLCertificates &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/listsslcertificates-method-wmi-msreportserver-configurationsetting.md)|Répertorie les certificats SSL installés sur l'ordinateur.|  
|[ReencryptSecureInformation](../../reporting-services/wmi-provider-library-reference/reencryptsecureinformation-method-wmi-msreportserver-configurationsetting.md)|Génère une nouvelle clé de chiffrement et rechiffre toutes les informations sécurisées dans la base de données du serveur de rapports à l'aide de cette nouvelle clé.|  
|[Méthode RemoveSSLCertificateBindings &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/removesslcertificatebindings-method-wmi-msreportserver-configurationsetting.md)|Supprime une liaison de certificat SSL.|  
|[RemoveUnattendedExecutionAccount](../../reporting-services/wmi-provider-library-reference/removeunattendedexecutionaccount-method-wmi-msreportserver-configurationsetting.md)|Supprime l'entrée de compte d'exécution sans assistance de la configuration du serveur de rapports.|  
|[Méthode RemoveURL &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/removeurl-method-wmi-msreportserver-configurationsetting.md)|Supprime une URL réservée pour le serveur de rapports.|  
|[Méthode ReserveURL &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/reserveurl-method-wmi-msreportserver-configurationsetting.md)|Ajoute une réservation d'URL pour une application donnée.|  
|[RestoreEncryptionKey](../../reporting-services/wmi-provider-library-reference/restoreencryptionkey-method-wmi-msreportserver-configurationsetting.md)|Réapplique la clé de chiffrement spécifiée à la base de données du serveur de rapports.|  
|[SetDatabaseConnection](../../reporting-services/wmi-provider-library-reference/setdatabaseconnection-method-wmi-msreportserver-configurationsetting.md)|Définit la connexion à une base de données de serveur de rapports spécifique.|  
|[SetDatabaseLogonTimeout](../../reporting-services/wmi-provider-library-reference/setdatabaselogontimeout-method-wmi-msreportserver-configurationsetting.md)|Spécifie la valeur du délai d'attente par défaut pour les tentatives d'ouverture de session de base de données du serveur de rapports.|  
|[SetDatabaseQueryTimeout](../../reporting-services/wmi-provider-library-reference/setdatabasequerytimeout-method-wmi-msreportserver-configurationsetting.md)|Spécifie la valeur de délai d'attente par défaut pour les connexions à la base de données du serveur de rapports.|  
|[SetEmailConfiguration](../../reporting-services/wmi-provider-library-reference/setemailconfiguration-method-wmi-msreportserver-configurationsetting.md)|Configure l'extension de remise par messagerie utilisée par le serveur de rapports pour envoyer des messages électroniques.|  
|[SetSecureConnectionLevel](../../reporting-services/wmi-provider-library-reference/setsecureconnectionlevel-method-wmi-msreportserver-configurationsetting.md)|Définit le niveau de connexion sécurisée du serveur de rapports.|  
|[SetServiceState](../../reporting-services/wmi-provider-library-reference/setservicestate-method-wmi-msreportserver-configurationsetting.md)|Active ou désactive les services Web et Windows Report Server.|  
|[SetUnattendedExecutionAccount](../../reporting-services/wmi-provider-library-reference/setunattendedexecutionaccount-method-wmi-msreportserver-configurationsetting.md)|Spécifie le compte utilisé pour exécuter les rapports sans assistance.|  
|[Méthode SetVirtualDirectory &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/setvirtualdirectory-method-wmi-msreportserver-configurationsetting.md)|Définit le répertoire virtuel pour une application.|  
|[SetWindowsServiceIdentity](../../reporting-services/wmi-provider-library-reference/setwindowsserviceidentity-method-wmi-msreportserver-configurationsetting.md)|Fait en sorte que le service Windows Report Server s'exécute en tant que l'utilisateur Windows spécifié et accorde des autorisations de système de fichiers suffisantes à ce compte pour permettre au serveur de rapports de fonctionner.|  
  
## Voir aussi  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
  