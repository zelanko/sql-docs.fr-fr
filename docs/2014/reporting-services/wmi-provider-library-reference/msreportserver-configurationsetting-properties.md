---
title: Propriétés MSReportServer_ConfigurationSetting | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- MSReportServer_ConfigurationSetting Properties
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services], MSReportServer_ConfigurationSetting class
- MSReportServer_ConfigurationSetting class
ms.assetid: e75fe1e5-197b-4c65-859b-370821cad003
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9c3937d888089f06435fece25e791b10ebbab785
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66097330"
---
# <a name="msreportserver_configurationsetting-properties"></a>Propriétés MSReportServer_ConfigurationSetting
  La classe MSReportServer_ConfigurationSetting représente les paramètres d’installation et d’exécution d’une instance de serveur de rapports. Ces paramètres sont stockés dans le fichier de configuration RSReportServer.config.  
  
## <a name="public-properties"></a>Propri&#233;t&#233;s publiques  
  
|||  
|-|-|  
|[ConnectionPoolSize](configurationsetting-property-connectionpoolsize.md)|Retourne la taille du pool de connexions utilisée par le serveur de rapports pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] communiquer avec l’instance qui héberge la base de données du serveur de rapports. Lecture seule.|  
|[DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md)|Spécifie le compte d’ouverture de session utilisé par le serveur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] rapports pour se connecter à l’instance qui héberge la base de données du serveur de rapports. Lecture seule.|  
|[DatabaseLogonTimeout](configurationsetting-property-databaselogontimeout.md)|Spécifie le délai d'attente, en secondes, avant l'échec d'une tentative de connexion à la base de données du serveur de rapports. Lecture seule.|  
|[DatabaseLogonType](configurationsetting-property-databaselogontype.md)|Spécifie si le serveur de rapports utilise un compte de service Windows, un compte d'utilisateur Windows ou un compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour accéder à la base de données du serveur de rapports. Lecture seule.|  
|[DatabaseName](configurationsetting-property-databasename.md)|Spécifie le nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge la base de données du serveur de rapports.|  
|[DatabaseQueryTimeout](configurationsetting-property-databasequerytimeout.md)|Spécifie le nombre de secondes qui doivent s’écouler avant que la commande échoue ou expire. Le serveur de rapports temporise le processus par rapport au catalogue de SQL Server, et non une source de données pour le rapport.|  
|[DatabaseServerName](configurationsetting-property-databaseservername.md)|Spécifie le nom du serveur sur lequel la base de données du serveur de rapports est installée.|  
|[Propriété InstallationID](configurationsetting-property-installationid.md)|Retourne un identificateur unique pour une instance de serveur de rapports spécifique.|  
|[InstanceName](configurationsetting-property-instancename.md)|Spécifie le nom d'une instance de serveur de rapports sur un ordinateur spécifique.|  
|[IsInitialized](configurationsetting-property-isinitialized.md)|Indique si l'instance de serveur de rapports est initialisée.  Lecture seule.|  
|[IsSharePointIntegrated](configurationsetting-property-issharepointintegrated.md)|Indique si le serveur de rapports est configuré pour le mode intégré SharePoint.|  
|[IsWebServiceEnabled](configurationsetting-property-iswebserviceenabled.md)|Indique si le service Web Report Server est activé. Lecture seule.|  
|[IsWindowsServiceEnabled](configurationsetting-property-iswindowsserviceenabled.md)|Indique si le service Windows Report Server est activé. Lecture seule.|  
|[Propriété MachineAccountIdentity &#40;WMI&#41;](configurationsetting-property-machineaccountidentity.md)|Obtient l'identité du compte d'ordinateur de l'ordinateur sur lequel le serveur de rapports est installé.|  
|[PathName](configurationsetting-property-pathname.md)|Spécifie le chemin d'installation d'une instance de serveur de rapports.|  
|[SecureConnectionLevel](configurationsetting-property-secureconnectionlevel.md)|Retourne le niveau de connexion sécurisée qui est spécifié dans le fichier RSReportServer.config.|  
|[SenderEmailAddress](configurationsetting-property-senderemailaddress.md)|Obtient l'adresse utilisée pour l'envoi de messages électroniques à partir du serveur de rapports. Lecture seule.|  
|[SendUsingSMTPServer](configurationsetting-property-sendusingsmtpserver.md)|Spécifie si la propriété SendUsing dans la configuration de la messagerie a la valeur TRUE.|  
|[SMTPServer](configurationsetting-property-smtpserver.md)|Obtient la propriété du serveur SMTP à partir du fichier RSReportServer.config. Lecture seule.|  
|[UnattendedExecutionAccount](configurationsetting-property-unattendedexecutionaccount.md)|Spécifie le compte d'utilisateur de connexion dont le serveur de rapports emprunte l'identité lorsqu'il exécute des rapports sans assistance. Lecture seule.|  
|[Version](configurationsetting-property-version.md)|Retourne la version du serveur de rapports.|  
|[Propriété VirtualDirectoryReportManager &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-property-virtualdirectoryreportmanager.md)|Retourne le répertoire virtuel de l'application Gestionnaire de rapports.|  
|[Propriété VirtualDirectoryReportServer &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-property-virtualdirectoryreportserver.md)|Retourne le répertoire virtuel de l'application de service Web Report Server.|  
|[WindowsServiceIdentityActual](configurationsetting-property-windowsserviceidentityactual.md)|Retourne l'identité sous laquelle le service Windows Report Server s'exécute en réalité. Lecture seule.|  
|[WindowsServiceIdentityConfigured](windowsserviceidentityconfigured-property.md)|Retourne l'identité sous laquelle le service Windows Report Server a été configuré la dernière fois pour son exécution. Lecture seule.|  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
