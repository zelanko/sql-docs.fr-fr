---
title: Configuration requise (ODBC Driver for SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/18/2020
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2459a9f57f3591db1107994d0b18770690f22724
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921177"
---
# <a name="system-requirements"></a>Configuration requise

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Cette rubrique répertorie la configuration requise pour utiliser [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux et macOS.

## <a name="sql-version-compatibility"></a>Compatibilité des versions de SQL

La compatibilité des versions SQL avec les pilotes Linux et macOS est identique à celle des [pilotes Windows](../windows/system-requirements-installation-and-driver-files.md#sql-version-compatibility).

## <a name="operating-system-support"></a>Prise en charge du système d’exploitation

Les versions 17, 13.1 et 13 des pilotes Linux et macOS sont prises en charge sur les versions 64 bits des systèmes d’exploitation suivants :

|Systèmes d’exploitation pris en charge     |17.5|17.4|17.3|17.2|17.1|17.0|13.1|13|
|-------------------------------|----|----|----|----|----|----|----|--|
|Apple OS X 10.11 (El Capitan)  | |O|O|O|O|O|O|O|
|Apple macOS 10.12 (Sierra)     | |O|O|O|O|O|O|O|
|Apple macOS 10.13 (High Sierra)|O|O|O|O|O|O|O|O|
|Apple macOS 10.14 (Mojave)     |O|O|O| | | | | |
|Apple macOS 10.15 (Catalina)   |O| | | | | | | |
|Alpine Linux 3.11              |O| | | | | | | |
|Debian Linux 8                 | |O|O|O|O|O|O|O|
|Debian Linux 9                 |O|O|O|O|O|O|O|O|
|Debian Linux 10                |O|O| | | | | | |
|Oracle Linux 8                 |O| | | | | | | |
|Red Hat Enterprise Linux 6      |O|O|O|O|O|O|O|O|
|Red Hat Enterprise Linux 7      |O|O|O|O|O|O|O|O|
|RedHat Enterprise Linux 8      |O|O| | | | | | |
|SUSE Linux Enterprise Server 11<sup>1</sup>|O|O|O|O|O|O|O|O|
|SUSE Linux Enterprise Server 12|O|O|O|O|O|O|O|O|
|SUSE Linux Enterprise Server 15|O|O|O| | | | | |
|Ubuntu Linux 14.04             | |O|O|O|O|O|O|O|
|Ubuntu Linux 16.04             |O|O|O|O|O|O|O|O|
|Ubuntu Linux 18.04             |O|O|O|O| | | | |
|Ubuntu Linux 19.10             |O| | | | | | | |

<sup>1</sup> ODBC Driver 17 prend uniquement en charge SUSE Linux Enterprise Server 11 SP4.

Les packages d’installation de [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13, 13.1 et 17 pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux et macOS résolvent automatiquement les dépendances du pilote quand ils sont installés à l’aide du système de gestion des packages de votre distribution, comme décrit dans [Installer le pilote ODBC (Linux)](installing-the-microsoft-odbc-driver-for-sql-server.md) et [Installer le pilote ODBC (macOS)](install-microsoft-odbc-driver-sql-server-macos.md).

## <a name="microsoft-odbc-driver-11-for-sql-server"></a>Pilote Microsoft ODBC 11 pour SQL Server  
  
* Gestionnaire de pilotes UnixODBC 2.3.0 64 bits, conçu pour SQLLEN/SQLULEN 64 bits. Les versions ultérieures du Gestionnaire de pilotes UnixODBC 64 bits ne sont pas prises en charge avec le pilote ODBC sur Linux. Consultez la rubrique [Installing the Driver Manager](../../../connect/odbc/linux-mac/installing-the-driver-manager.md) (éventuellement en anglais) pour plus d'informations.  
  
* Les packages suivants sont nécessaires pour le pilote ODBC pour **Red Hat Enterprise Linux 5 (64 bits)** , téléchargeable suivant le lien [Microsoft ODBC Driver 11 for SQL Server – Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321) :  
  * `glibc`  
  * `libgcc`  
  * `libstdc++`  
  * `e2fsprogs-libs`  
  * `krb5-libs`  
  * `openssl`  
  
* Les packages suivants sont nécessaires pour le pilote ODBC pour **Red Hat Enterprise Linux 6 (64 bits)** , téléchargeable suivant le lien [Microsoft ODBC Driver 11 for SQL Server – Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321) :  
  * `glibc`  
  * `libgcc`  
  * `libstdc++`  
  * `libuuid`  
  * `krb5-libs`  
  * `openssl`  
  
* Les packages suivants sont nécessaires pour le pilote ODBC pour **SUSE Linux Enterprise 11 Service Pack 2 (64 bits)** , téléchargeable suivant le lien [Microsoft ODBC Driver 11 Preview for SQL Server – SUSE Linux](https://go.microsoft.com/fwlink/?LinkId=264916) :  
  * `glibc`  
  * `libstdc++46`  
  * `libgcc46`  
  * `libuuid1`  
  * `krb5`  
  * `libopenssl0_9_8`  
  
## <a name="see-also"></a>Voir aussi

[Installation du Gestionnaire de pilotes](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)  
[Problèmes connus dans cette version du pilote](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)  
[Notes de publication](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)  
