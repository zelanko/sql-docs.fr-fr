---
title: Membres MSReportServer_ConfigurationSetting | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- MSReportServer_ConfigurationSetting Members
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services], MSReportServer_ConfigurationSetting class
- MSReportServer_ConfigurationSetting class
ms.assetid: 5e21a53a-a2f8-4b35-a8d9-5483519e3857
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 7acfc09d226c3e352feae42e76d85f1dd8d1a531
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56024170"
---
# <a name="msreportserverconfigurationsetting-members"></a>Membres MSReportServer_ConfigurationSetting
  La classe MSReportServer_ConfigurationSetting contient les propriétés et méthodes suivantes.  
  
## <a name="public-properties"></a>Propri&#233;t&#233;s publiques  
  
|||  
|-|-|  
|[ConnectionPoolSize](configurationsetting-property-connectionpoolsize.md)|Retourne la taille du pool de connexions qu'utilise le serveur de rapports pour communiquer avec l'instance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui héberge la base de données du serveur de rapports. En lecture seule.|  
|[DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md)|Spécifie le compte de connexion utilisé par le serveur de rapports pour se connecter à l'instance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui héberge la base de données du serveur de rapports. En lecture seule.|  
|[DatabaseLogonTimeout](configurationsetting-property-databaselogontimeout.md)|Spécifie le délai d'attente, en secondes, avant l'échec d'une tentative de connexion à la base de données du serveur de rapports. En lecture seule.|  
|[DatabaseLogonType](configurationsetting-property-databaselogontype.md)|Spécifie si le serveur de rapports utilise un compte de service Windows, un compte d'utilisateur Windows ou un compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour accéder à la base de données du serveur de rapports. En lecture seule.|  
|[DatabaseName](configurationsetting-property-databasename.md)|Spécifie le nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge la base de données du serveur de rapports.|  
|[DatabaseQueryTimeout](configurationsetting-property-databasequerytimeout.md)|Spécifie le délai, en secondes, au terme duquel la commande échoue ou expire. Le serveur de rapports établit la valeur de minutage du processus par rapport à la base de données du serveur de rapports, et non par rapport à une source de données du rapport.|  
|[DatabaseServerName](configurationsetting-property-databaseservername.md)|Spécifie le nom du serveur sur lequel la base de données du serveur de rapports est installée.|  
|[Propriété InstallationID](configurationsetting-property-installationid.md)|Retourne un identificateur unique pour une instance de serveur de rapports spécifique.|  
|[InstanceName](configurationsetting-property-instancename.md)|Spécifie le nom d'une instance de serveur de rapports sur un ordinateur spécifique.|  
|[IsInitialized](configurationsetting-property-isinitialized.md)|Indique si l'instance de serveur de rapports est initialisée. En lecture seule.|  
|[IsSharePointIntegrated](configurationsetting-property-issharepointintegrated.md)|Indique si le serveur de rapports est configuré pour le mode intégré SharePoint.|  
|[IsWebServiceEnabled](configurationsetting-property-iswebserviceenabled.md)|Indique si le service Web Report Server est activé. En lecture seule.|  
|[IsWindowsServiceEnabled](configurationsetting-property-iswindowsserviceenabled.md)|Indique si le service Windows Report Server est activé. En lecture seule.|  
|[Propriété MachineAccountIdentity &#40;WMI&#41;](configurationsetting-property-machineaccountidentity.md)|Obtient l'identité du compte d'ordinateur de l'ordinateur sur lequel le serveur de rapports est installé.|  
|[PathName](configurationsetting-property-pathname.md)|Spécifie le chemin d'installation d'une instance de serveur de rapports.|  
|[SecureConnectionLevel](configurationsetting-property-secureconnectionlevel.md)|Retourne le niveau de connexion sécurisée qui est spécifié dans le fichier RSReportServer.config.|  
|[SenderEmailAddress](configurationsetting-property-senderemailaddress.md)|Obtient l'adresse utilisée pour l'envoi de messages électroniques à partir du serveur de rapports. En lecture seule.|  
|[SendUsingSMTPServer](configurationsetting-property-sendusingsmtpserver.md)|Spécifie si la propriété SendUsing dans la configuration de la messagerie a la valeur TRUE.|  
|[SMTPServer](configurationsetting-property-smtpserver.md)|Obtient la propriété du serveur SMTP à partir du fichier RSReportServer.config. En lecture seule.|  
|[UnattendedExecutionAccount](configurationsetting-property-unattendedexecutionaccount.md)|Spécifie le compte d'utilisateur de connexion dont le serveur de rapports emprunte l'identité lorsqu'il exécute des rapports sans assistance. En lecture seule.|  
|[Version](configurationsetting-property-version.md)|Retourne la version du serveur de rapports.|  
|[Propriété VirtualDirectoryReportManager &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-property-virtualdirectoryreportmanager.md)|Retourne le répertoire virtuel de l'application Gestionnaire de rapports.|  
|[Propriété VirtualDirectoryReportServer &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-property-virtualdirectoryreportserver.md)|Retourne le répertoire virtuel de l'application de service Web Report Server.|  
|[WindowsServiceIdentityActual](configurationsetting-property-windowsserviceidentityactual.md)|Retourne l'identité sous laquelle le service Windows Report Server s'exécute en réalité. En lecture seule.|  
|[WindowsServiceIdentityConfigured](windowsserviceidentityconfigured-property.md)|Retourne l'identité sous laquelle le service Windows Report Server a été configuré la dernière fois pour son exécution. En lecture seule.|  
  
## <a name="public-methods"></a>M&#233;thodes publiques  
  
|||  
|-|-|  
|[BackupEncryptionKey](configurationsetting-method-backupencryptionkey.md)|Sauvegarde la clé de chiffrement pour l'instance. Un chiffrement par mot de passe est utilisé pour le stockage de la clé de chiffrement.|  
|[Méthode CreateSSLCertificateBinding &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-createsslcertificatebinding.md)|Crée une liaison de certificat SSL.|  
|[DeleteEncryptedInformation](configurationsetting-method-deleteencryptedinformation.md)|Supprime les informations chiffrées de la base de données du serveur de rapports.|  
|[DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md)|Supprime les clés de chiffrement de la base de données du serveur de rapports.|  
|[GenerateDatabaseCreationScript](configurationsetting-method-generatedatabasecreationscript.md)|Génère un script SQL qui peut être utilisé pour créer la base de données du serveur de rapports.|  
|[GenerateDatabaseRightsScript](configurationsetting-method-generatedatabaserightsscript.md)|Génère un script SQL pouvant être utilisé pour accorder des autorisations d'utilisateurs à la base de données du serveur de rapports.|  
|[GenerateDatabaseUpgradeScript](configurationsetting-method-generatedatabaseupgradescript.md)|Génère un script SQL qui peut être utilisé pour mettre à niveau une base de données du serveur de rapports.|  
|[Méthode GetAdminSiteUrl &#40;WMI&#41;](configurationsetting-method-getadminsiteurl.md)|Obtient l'URL absolue vers le site Web Administration centrale.|  
|[GetDatabaseVersionDisplayName](configurationsetting-method-getdatabaseversiondisplayname.md)|Obtient le nom complet de la chaîne de version d'une base de données de serveur de rapports spécifique.|  
|[InitializeReportServer](configurationsetting-method-initializereportserver.md)|Initialise l'instance de serveur de rapports spécifiée.|  
|[Méthode ListInstalledSharePointVersions &#40;WMI&#41;](configurationsetting-method-listinstalledsharepointversions.md)|Retourne un ensemble de jetons qui représentent les versions de [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]ou [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installées sur le même ordinateur que le serveur de rapports.|  
|[Méthode ListIPAddresses &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-listipaddresses.md)|Répertorie les adresses IP de l'ordinateur.|  
|[ListReportServersInDatabase](configurationsetting-method-listreportserversindatabase.md)|Retourne une liste des installations du serveur de rapports qui sont présentes dans la base de données du serveur de rapports, même si ces installations n'ont pas accès aux informations sécurisées.|  
|[Méthode ListReservedURLs &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-listreservedurls.md)|Répertorie les URL réservées pour toutes les applications sur le serveur de rapports.|  
|[Méthode ListSSLCertificateBindings &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-listsslcertificatebindings.md)|Répertorie les liaisons de certificats SSL qui existent dans HTTP.SYS et celles attendues de rsreportserver.config.|  
|[Méthode ListSSLCertificates &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-listsslcertificates.md)|Répertorie les certificats SSL installés sur l'ordinateur.|  
|[ReencryptSecureInformation](configurationsetting-method-reencryptsecureinformation.md)|Génère une nouvelle clé de chiffrement et rechiffre toutes les informations sécurisées dans la base de données du serveur de rapports à l'aide de cette nouvelle clé.|  
|[Méthode RemoveSSLCertificateBindings &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-removesslcertificatebinding.md)|Supprime une liaison de certificat SSL.|  
|[RemoveUnattendedExecutionAccount](configurationsetting-method-removeunattendedexecutionaccount.md)|Supprime l'entrée de compte d'exécution sans assistance de la configuration du serveur de rapports.|  
|[Méthode RemoveURL &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-removeurl.md)|Supprime une URL réservée pour le serveur de rapports.|  
|[Méthode ReserveURL &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-reserveurl.md)|Ajoute une réservation d'URL pour une application donnée.|  
|[RestoreEncryptionKey](configurationsetting-method-restoreencryptionkey.md)|Réapplique la clé de chiffrement spécifiée à la base de données du serveur de rapports.|  
|[SetDatabaseConnection](configurationsetting-method-setdatabaseconnection.md)|Définit la connexion à une base de données de serveur de rapports spécifique.|  
|[SetDatabaseLogonTimeout](configurationsetting-method-setdatabaselogontimeout.md)|Spécifie la valeur du délai d'attente par défaut pour les tentatives d'ouverture de session de base de données du serveur de rapports.|  
|[SetDatabaseQueryTimeout](configurationsetting-method-setdatabasequerytimeout.md)|Spécifie la valeur de délai d'attente par défaut pour les connexions à la base de données du serveur de rapports.|  
|[SetEmailConfiguration](configurationsetting-method-setemailconfiguration.md)|Configure l'extension de remise par messagerie utilisée par le serveur de rapports pour envoyer des messages électroniques.|  
|[SetSecureConnectionLevel](configurationsetting-method-setsecureconnectionlevel.md)|Définit le niveau de connexion sécurisée du serveur de rapports.|  
|[SetServiceState](configurationsetting-method-setservicestate.md)|Active ou désactive les services Web et Windows Report Server.|  
|[SetUnattendedExecutionAccount](configurationsetting-method-setunattendedexecutionaccount.md)|Spécifie le compte utilisé pour exécuter les rapports sans assistance.|  
|[Méthode SetVirtualDirectory &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md)|Définit le répertoire virtuel pour une application.|  
|[SetWindowsServiceIdentity](configurationsetting-method-setwindowsserviceidentity.md)|Fait en sorte que le service Windows Report Server s'exécute en tant que l'utilisateur Windows spécifié et accorde des autorisations de système de fichiers suffisantes à ce compte pour permettre au serveur de rapports de fonctionner.|  
  
## <a name="see-also"></a>Voir aussi  
 [MSReportServer_ConfigurationSetting Class](msreportserver-configurationsetting-class.md)  
  
  
