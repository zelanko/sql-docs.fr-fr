---
title: updateSQLXML, méthode (java.lang.String, java.sql.SQLXML) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 60021881-ef83-499b-9977-e20ff23c1312
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0e2772b43c084e1780b8e65cd6425b67d01092f1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67998287"
---
# <a name="updatesqlxml-method-javalangstring-javasqlsqlxml"></a>Méthode updateSQLXML (java.lang.String, java.sql.SQLXML)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec une valeur java.sql.SQLXML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateSQLXML(java.lang.String columnLabel,  
                         java.sql.SQLXML xmlObject)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnLabel*  
  
 **Chaîne** qui indique l’étiquette de colonne.  
  
 *xmlObject*  
  
 Objet SQLXML.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateSQLXML est spécifiée par la méthode updateSQLXML de l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [updateSQLXML, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatesqlxml-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
