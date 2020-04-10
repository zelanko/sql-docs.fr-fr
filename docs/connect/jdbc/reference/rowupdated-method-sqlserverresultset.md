---
title: Méthode rowUpdated (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.rowUpdated
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 29303550-294e-4d43-b892-312b42e21271
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c75169c8ea36ff4008e8a0237ffeaf9f9a9d0c5e
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924505"
---
# <a name="rowupdated-method-sqlserverresultset"></a>rowUpdated, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si la ligne actuelle a été mise à jour.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean rowUpdated()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si la ligne a visiblement été mise à jour par le propriétaire ou par un autre utilisateur, et si des mises à jour sont détectées. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode rowUpdated est spécifiée par la méthode rowUpdated dans l’interface java.sql.ResultSet.  
  
 La valeur qui est retournée varie selon que le jeu de résultats peut ou non détecter les mises à jour.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne détecte les lignes mises à jour d’aucun type de curseur.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
