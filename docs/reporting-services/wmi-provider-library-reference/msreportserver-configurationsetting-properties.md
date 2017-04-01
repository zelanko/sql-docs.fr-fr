---
title: "Propri&#233;t&#233;s MSReportServer_ConfigurationSetting | Microsoft Docs"
ms.custom: 
  - "force 2/17"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "MSReportServer_ConfigurationSetting Properties"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "fournisseur WMI [Reporting Services], classe MSReportServer_ConfigurationSetting"
  - "classe MSReportServer_ConfigurationSetting"
ms.assetid: e75fe1e5-197b-4c65-859b-370821cad003
caps.latest.revision: 48
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 45
---
# Propri&#233;t&#233;s MSReportServer_ConfigurationSetting
  La classe MSReportServer_ConfigurationSetting représente les paramètres d’installation et d’exécution d’une instance de serveur de rapports. Ces paramètres sont stockés dans le fichier de configuration RSReportServer.config.  
  
## Propri&amp;#233;t&amp;#233;s publiques  
  
|||  
|-|-|  
|[ConnectionPoolSize](../../reporting-services/wmi-provider-library-reference/connectionpoolsize-property-wmi-msreportserver-configurationsetting.md)|Retourne la taille du pool de connexions qu'utilise le serveur de rapports pour communiquer avec l'instance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui héberge la base de données du serveur de rapports. En lecture seule.|  
|[DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/databaselogonaccount-property-wmi-msreportserver-configurationsetting.md)|Spécifie le compte d'ouverture de session utilisé par le serveur de rapports pour se connecter à l'instance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui héberge la base de données du serveur de rapports. En lecture seule.|  
|[DatabaseLogonTimeout](../../reporting-services/wmi-provider-library-reference/databaselogontimeout-property-wmi-msreportserver-configurationsetting.md)|Spécifie le délai d'attente, en secondes, avant l'échec d'une tentative de connexion à la base de données du serveur de rapports. En lecture seule.|  
|[DatabaseLogonType](../../reporting-services/wmi-provider-library-reference/databaselogontype-property-wmi-msreportserver-configurationsetting.md)|Spécifie si le serveur de rapports utilise un compte de service Windows, un compte d'utilisateur Windows ou un compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour accéder à la base de données du serveur de rapports. En lecture seule.|  
|[DatabaseName](../../reporting-services/wmi-provider-library-reference/databasename-property-wmi-msreportserver-configurationsetting.md)|Spécifie le nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge la base de données du serveur de rapports.|  
|[DatabaseQueryTimeout](../../reporting-services/wmi-provider-library-reference/databasequerytimeout-property-wmi-msreportserver-configurationsetting.md)|Spécifie le délai, en secondes, au terme duquel la commande échoue ou expire. Le serveur de rapports établit la valeur de minutage du processus par rapport au catalogue SQL Server et non par rapport à une source de données du rapport.|  
|[DatabaseServerName](../../reporting-services/wmi-provider-library-reference/databaseservername-property-wmi-msreportserver-configurationsetting.md)|Spécifie le nom du serveur sur lequel la base de données du serveur de rapports est installée.|  
|[Propriété InstallationID](../../reporting-services/wmi-provider-library-reference/installationid-property-wmi-msreportserver-configurationsetting.md)|Retourne un identificateur unique pour une instance de serveur de rapports spécifique.|  
|[InstanceName](../../reporting-services/wmi-provider-library-reference/instancename-property-wmi-msreportserver-configurationsetting.md)|Spécifie le nom d'une instance de serveur de rapports sur un ordinateur spécifique.|  
|[IsInitialized](../../reporting-services/wmi-provider-library-reference/isinitialized-property-wmi-msreportserver-configurationsetting.md)|Indique si l'instance de serveur de rapports est initialisée.  En lecture seule.|  
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
  
## Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  