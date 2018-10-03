---
title: rowDeleted, méthode (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.rowDeleted
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9c6db315-e614-4604-b020-41af6a214cc1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b99e2f6f7bc289e123c36e3a528ec937e0f5f7ec
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47605607"
---
# <a name="rowdeleted-method-sqlserverresultset"></a>rowDeleted, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si une ligne a été supprimée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean rowDeleted()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si une ligne a été supprimée et suppressions sont détectées. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode rowDeleted est spécifiée par la méthode rowDeleted dans l’interface java.sql.ResultSet.  
  
 Une ligne supprimée peut laisser un trou visible dans un jeu de résultats. Cette méthode peut être utilisée pour détecter des trous dans un jeu de résultats. La valeur qui est retournée varie selon que cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) peut ou non détecter les suppressions.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] détecte les lignes supprimées pour tous les types de curseur modifiable, bien que la détection est temporaire pour les curseurs avant et dynamiques.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
