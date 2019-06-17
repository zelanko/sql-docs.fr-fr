---
title: registeroutparameter, méthode au type et à l’échelle | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter (java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8bddc557-4526-4843-9804-05dc83c8832d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 36f8300ade9c8b514f4c1efdee9848fafb8b5683
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802066"
---
# <a name="registeroutparameter-method-javalangstring-int-int"></a>Méthode registerOutParameter (java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Inscrit le paramètre OUT avec le nom spécifié en fonction de l'échelle et du type JDBC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void registerOutParameter(java.lang.String s,  
                                 int n,  
                                 int n1)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *s*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
 *sqlType*  
  
 Code de type JDBC comme défini dans java.sql.Types.  
  
 *scale*  
  
 **int** indiquant le nombre de chiffres à placer à droite du séparateur décimal.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode registerOutParameter est spécifiée par la méthode registerOutParameter dans l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [registerOutParameter, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
