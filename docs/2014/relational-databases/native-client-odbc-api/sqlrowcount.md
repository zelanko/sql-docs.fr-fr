---
title: SQLRowCount | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLRowCount function
ms.assetid: 967ed3d4-3d31-4485-ac92-027076ebc829
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4ff2a744f68cf6152330179eb8dcab1f33911914
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63046604"
---
# <a name="sqlrowcount"></a>SQLRowCount
  Lorsque des tableaux de valeurs de paramètre sont liés pour l’exécution `SQLRowCount` d’une instruction, retourne SQL_ERROR si une ligne de valeurs de paramètre génère une condition d’erreur dans l’exécution de l’instruction. Aucune valeur n'est retournée via l'argument *RowCountPtr* de la fonction.  
  
 L'application peut tirer parti de l'attribut d'instruction SQL_ATTR_PARAMS_PROCESSED_PTR pour capturer le nombre de paramètres traités avant l'erreur.  
  
 En outre, l'application peut utiliser un tableau de valeurs d'état, lié via l'utilisation de l'attribut d'instruction SQL_ATTR_PARAM_STATUS_PTR, pour capturer les décalages des lignes de paramètres incriminées du tableau. L'application peut parcourir le tableau de valeurs d'état pour déterminer le nombre réel de lignes traitées.  
  
 Lorsqu’une [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction INSERT, Update, Delete ou Merge avec une clause OUTPUT est exécutée, SQLRowCount ne retourne pas le nombre de lignes affectées tant que toutes les lignes du jeu de résultats générés par la clause OUTPUT n’ont pas été consommées. Pour consommer ces lignes, vous appelez SQLFetch ou SQLFetchScroll. SQLResultCols retourne-1 jusqu’à ce que toutes les lignes de résultat soient consommées. Une fois SQLFetch ou SQLFetchScroll retournée SQL_NO_DATA, l’application doit appeler SQLRowCount pour déterminer le nombre de lignes affectées avant d’appeler SQLMoreResults pour passer au résultat suivant.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLRowCount fonction)](https://go.microsoft.com/fwlink/?LinkId=59367)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
