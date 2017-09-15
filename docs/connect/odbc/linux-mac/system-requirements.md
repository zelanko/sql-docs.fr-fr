---
title: "Configuration système requise | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- prerequisites
- system requirements
- requirements
ms.assetid: f03b7fdd-0e9d-4e74-958d-e8c87e027348
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 13f3c7b9384ee0d8ff74d4d51e6726c52ecc8098
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="system-requirements"></a>Configuration système requise
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Cette rubrique répertorie la configuration requise pour utiliser le [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sur Linux et macOS.

## <a name="microsoft-odbc-driver-13-and-131-for-sql-server"></a>Microsoft ODBC Driver 13 et 13.1 for SQL Server

Les pilotes Linux et macOS sont disponibles uniquement pour les versions 64 bits des systèmes d’exploitation suivants :

- Apple macOS 10.12 (Sierra)
- Apple OS X 10.11 (El Capitan)
- Debian Linux 8
- RedHat Enterprise Linux 6
- RedHat Enterprise Linux 7
- SuSE Linux Enterprise Server 12
- Ubuntu Linux 15.10
- Ubuntu Linux 16.04
- Ubuntu Linux 16.10

L’installation de packages pour le [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 et 13.1 pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sur Linux et macOS résoudre les dépendances du pilote automatiquement lorsqu’il est installé à l’aide du système de gestion de package de votre distribution, comme décrit dans [L’installation du pilote](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

## <a name="microsoft-odbc-driver-11-for-sql-server"></a>Microsoft ODBC Driver 11 for SQL Server  
  
-   Gestionnaire de pilotes UnixODBC 2.3.0 64 bits, conçu pour SQLLEN/SQLULEN 64 bits. Les versions ultérieures du Gestionnaire de pilotes UnixODBC 64 bits ne sont pas prises en charge avec le pilote ODBC sur Linux. Consultez la rubrique [Installing the Driver Manager](../../../connect/odbc/linux-mac/installing-the-driver-manager.md) (éventuellement en anglais) pour plus d'informations.  
  
-   Pilote ODBC pour **Red Hat Enterprise Linux 5 (64 bits)** requiert les packages suivants et peut être téléchargée ici : [Microsoft ODBC Driver 11 for SQL Server - Red Hat Linux](http://go.microsoft.com/fwlink/?LinkId=267321)  
    -   glibc  
    -   libgcc  
    -   libstdc++  
    -   e2fsprogs-libs  
    -   krb5-libs  
    -   openssl  
  
-   Pilote ODBC pour **Red Hat Enterprise Linux 6 (64 bits)** requiert les packages suivants et peut être téléchargée ici : [Microsoft ODBC Driver 11 for SQL Server - Red Hat Linux](http://go.microsoft.com/fwlink/?LinkId=267321)  
    -   glibc  
    -   libgcc  
    -   libstdc++  
    -   libuuid  
    -   krb5-libs  
    -   openssl  
  
-   Pilote ODBC pour **SUSE Linux Enterprise 11 Service Pack 2 (64 bits)** requiert les packages suivants et peut être téléchargée ici : [version préliminaire Microsoft ODBC Driver 11 for SQL Server - SUSE Linux](http://go.microsoft.com/fwlink/?LinkId=264916)  
    -   glibc  
    -   libstdc++46  
    -   libgcc46  
    -   libuuid1  
    -   krb5  
    -   libopenssl0_9_8  
  
## <a name="see-also"></a>Voir aussi
[Installation du Gestionnaire de pilotes](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)

[Problèmes connus dans cette version du pilote](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)  

[Notes de publication](../../../connect/odbc/linux-mac/release-notes.md)  


