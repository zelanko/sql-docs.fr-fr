---
title: Méthode supportsConvert (int, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsConvert (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 54741cfd-32ac-46c5-8b09-fd60fd8833d7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ae22b0f4149536977dd3ee7c9cc21758e7dcc980
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67969603"
---
# <a name="supportsconvert-method-int-int"></a>Méthode supportsConvert (int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si cette base de données prend en charge la fonction CONVERT pour deux types SQL donnés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsConvert(int fromType,  
                               int toType)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *fromType*  
  
 Type JDBC depuis lequel effectuer la conversion.  
  
 *toType*  
  
 Type JDBC vers lequel effectuer la conversion.  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si pris en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode supportsConvert est spécifiée par la méthode supportsConvert dans l’interface java. Sql. DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [supportsConvert, méthode &#40;SQLServerDatabaseMetaData&#41;](../../../connect/jdbc/reference/supportsconvert-method-sqlserverdatabasemetadata.md)   
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
