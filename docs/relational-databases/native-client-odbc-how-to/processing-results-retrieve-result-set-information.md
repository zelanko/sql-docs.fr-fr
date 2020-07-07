---
title: Récupérer les informations du jeu de résultats (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f00fe6310c339d7ec24736c5f659d3b7b7d84ce8
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006570"
---
# <a name="processing-results---retrieve-result-set-information"></a>Traitement des résultats - Récupérer les informations du jeu de résultats
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

    
### <a name="to-get-information-about-a-result-set"></a>Pour obtenir des informations sur un jeu de résultats  
  
1.  Appelez [SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md) pour obtenir le nombre de colonnes dans le jeu de résultats.  
  
2.  Pour chaque colonne de l'ensemble de résultats :  
  
    -   Appelez [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) pour obtenir des informations sur la colonne de résultats.  
  
     ou  
  
    -   Appelez [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) pour obtenir des informations de descripteur spécifiques sur la colonne de résultats.  
  
## <a name="see-also"></a>Voir aussi  
[Traiter les résultats &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/processing-results-process-results.md)

[Détermination des caractéristiques d’un jeu de résultats &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
