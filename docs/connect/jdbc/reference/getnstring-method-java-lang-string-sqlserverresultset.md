---
title: getNString, méthode (java.lang.String) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 546d77e2-723a-42ac-ba3f-fabf2395d376
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e0a76052ccf05927ebd598e2baa37fbf0229bf54
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67981395"
---
# <a name="getnstring-method-javalangstring-sqlserverresultset"></a>Méthode getNString (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur de la colonne désignée dans la ligne actuelle de l’objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) sous forme d’objet java.lang.String.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getNString(java.lang.String columnLabel)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnLabel*  
  
 String contenant l’étiquette de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet String.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getNString est spécifiée par la méthode getNString de l’interface java.sql.SQLServerResultSet.  
  
 Cette méthode peut être utilisée pour récupérer la valeur d’une colonne **nvarchar**, **nchar**, **nvarchar (max)** , **ntext**ou **XML** dans la ligne actuelle de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) . Si vous essayez d'utiliser cette méthode pour récupérer les valeurs d'autres types de données, une exception est levée.  
  
## <a name="see-also"></a>Voir aussi  
 [getNString, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)  
  
  
