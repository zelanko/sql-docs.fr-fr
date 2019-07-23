---
title: Méthode setFetchDirection (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 18176517-2fb3-4266-924d-0f01253083d2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 995f3f0f63728d397cf51013bd5429943e9cac0c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974398"
---
# <a name="setfetchdirection-method-sqlserverstatement"></a>Méthode setFetchDirection (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Donne à [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] une indication concernant la direction de traitement des lignes du jeu de résultats.  
  
> [!NOTE]  
>  Le pilote JDBC ignore actuellement le conseil fournie par cette méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setFetchDirection(int nDir)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nDir*  
  
 **Entier** qui indique la direction de traitement des lignes, qui peut prendre l’une des valeurs suivantes:  
  
 FETCH_FORWARD  
  
 FETCH_REVERSE  
  
 FETCH_UNKNOWN  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setFetchDirection est spécifiée par la méthode setFetchDirection dans l’interface java. Sql. Statement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
