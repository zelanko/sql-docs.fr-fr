---
title: Méthode isDefinitelyWritable (SQLServerResultSetMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSetMetaData.isDefinitelyWritable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7650e89a-dc8e-43ca-8eb2-f962f1a4b4ae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 28b64f5cbc9de40057a9015c19eef96c21f93260
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923593"
---
# <a name="isdefinitelywritable-method-sqlserverresultsetmetadata"></a>Méthode isDefinitelyWritable (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique si une écriture dans la colonne désignée réussit toujours.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isDefinitelyWritable(int column)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *column*  
  
 **int** indiquant l’index de la colonne.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si l’écriture de la colonne réussit définitivement. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode isDefinitelyWritable est spécifiée par la méthode isDefinitelyWritable de l'interface java.sql.ResultSetMetaData.  
  
> [!NOTE]  
>  Lors de l’utilisation du [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] avec une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], cette méthode retourne toujours la valeur False.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSetMetaData, méthodes](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData, membres](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
