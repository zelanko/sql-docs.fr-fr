---
title: SQLNativeSql | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLNativeSql function
ms.assetid: 2d999fec-9e22-4514-ad5f-22a64b82f95b
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dd39e72cb9de6debc4af80ea574de07c541cf328
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86000314"
---
# <a name="sqlnativesql"></a>SQLNativeSql
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Le pilote ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client répond aux demandes **SQLNativeSql** sans visiter le serveur. La fonction teste efficacement la syntaxe d'instructions SQL. La vérification de la syntaxe ne détermine pas si des identificateurs ou les résultats d'expressions dans les instructions SQL sont valides, et l'exécution du code SQL natif [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourné par **SQLNativeSql** peut échouer.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLNativeSql fonction)](https://go.microsoft.com/fwlink/?LinkID=59358)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
