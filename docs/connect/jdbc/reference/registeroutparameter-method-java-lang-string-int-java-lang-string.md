---
description: Méthode registerOutParameter (java.lang.String, int, java.lang.String)
title: Méthode registerOutParameter pour type et nom | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f962c912-2475-4e1f-a384-579be2d17f37
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0fab9ba4e979780fedfb676fd779f8ed83da7566
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432801"
---
# <a name="registeroutparameter-method-javalangstring-int-javalangstring"></a>Méthode registerOutParameter (java.lang.String, int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Inscrit le paramètre OUT avec le nom spécifié en fonction du type JDBC et du nom du type donnés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void registerOutParameter(java.lang.String s,  
                                 int n,  
                                 java.lang.String s1)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *s*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
 *n*  
  
 Code de type JDBC comme défini dans java.sql.Types.  
  
 *s1*  
  
 **String** contenant le nom de type SQL complet.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode registerOutParameter est spécifiée par la méthode registerOutParameter de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [registerOutParameter, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
