---
title: issparsecolumnset, méthode (SQLServerResultSetMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ac363670-78ae-49f1-aeda-4fba3329a258
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6d40bcf6f43f0323131ece954889459018340379
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796326"
---
# <a name="issparsecolumnset-method-sqlserverresultsetmetadata"></a>isSparseColumnSet, méthode (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique si une colonne dans un jeu de résultats est un jeu de colonnes éparses.  
  
## <a name="syntax"></a>Syntaxe  
  
```scr  
public boolean isSparseColumnSet(int column)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *column*  
  
 Index (de base un) de la colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si une colonne dans un jeu de résultats est un jeu de colonnes éparses, sinon **false**.  
  
## <a name="remarks"></a>Notes  
 Cette méthode ne récupère pas d'informations de la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSetMetaData, méthodes](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData, membres](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
