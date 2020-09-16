---
description: Méthode isNullable (SQLServerParameterMetaData)
title: Méthode isNullable (SQLServerParameterMetaData) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e8b69729195546246a624773976487670c6441c0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433531"
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
  
 **int** indiquant l’index du paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 **int** indiquant la possibilité de valeur Null du paramètre désigné, qui peut être l’une des valeurs suivantes :  
  
 ParameterMetaData.parameterNoNulls  
  
 ParameterMetaData.parameterNullable  
  
 ParameterMetaData.parameterNullabilityUnknown  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode isNullable est spécifiée par la méthode isNullable de l’interface java.sql.ParameterMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerParameterMetaData, méthodes](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData, membres](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [Classe SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
