---
title: Configuration requise (ODBC Driver for SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 02/15/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- prerequisites
- system requirements
- requirements
ms.assetid: f03b7fdd-0e9d-4e74-958d-e8c87e027348
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9bc5f0a66cc891c1efa4810253a02d98f384e081
ms.sourcegitcommit: 577e7467821895f530ec2f97a33a965fca808579
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79058743"
---
# <a name="system-requirements"></a>Configuration requise
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Cette rubrique répertorie la configuration requise pour utiliser [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux et macOS.


## <a name="microsoft-odbc-driver-13-131-and-17-for-sql-server"></a>Microsoft ODBC Driver 13, 13.1 et 17 for SQL Server

Les pilotes Linux et macOS sont disponibles uniquement pour les versions 64 bits des systèmes d’exploitation suivants :

|Système d’exploitation|Version du pilote pris en charge|
|------------------------------------|--------------------------------|
|Apple OS X 10.11 (El Capitan)|13, 13.1, 17.4|
|Apple macOS 10.12 (Sierra)|13, 13.1, 17.4|
|Apple macOS 10.13 (High Sierra)|17+| 
|Apple macOS 10.14 (Mojave)|17+| 
|Apple macOS 10.15 (Catalina)|17.5+| 
|Alpine Linux 3.11|17.5+| 
|Debian Linux 8|13, 13.1, 17.4| 
|Debian Linux 9|17+|
|Debian Linux 10|17.4+|
|Oracle Linux 8|17.5+|
|Red Hat Enterprise Linux 6|13, 13.1, 17+|
|Red Hat Enterprise Linux 7|13, 13.1, 17+|
|RedHat Enterprise Linux 8|17.4+|
|SUSE Linux Enterprise Server 11|13, 13.1, 17+ <br /><br /> **REMARQUE :** ODBC Driver 17 prend uniquement en charge SUSE Linux Enterprise Server 11 SP4.|
|SUSE Linux Enterprise Server 12|13, 13.1, 17+|
|SUSE Linux Enterprise Server 15|17+|
|Ubuntu Linux 14.04|13, 13.1, 17.4|
|Ubuntu Linux 15.10|13, 13.1|
|Ubuntu Linux 16.04|13, 13.1, 17+|
|Ubuntu Linux 16.10|13, 13.1|
|Ubuntu Linux 17.04|17.4| 
|Ubuntu Linux 17.10|17.4|
|Ubuntu Linux 18.04|17+|
|Ubuntu Linux 18.10|17.4|
|Ubuntu Linux 19.04|17.3|
|Ubuntu Linux 19.10|17.5+| 

> [!NOTE]
> - Les systèmes d’exploitation avec prise en charge active présentent un « + » après la version du pilote. Ceux qui ne comportent pas le signe plus indiquent la dernière version du pilote prise en charge.

Les packages d’installation pour [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13, 13.1 et 17 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux et macOS résolvent automatiquement les dépendances du pilote quand ils sont installés à l’aide du système de gestion des packages de votre distribution, comme décrit dans [Installation du pilote](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

## <a name="microsoft-odbc-driver-11-for-sql-server"></a>Pilote Microsoft ODBC 11 pour SQL Server  
  
-   Gestionnaire de pilotes UnixODBC 2.3.0 64 bits, conçu pour SQLLEN/SQLULEN 64 bits. Les versions ultérieures du Gestionnaire de pilotes UnixODBC 64 bits ne sont pas prises en charge avec le pilote ODBC sur Linux. Consultez la rubrique [Installing the Driver Manager](../../../connect/odbc/linux-mac/installing-the-driver-manager.md) (éventuellement en anglais) pour plus d'informations.  
  
-   Les packages suivants sont nécessaires pour le pilote ODBC pour **Red Hat Enterprise Linux 5 (64 bits)** , téléchargeable suivant le lien [Microsoft ODBC Driver 11 for SQL Server – Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321) :  
    -   `glibc`  
    -   `libgcc`  
    -   `libstdc++`  
    -   `e2fsprogs-libs`  
    -   `krb5-libs`  
    -   `openssl`  
  
-   Les packages suivants sont nécessaires pour le pilote ODBC pour **Red Hat Enterprise Linux 6 (64 bits)** , téléchargeable suivant le lien [Microsoft ODBC Driver 11 for SQL Server – Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321) :  
    -   `glibc`  
    -   `libgcc`  
    -   `libstdc++`  
    -   `libuuid`  
    -   `krb5-libs`  
    -   `openssl`  
  
-   Les packages suivants sont nécessaires pour le pilote ODBC pour **SUSE Linux Enterprise 11 Service Pack 2 (64 bits)** , téléchargeable suivant le lien [Microsoft ODBC Driver 11 Preview for SQL Server – SUSE Linux](https://go.microsoft.com/fwlink/?LinkId=264916) :  
    -   `glibc`  
    -   `libstdc++46`  
    -   `libgcc46`  
    -   `libuuid1`  
    -   `krb5`  
    -   `libopenssl0_9_8`  
  
## <a name="see-also"></a>Voir aussi
[Installation du Gestionnaire de pilotes](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)

[Problèmes connus dans cette version du pilote](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)  

[Notes de publication](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)  
