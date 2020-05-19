---
title: Fonctionnalités de SQL Server abandonnées dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 0678bfbc-5d3f-44f4-89c0-13e8e52404da
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bf9e3f3e7bf2d170faf0eaab2be18098a24b52cc
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706968"
---
# <a name="discontinued-sql-server-features-in-sql-server-2014"></a>Fonctionnalités SQL Server supprimées dans SQL Server 2014
  Cette rubrique décrit des fonctionnalités qui ne sont plus disponibles dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
## <a name="discontinued-features-in-sssql14"></a>Fonctionnalités supprimées dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Pas de fonctionnalités supprimées dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
## <a name="discontinued-features-in-sssql11"></a>Fonctionnalités supprimées dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="discontinued-active-directory-helper-service"></a>Service Active Directory Helper  
 Le service Active Directory Helper et les composants associés ont été supprimés. Le tableau suivant répertorie les composants associés qui se trouvent par conséquent supprimés :  
  
|Category|Fonctionnalité supprimée|Remplacement|  
|--------------|--------------------------|-----------------|  
|Procédures stockées système|sp_ActiveDirectory_Obj<br /><br /> sp_ActiveDirectory_SCP<br /><br /> sp_ActiveDirectory_Start|Aucun remplacement disponible|  
  
## <a name="discontinued-features-in-sql-server-2008-r2"></a>Fonctionnalités supprimées dans SQL Server 2008 R2  
  
### <a name="64-bit-platform-support-in-reporting-services"></a>Support de plate-forme 64 bits dans Reporting Services  
 À partir de [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], le composant [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne prend plus en charge les serveurs Itanium qui exécutent Windows Server 2003 ou Windows Server 2003 R2. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] continue à prendre en charge d'autres systèmes d'exploitation 64 bits, notamment Windows Server 2008 et Windows Server 2008 R2 pour les systèmes Itanium. Pour effectuer une mise à niveau vers [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] à partir d’une installation [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] avec [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sur une édition de système Itanium de Windows Server 2003 ou Windows Server 2003 R2, vous devez commencer par mettre à niveau le système d’exploitation.  
  
## <a name="discontinued-features-in-sql-server-2008"></a>Fonctionnalités supprimées dans SQL Server 2008  
  
### <a name="discontinued-sql-dmo-from-sql-server-express-installation"></a>Suppression de l'installation de SQL-DMO à partir de SQL Server Express  
 SQL-DMO pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a été supprimé de [!INCLUDE[ssExpressEd10](../includes/ssexpressed10-md.md)]. Nous vous recommandons de modifier le plus tôt possible les applications qui utilisent actuellement cette fonction. Si vous devez prendre en charge SQL-DMO pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express, installez les composants de compatibilité descendante à partir du [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] Feature Pack à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/). Utilisez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Objects (SMO) pour les nouveaux travaux de développement.  
  
### <a name="discontinued-option-for-web-assistant"></a>Suppression de l'option de l'Assistant Web  
 L'option `sp_configure` permettant d'activer l'Assistant Web est supprimée de [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]. Nous vous recommandons d'utiliser [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] à la place.  
  
### <a name="surface-area-configuration-tool"></a>Outil Configuration de la surface d’exposition  
 L’outil Configuration de la surface d’exposition n’est plus disponible pour [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] . La table suivante indique ce que vous pouvez utiliser pour configurer des paramètres, des options et des fonctionnalités de composant dans cette version.  
  
|Paramètres de remplacement et fonctionnalités de composant|Comment configurer|  
|-------------------------------------------------|----------------------|  
|Protocoles, connexion et options de démarrage|Utilisez le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|  
|Fonctionnalités [!INCLUDE[ssDE](../includes/ssde-md.md)]|Utilisez la Gestion basée sur une stratégie, les paramètres de propriétés dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou sp_Configure.|  
|Fonctionnalités [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|Utilisez les paramètres de propriétés dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] - Propriété EnableIntegratedSecurity|Utilisez les paramètres de propriétés dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] - « Événements programmés et remise du rapport » et « Service Web et accès HTTP »|Modifiez le fichier de configuration RSReportServer.config.|  
|Options de ligne de commande|Pas de prise en charge dans cette version.|  
|Points de terminaison SOAP et [!INCLUDE[ssSB](../includes/sssb-md.md)]|Utilisez [CREATE ENDPOINT](/sql/t-sql/statements/create-endpoint-transact-sql)et [ALTER ENDPOINT](/sql/t-sql/statements/alter-endpoint-transact-sql).|  
  
### <a name="discontinued-command-prompt-parameters-for-sql-server-setup"></a>Paramètres d'invite de commandes abandonnés pour l'installation de SQL Server  
 Le tableau suivant répertorie les paramètres d'invite de commandes d'installation des versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui ne sont pas pris en charge dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].  
  
|Paramètre abandonné|Paramètre de remplacement|  
|----------------------------|---------------------------|  
|ADDLOCAL|/ACTION=Uninstall et /FEATURES|  
|DISABLENETWORKPROTOCOLS|/TCPENABLED pour TCP/IP<sup>1</sup>|  
|DISABLENETWORKPROTOCOLS|/NPENABLED pour les canaux nommés<sup>1</sup>|  
|INSTALLSQLDATADIR|/SQLUSERDBDIR<br /><br /> /SQLUSERDBLOGDIR<br /><br /> /SQLBACKUPDIR<br /><br /> /SQLTEMPDBDIR<br /><br /> /SQLTEMPDBLOGDIR|  
|REINSTALL|Pas de fonction équivalente dans cette version.|  
|REINSTALLMODE|Pas de fonction équivalente dans cette version.|  
|REMOVE|/ACTION=Uninstall et /FEATURES|  
|SAMPLEDATABASE|Pas de fonction équivalente dans cette version.|  
|SAVESYSDB|Pas de fonction équivalente dans cette version.|  
|SKUUPGRADE<sup>2</sup>|Pas de fonction équivalente dans cette version.|  
|UPGRADE|/ACTION=Upgrade et /FEATURES|  
|USESYSDB|Pas de fonction équivalente dans cette version.|  
  
 <sup>1</sup> Ces paramètres sont valides uniquement pour l’installation.  
  
 <sup>2</sup> À partir de [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] , spécifiez/action = EditionUpgrade pour mettre à niveau une édition existante de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vers une édition différente à tout moment sans utiliser le support d’installation d’origine. Pour plus d'informations sur les mises à niveau des versions et éditions prises en charge, consultez [Supported Version and Edition Upgrades](../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
 Pour plus d’informations, consultez [Installer SQL Server 2014 à partir de l’invite de commandes](../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
  
