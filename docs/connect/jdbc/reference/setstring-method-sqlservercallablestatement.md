---
title: "Méthode setString (SQLServerCallableStatement) | Documents Microsoft"
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
- SQLServerCallableStatement.setString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f38b97b5-d4f0-4f74-a33d-740241a85842
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2ebcac5fedd89cbec614d7278232c3a5e32e5740
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="setstring-method-sqlservercallablestatement"></a>Méthode setString (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon le Java donné **chaîne** valeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setString(java.lang.String sCol,  
                      java.lang.String s)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sCol*  
  
 A **chaîne** qui contient le nom du paramètre.  
  
 *s*  
  
 A **chaîne** valeur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setString est spécifiée par la méthode setString dans l’interface java.sql.CallableStatement.  
  
 Chaîne pour les conversions binaire sont effectuées uniquement lorsque [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] connaît le type de destination est binaire. Dans les cas où le pilote JDBC ne connaît pas le type sous-jacent, il passe le **chaîne** littéral et retourner une erreur de serveur si le serveur ne peut pas effectuer la conversion.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

