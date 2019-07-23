---
title: Méthode setNString (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6494300b-7fc0-4076-8311-22d35a96cdc6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5891b971bcf6129ec3b5fcec4e9ae8f0301283b9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67973584"
---
# <a name="setnstring-method-sqlservercallablestatement"></a>Méthode setNString (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon l’objet String spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setNString(java.lang.String parameterName, java.lang.String value)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 **Chaîne** qui indique le nom du paramètre.  
  
 *value*  
  
 Objet String.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode doit être utilisée pour les types de données **nchar**, **nvarchar**, **ntext**et **XML** .  
  
 Cette méthode setNString est spécifiée par la méthode setNString de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
