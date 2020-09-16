---
description: Méthode setString (SQLServerCallableStatement)
title: Méthode setString (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f38b97b5-d4f0-4f74-a33d-740241a85842
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6ab66f76ccc0f6c80c9358e56902c063ca5e1e15
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450711"
---
# <a name="setstring-method-sqlservercallablestatement"></a>Méthode setString (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon la valeur **String** Java donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setString(java.lang.String sCol,  
                      java.lang.String s)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sCol*  
  
 Valeur **String** qui contient le nom du paramètre.  
  
 *s*  
  
 Valeur de **chaîne**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setString est spécifiée par la méthode setString de l’interface java.sql.CallableStatement.  
  
 Les conversions de chaîne en binaire ne sont effectuées que lorsque [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] sait que le type de destination est binaire. Dans les cas où le pilote JDBC ne connaît pas le type sous-jacent, il transmet le littéral **String** et retourne une erreur de serveur si ce dernier ne parvient pas à effectuer la conversion.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
