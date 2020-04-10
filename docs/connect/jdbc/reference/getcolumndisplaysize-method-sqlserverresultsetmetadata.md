---
title: Méthode getColumnDisplaySize (SQLServerResultSetMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSetMetaData.getColumnDisplaySize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 21c25443-bd2b-4b60-9798-4efe2c158952
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 60ed53f51ff9fe828944ecfdbadab647501eac5c
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923415"
---
# <a name="getcolumndisplaysize-method-sqlserverresultsetmetadata"></a>Méthode getColumnDisplaySize (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne la largeur maximale normale, en caractères, pour la colonne désignée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getColumnDisplaySize(int column)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *column*  
  
 **int** indiquant l’index de la colonne.  
  
## <a name="return-value"></a>Valeur de retour  
 **int** indiquant la largeur maximale. Si la largeur n'est pas connue, retourne 0.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getColumnDisplaySize est spécifiée par la méthode getColumnDisplaySize de l’interface java.sql.ResultSetMetaData.  
  
 Le comportement de [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 a changé pour la colonne COLUMN_SIZE. Pour plus d’informations, consultez [SQLServerDatabaseMetaData.getColumns](../../../connect/jdbc/reference/getcolumns-method-sqlserverdatabasemetadata.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSetMetaData, membres](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
