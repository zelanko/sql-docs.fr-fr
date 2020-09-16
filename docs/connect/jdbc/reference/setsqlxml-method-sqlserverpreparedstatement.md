---
description: Méthode setSQLXML (SQLServerPreparedStatement)
title: setSQLXML, méthode (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 70bbdde0-75f7-4169-88c5-dbbe2c4bcd03
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 352f46f4cbe8387aaffbf0eb0f13d6046c1db5b8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458291"
---
# <a name="setsqlxml-method-sqlserverpreparedstatement"></a>Méthode setSQLXML (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon l’objet SQLXML spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setSQLXML(int parameterIndex,  
                            java.sql.SQLXML xmlObject)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterIndex*  
  
 **int** indiquant l’index du paramètre.  
  
 *xmlObject*  
  
 Objet SQLXML contenant la valeur du paramètre.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setSQLXML est spécifiée par la méthode setSQLXML de l’interface java.sql.PreparedStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
