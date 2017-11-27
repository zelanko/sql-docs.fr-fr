---
title: SQLRowCount | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLRowCount function
ms.assetid: 967ed3d4-3d31-4485-ac92-027076ebc829
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 46520586098ce96899dd49df4ada60541f0c6bb0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sqlrowcount"></a>SQLRowCount
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Lorsque des tableaux de valeurs de paramètre sont liés pour l'exécution d'une instruction, **SQLRowCount** retourne SQL_ERROR si une ligne de valeurs de paramètre génère une condition d'erreur dans l'exécution d'une instruction. Aucune valeur n'est retournée via l'argument *RowCountPtr* de la fonction.  
  
 L'application peut tirer parti de l'attribut d'instruction SQL_ATTR_PARAMS_PROCESSED_PTR pour capturer le nombre de paramètres traités avant l'erreur.  
  
 En outre, l'application peut utiliser un tableau de valeurs d'état, lié via l'utilisation de l'attribut d'instruction SQL_ATTR_PARAM_STATUS_PTR, pour capturer les décalages des lignes de paramètres incriminées du tableau. L'application peut parcourir le tableau de valeurs d'état pour déterminer le nombre réel de lignes traitées.  
  
 Lorsqu’un [!INCLUDE[tsql](../../includes/tsql-md.md)] une instruction INSERT, UPDATE, DELETE ou MERGE avec une clause OUTPUT est exécutée, SQLRowCount ne retourne pas le nombre de lignes affectées tant que toutes les lignes du jeu de résultats généré par la clause OUTPUT ont été consommées. Pour consommer ces lignes, vous devez appeler SQLFetch ou SQLFetchScroll. SQLResultCols retourne -1 jusqu'à ce que toutes les lignes de résultat ont été consommés. SQLFetch ou SQLFetchScroll retourne SQL_NO_DATA, l’application doit appeler SQLRowCount pour déterminer le nombre de lignes affectées avant d’appeler SQLMoreResults pour atteindre le résultat suivant.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLRowCount (fonction)](http://go.microsoft.com/fwlink/?LinkId=59367)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
