---
description: Méthode setSQLXML (SQLServerCallableStatement)
title: Méthode setSQLXML (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: de095cb3-1111-4154-8996-3c2e529e3000
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e41da20bd3e3f046f5ece7e2c190a3a81c70e861
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458301"
---
# <a name="setsqlxml-method-sqlservercallablestatement"></a>Méthode setSQLXML (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon l’objet SQLXML spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setSQLXML(java.lang.String parameterName,  
                            java.sql.SQLXML xmlObject)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 **Chaîne** indiquant le nom du paramètre.  
  
 *xmlObject*  
  
 Objet SQLXML contenant la valeur du paramètre.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setSQLXML est spécifiée par la méthode setSQLXML de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
