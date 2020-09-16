---
description: Méthode registerOutParameter (java.lang.String, int)
title: Méthode registerOutParameter pour type | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter (java.lang.String, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5d00242c-4d9c-42cc-86bb-b76f5ef876b8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a3d7c0a511f630683682c427fe73d0808e418375
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432781"
---
# <a name="registeroutparameter-method-javalangstring-int"></a>Méthode registerOutParameter (java.lang.String, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Inscrit le paramètre OUT avec le nom spécifié en fonction du type JDBC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void registerOutParameter(java.lang.String s,  
                                 int n)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *s*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
 *n*  
  
 Code de type JDBC comme défini dans java.sql.Types.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode registerOutParameter est spécifiée par la méthode registerOutParameter de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [registerOutParameter, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
