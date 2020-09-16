---
description: isSparseColumnSet, méthode (SQLServerResultSetMetaData)
title: Méthode isSparseColumnSet (SQLServerResultSetMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ac363670-78ae-49f1-aeda-4fba3329a258
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 86fbbcdc34259e6b3d783d34ca77af57bcfba89f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433371"
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
  
## <a name="return-value"></a>Valeur de retour  
 **true** si la colonne du jeu de résultats est un jeu de colonnes éparses ; **false** sinon.  
  
## <a name="remarks"></a>Notes  
 Cette méthode ne récupère pas d'informations de la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSetMetaData, méthodes](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData, membres](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
