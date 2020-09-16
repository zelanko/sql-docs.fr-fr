---
description: Méthode getNString (int) (SQLServerResultSet)
title: Méthode getNString (int) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c8cc4636-01e9-4dc8-a40c-728337ca08f5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 91e6dd1e44620d4e07a8376f78dd93b834dcc609
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435241"
---
# <a name="getnstring-method-int-sqlserverresultset"></a>Méthode getNString (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur de la colonne désignée dans la ligne actuelle de l’objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) sous forme d’objet String.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getNString(int columnIndex)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnIndex*  
  
 **int** indiquant l’index de la colonne.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet String.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getNString est spécifiée par la méthode getNString de l’interface java.sql.SQLServerResultSet.  
  
 Cette méthode peut être utilisée pour récupérer la valeur d’une colonne **nvarchar**, **nchar**, **nvarchar(max)**, **ntext** ou **xml** dans la ligne actuelle de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md). Si vous essayez d'utiliser cette méthode pour récupérer les valeurs d'autres types de données, une exception est levée.  
  
## <a name="see-also"></a>Voir aussi  
 [getNString, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md)   
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)  
  
  
