---
title: "Méthode setEscapeProcessing (SQLServerStatement) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerStatement.setEscapeProcessing
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6ac0682e-e04c-4fdb-893b-92408d42051e
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5e7c53393acca2a1ad95d590ce28fbd7b943b534
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="setescapeprocessing-method-sqlserverstatement"></a>Méthode setEscapeProcessing (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le mode de traitement d'échappement.  
  
> [!NOTE]  
>  Le traitement de d’échappement [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] est toujours activée. Si cette méthode a la valeur False, cela est sans effet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setEscapeProcessing(boolean enable)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Activer*  
  
 **true** pour activer le traitement d’échappement. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setEscapeProcessing est spécifiée par la méthode setEscapeProcessing dans l’interface java.sql.Statement.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

