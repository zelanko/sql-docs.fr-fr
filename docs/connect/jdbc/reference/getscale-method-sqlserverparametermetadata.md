---
title: "Méthode getScale (SQLServerParameterMetaData) | Documents Microsoft"
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
apiname: SQLServerParameterMetaData.getScale
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 7b8d8d9c-74aa-4e6e-88f1-2fc5c74004ae
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 29223b9a6ecb6ddef96c4c4cbb929e5ca5b02d75
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getscale-method-sqlserverparametermetadata"></a>Méthode getScale (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nombre de chiffres à droite de la virgule décimale pour le paramètre désigné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getScale(int param)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Param*  
  
 Un **int** qui indique l’index de paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Dans **int** qui indique l’échelle du paramètre désigné.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getScale est spécifiée par la méthode getScale dans l’interface java.sql.ParameterMetaData.  
  
 Cette méthode obtient les chiffres de la colonne à droite de la virgule décimale. Pour les types qui n'ont pas de virgule décimale, cette méthode retourne la valeur « 0 ».  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [Membres de SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData, classe](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
