---
title: Méthode getParameterType (SQLServerParameterMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.getParameterType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 638aca05-63e4-4d73-a9c8-e0442f775720
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bd9252827e7c7bec70636937bc89dd5390e68519
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67980956"
---
# <a name="getparametertype-method-sqlserverparametermetadata"></a>Méthode getParameterType (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le type SQL du paramètre désigné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getParameterType(int param)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *param*  
  
 **Entier** qui indique un index de paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 **Entier** qui indique le code de type JDBC tel que défini dans Java. Sql. types.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getParameterType est spécifiée par la méthode getParameterType dans l’interface java. Sql. ParameterMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerParameterMetaData, méthodes](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData, membres](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData, classe](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
