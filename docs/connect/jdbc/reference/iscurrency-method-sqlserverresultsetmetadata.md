---
description: Méthode isCurrency (SQLServerResultSetMetaData)
title: Méthode isCurrency (SQLServerResultSetMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSetMetaData.isCurrency
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7fe25d90-693c-4d3b-9dd2-0f8351c5a9ed
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b4b5c127dab64cfd77599fb9f2dfb50b4605c64e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433661"
---
# <a name="iscurrency-method-sqlserverresultsetmetadata"></a>Méthode isCurrency (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique si la colonne désignée est une valeur de devise.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isCurrency(int column)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *column*  
  
 **int** indiquant l’index de la colonne.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si la colonne est une valeur de devise. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode isCurrency est spécifiée par la méthode isCurrency de l’interface java.sql.ResultSetMetaData.  
  
 Cette méthode retourne **true** seulement avec les types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] money et smallmoney.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSetMetaData, méthodes](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData, membres](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
