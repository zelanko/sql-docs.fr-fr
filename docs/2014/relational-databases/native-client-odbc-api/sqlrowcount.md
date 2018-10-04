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
ms.openlocfilehash: 9858619250b5f71e973e4af8eb92868f094e2193
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48165029"
---
# <a name="sqlrowcount"></a>SQLRowCount
  Lorsque des tableaux de valeurs de paramètre sont liés pour l’exécution des instructions, `SQLRowCount` retourne SQL_ERROR si une ligne de valeurs de paramètre génère une condition d’erreur dans l’exécution des instructions. Aucune valeur n'est retournée via l'argument *RowCountPtr* de la fonction.  
  
 L'application peut tirer parti de l'attribut d'instruction SQL_ATTR_PARAMS_PROCESSED_PTR pour capturer le nombre de paramètres traités avant l'erreur.  
  
 En outre, l'application peut utiliser un tableau de valeurs d'état, lié via l'utilisation de l'attribut d'instruction SQL_ATTR_PARAM_STATUS_PTR, pour capturer les décalages des lignes de paramètres incriminées du tableau. L'application peut parcourir le tableau de valeurs d'état pour déterminer le nombre réel de lignes traitées.  
  
 Quand un [!INCLUDE[tsql](../../includes/tsql-md.md)] une instruction INSERT, UPDATE, DELETE ou MERGE avec une clause OUTPUT est exécutée, SQLRowCount ne retourne pas le nombre de lignes affectées tant que toutes les lignes du jeu de résultats généré par la clause OUTPUT ont été consommées. Pour consommer ces lignes, vous devez appeler SQLFetch ou SQLFetchScroll. SQLResultCols retourne -1 tant que toutes les lignes de résultat ont été consommées. SQLFetch ou SQLFetchScroll retourne SQL_NO_DATA, l’application doit appeler SQLRowCount pour déterminer le nombre de lignes affectées avant l’appel de SQLMoreResults pour atteindre le résultat suivant.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLRowCount, fonction](http://go.microsoft.com/fwlink/?LinkId=59367)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
