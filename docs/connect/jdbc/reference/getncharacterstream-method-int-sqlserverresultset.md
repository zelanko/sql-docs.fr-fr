---
title: getNCharacterStream, méthode (int) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f1cfa4e4-3e1f-4504-b0de-cc626d653661
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 23cd90d0180486f364d4b1018212d5ef4d57de94
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66784694"
---
# <a name="getncharacterstream-method-int-sqlserverresultset"></a>Méthode getNCharacterStream (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur d’une colonne désignée dans la ligne actuelle de l’objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) sous forme d’objet Reader.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.io.Reader getNCharacterStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnIndex*  
  
 Un **int** qui indique l’index de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet de lecteur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getNCharacterStream est spécifiée par la méthode getNCharacterStream dans l’interface java.sql.ResultSet.  
  
 Cette méthode peut être utilisée pour récupérer la valeur d’un **nvarchar**, **nchar**, **nvarchar (max)** , **ntext**, ou **xml** colonne dans la ligne actuelle de ce [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet. Si vous essayez d'utiliser cette méthode pour récupérer les valeurs d'autres types de données, une exception est levée.  
  
## <a name="see-also"></a>Voir aussi  
 [getNCharacterStream, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)  
  
  
