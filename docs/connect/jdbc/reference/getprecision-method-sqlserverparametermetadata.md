---
title: "Méthode getPrecision (SQLServerParameterMetaData) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerParameterMetaData.getPrecision
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8bd79484-bab6-423b-978f-d7ec7132ebeb
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8c80beecc510fb5f2d4190839e8bc4ca1c95602c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getprecision-method-sqlserverparametermetadata"></a>Méthode getPrecision (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nombre de décimales du paramètre désigné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getPrecision(int param)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Param*  
  
 Un **int** qui indique l’index de paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui indique la précision du paramètre désigné.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getPrecision est spécifiée par la méthode getPrecision dans l’interface java.sql.ParameterMetaData.  
  
 Pour les types de nombres, cette méthode obtient le nombre de décimales. Pour les types de caractères, elle obtient la longueur maximale en caractères. Pour les types binaires, elle obtient la longueur maximale en octets. Lorsque le nombre de chiffres n'est pas connu, cette méthode retourne la valeur « 0 ».  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [Membres de SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData, classe](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  

