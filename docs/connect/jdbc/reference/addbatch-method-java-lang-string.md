---
title: addBatch, méthode (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.addBatch (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 093f6c3b-49a6-4043-9993-bd0482de04dd
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4cbd38eddb3fb5dcdb3f614b53c7d8d6399fa79f
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803757"
---
# <a name="addbatch-method-javalangstring"></a>Méthode addBatch (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ajoute la commande SQL donnée à la liste actuelle de commandes de cet objet [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void addBatch(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sql*  
  
 Un **chaîne** qui contient une instruction SQL.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode addBatch est spécifiée par la méthode addBatch dans l’interface java.sql.Statement.  
  
 L’appel de cette méthode entraîne une exception, car l’instruction SQL de l’objet SQLServerPreparedStatement est spécifiée lors de la création de l’objet.  
  
## <a name="see-also"></a>Voir aussi  
 [addBatch, méthode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
