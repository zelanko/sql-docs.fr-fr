---
title: Méthode rowDeleted (SQLServerResultSet) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d4f761f4780b2fdb5da210db5bfb38d2368d865f
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80903925"
---
# <a name="rowdeleted-method-sqlserverresultset"></a>rowDeleted, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si une ligne a été supprimée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean rowDeleted()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si une ligne a été supprimée et que des suppressions sont détectées. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode rowDeleted est spécifiée par la méthode rowDeleted de l’interface java.sql.ResultSet.  
  
 Une ligne supprimée peut laisser un trou visible dans un jeu de résultats. Cette méthode peut être utilisée pour détecter des trous dans un jeu de résultats. La valeur qui est retournée varie selon que cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) peut ou non détecter les suppressions.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] détecte les lignes supprimées pour tous les types de curseur pouvant être mis à jour, même si la détection est temporaire pour les curseurs de transfert et dynamiques.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
