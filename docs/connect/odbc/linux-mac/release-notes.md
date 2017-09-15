---
title: "Notes de mise à jour-pilote Microsoft ODBC pour SQL Server sur Linux et macOS | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fe65ff49f5618634517b612c2430a3489ac11141
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="release-notes-for-the-microsoft-odbc-driver-for-sql-server-on-linux-and-macos"></a>Notes de publication pour le pilote Microsoft ODBC pour SQL Server sur Linux et Mac OS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-131-for-includessnoversionincludesssnoversionmdmd-on-linux-and-macos"></a>Nouveautés le [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13.1 pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sur Linux et Mac OS  

ODBC Driver 13.1 for [ ! INCLUDEssNoVersion] ajoute la prise en charge pour Always Encrypted et Azure Active Directory lorsqu’il est utilisé conjointement avec Microsoft SQL Server 2016. 

**Nouvelle prise en charge les distributions**: OS X 10.11 et macOS 10.12 sont pris en charge dans la première version du pilote ODBC sur macOS. 16.10 d’Ubuntu est maintenant également pris en charge, ainsi que Red Hat 6, 7 et SUSE 12. Chaque plateforme possède un package relatifs à la plate-forme (RPM ou DEB) pour faciliter l’installation et la configuration.  Consultez [l’installation du pilote](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) pour obtenir des instructions d’installation.

**unixODBC 2.3.1 du Gestionnaire de pilotes en charge les modifications**: le pilote ODBC ne dépend plus emballage personnalisé pour le Gestionnaire de pilotes unixODBC (sauf sur RedHat 6) et s’appuie sur le Gestionnaire de package de distribution pour résoudre la dépendance UnixODBC à partir des référentiels de la distribution.

**Prise en charge des API BCP**: Linux et macOS le pilote ODBC prend désormais en charge l’utilisation de la [fonctions de l’API BCP (**bcp_init**, etc..)](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)

## <a name="whats-new-in-the-microsoft-odbc-driver-130-for-includessnoversionincludesssnoversionmdmd-on-linux"></a>Nouveautés de Microsoft ODBC Driver 13.0 pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sur Linux  
Avec Microsoft ODBC Driver 13.0 pour SQL Server, SQL Server 2014 et SQL Server 2016 sont maintenant également pris en charge.  
  
**Nouvelle prise en charge les distributions**:

Ubuntu est maintenant pris en charge, ainsi que Red Hat et SUSE. Chaque plateforme possède un package relatifs à la plate-forme (RPM ou DEB) pour faciliter l’installation et la configuration.  Consultez [l’installation du pilote](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) pour obtenir des instructions d’installation.
  
**prise en charge 2.3.1 du Gestionnaire de pilotes unixODBC**: en plus d’un gestionnaire de pilotes plus récent, il existe également un package d’installation de cette dépendance qui facilite l’installation et la configuration.  

**La résolution IP réseau transparent**: la résolution IP réseau Transparent est une révision de la fonctionnalité de basculement de sous-réseaux multiples existante qui affecte la séquence de connexion du pilote dans le cas où le premier résolu n’est pas le cas de l’adresse IP du nom d’hôte répondre et qu’il existe plusieurs adresses IP associée avec le nom d’hôte.

**Prise en charge de TLS 1.2**: le 13.0 de pilote Microsoft ODBC pour SQL Server sur Linux prend désormais en charge TLS 1.2 lorsque sécuriser les communications avec SQL Server sont utilisées.

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-11-for-includessnoversionincludesssnoversionmdmd-on-linux"></a>Quelles sont les nouveautés le [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sur Linux  
Le pilote ODBC sur SUSE Linux (Preview) prend en charge 64 bits SUSE Linux Enterprise 11 Service Pack 2. Pour plus d’informations, consultez [requise](../../../connect/odbc/linux-mac/system-requirements.md).  
  
Le pilote ODBC sur Linux prend en charge [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]. Pour plus d’informations, consultez [du pilote ODBC pour la prise en charge Linux pour une haute disponibilité, la récupération d’urgence](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).  
  
Le pilote ODBC sur Linux prend en charge les connexions à Microsoft Azure SQL Database. Pour plus d’informations, consultez [How to: Connect to Windows Azure SQL Database Using ODBC](http://msdn.microsoft.com/library/hh974312.aspx).  
  
Le `-l` option (délai d’expiration de connexion) a été ajoutée à `bcp`. Pour plus d’informations, consultez [connexion avec **bcp**](../../../connect/odbc/linux-mac/connecting-with-bcp.md).
  

