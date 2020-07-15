---
title: Vérifier la version des pilotes ODBC de SQL Server (Windows) | Microsoft Docs
description: Découvrez comment utiliser l’Administrateur de la source de données ODBC Windows pour vérifier la version des pilotes ODBC installés sur votre ordinateur.
ms.custom: ''
ms.date: 11/07/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- driver version number [ODBC]
- ODBC drivers, version number
ms.assetid: 43451080-a562-4231-b1d4-1ba35ca0ea79
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 7cfebbf9266bfa97bd17415cd892f20f04869f1d
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86001209"
---
# <a name="check-the-odbc-sql-server-driver-version-windows"></a>Vérifier la version des pilotes ODBC de SQL Server (Windows)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Votre ordinateur peut contenir divers pilotes ODBC, provenant de [!INCLUDE[msCoName](../../includes/msconame-md.md)] et d'autres sociétés. Cette rubrique explique comment utiliser l’ **Administrateur de la source de données ODBC** Windows pour vérifier la version des pilotes ODBC installés.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-check-the-odbc-sql-server-driver-version-32-bit-odbc"></a>Pour vérifier la version des pilotes ODBC de SQL Server (ODBC 32 bits)  
  
-   Dans l’ **Administrateur de la source de données ODBC**, cliquez sur l’onglet **Pilotes** .  
  
     Les informations relatives à l’entrée Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] apparaissent dans la colonne **Version** .  


> [!NOTE]  
>  Pour les connexions à l’authentification Azure Active Directory pour SQL Database, installez le pilote le plus récent, tel que le [Pilote ODBC 13.1 pour SQL Server](https://www.microsoft.com/download/details.aspx?id=53339).   

  
## <a name="see-also"></a>Voir aussi  
 [Ouvrir l'Administrateur de la source de données ODBC](../../database-engine/configure-windows/open-the-odbc-data-source-administrator.md)  
  
  
