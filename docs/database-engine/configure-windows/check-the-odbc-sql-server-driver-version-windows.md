---
title: "Vérifier la version des pilotes ODBC de SQL Server (Windows) | Microsoft Docs"
ms.custom: 
ms.date: 11/07/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- driver version number [ODBC]
- ODBC drivers, version number
ms.assetid: 43451080-a562-4231-b1d4-1ba35ca0ea79
caps.latest.revision: "23"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 23b130cee2c61ff4677eedfd8070574a9df52061
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="check-the-odbc-sql-server-driver-version-windows"></a>Vérifier la version des pilotes ODBC de SQL Server (Windows)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Votre ordinateur peut contenir divers pilotes ODBC, provenant de [!INCLUDE[msCoName](../../includes/msconame-md.md)] et d'autres sociétés. Cette rubrique explique comment utiliser l’ **Administrateur de la source de données ODBC** Windows pour vérifier la version des pilotes ODBC installés.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-check-the-odbc-sql-server-driver-version-32-bit-odbc"></a>Pour vérifier la version des pilotes ODBC de SQL Server (ODBC 32 bits)  
  
-   Dans l’ **Administrateur de la source de données ODBC**, cliquez sur l’onglet **Pilotes** .  
  
     Les informations relatives à l’entrée Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] apparaissent dans la colonne **Version** .  


> [!NOTE]  
>  Pour les connexions à l’authentification Azure Active Directory pour SQL Database, installez le pilote le plus récent, tel que le [Pilote ODBC 13.1 pour SQL Server](https://www.microsoft.com/download/details.aspx?id=53339).   

  
## <a name="see-also"></a> Voir aussi  
 [Ouvrir l’Administrateur de la source de données ODBC](../../database-engine/configure-windows/open-the-odbc-data-source-administrator.md)  
  
  
