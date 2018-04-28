---
title: Méthode getPrecision (SQLServerParameterMetaData) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
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
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d61849b2a73f55bb06472aed14590895b4e0eeec
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="getprecision-method-sqlserverparametermetadata"></a>Méthode getPrecision (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nombre de décimales du paramètre désigné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getPrecision(int param)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *param*  
  
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
  
  
