---
title: isNullable, méthode (SQLServerParameterMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.sNullable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d7e07cff-6fc4-4c9c-8e8f-838c77734bc5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f340a182da1cd232aab70e61c268ba6ec58633db
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67977532"
---
# <a name="isnullable-method-sqlserverparametermetadata"></a>Méthode isNullable (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si les valeurs Null sont autorisées dans le paramètre désigné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int isNullable(int param)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *param*  
  
 **Entier** qui indique un index de paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 **Entier** qui indique la possibilité de valeur null du paramètre désigné, qui peut prendre l’une des valeurs suivantes:  
  
 ParameterMetaData.parameterNoNulls  
  
 ParameterMetaData.parameterNullable  
  
 ParameterMetaData.parameterNullabilityUnknown  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode isNullable est spécifiée par la méthode isNullable dans l’interface java. Sql. ParameterMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerParameterMetaData, méthodes](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData, membres](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData, classe](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
