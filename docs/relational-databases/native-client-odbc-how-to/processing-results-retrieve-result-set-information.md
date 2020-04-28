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
ms.openlocfilehash: f1c65841db0fdfd386891cfbd03bdee483ce25f6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300369"
---
# <a name="processing-results---retrieve-result-set-information"></a>Traitement des résultats - Récupérer les informations du jeu de résultats
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-get-information-about-a-result-set"></a>Pour obtenir des informations sur un jeu de résultats  
  
1.  Appelez [SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md) pour obtenir le nombre de colonnes dans le jeu de résultats.  
  
2.  Pour chaque colonne de l'ensemble de résultats :  
  
    -   Appelez [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) pour obtenir des informations sur la colonne de résultats.  
  
     ou  
  
    -   Appelez [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) pour obtenir des informations de descripteur spécifiques sur la colonne de résultats.  
  
## <a name="see-also"></a>Voir aussi  
[Traiter les résultats &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/processing-results-process-results.md)

[Détermination des caractéristiques d’un jeu de résultats &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
