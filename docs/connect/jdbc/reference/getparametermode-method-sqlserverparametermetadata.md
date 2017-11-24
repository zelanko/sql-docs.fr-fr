---
title: "Méthode getParameterMode (SQLServerParameterMetaData) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerParameterMetaData.getParameterMode
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: d93c9b70-18c2-44bb-a6de-70a7e940d806
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 089a9996eb22fd354b394a61624a00f5b3a489d3
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getparametermode-method-sqlserverparametermetadata"></a>Méthode getParameterMode (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le mode du paramètre désigné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getParameterMode(int param)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Param*  
  
 Un **int** qui indique l’index de paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui indique le mode du paramètre désigné, qui peut être une des valeurs suivantes :  
  
 ParameterMetaData.parameterModeIn  
  
 ParameterMetaData.parameterModeInOut  
  
 ParameterMetaData.parameterModeOut  
  
 ParameterMetaData.parameterModeUnknown  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getParameterMode est spécifiée par la méthode getParameterMode dans l’interface java.sql.ParameterMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [Membres de SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData, classe](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
