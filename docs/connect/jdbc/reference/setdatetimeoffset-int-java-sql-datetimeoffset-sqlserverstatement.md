---
title: setDateTimeOffset (int, java.sql.DateTimeOffset) | Documents Microsoft
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
ms.assetid: e8b6e380-6b53-489b-be73-73fcb5258269
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e2f2c0e6fcdd299f6d1b0d18615e72dbfc4ff76f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="setdatetimeoffsetint-javasqldatetimeoffset-sqlserverstatement"></a>setDateTimeOffset(int, java.sql.DateTimeOffset) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon la valeur DateTimeOffset donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setDateTimeOffset(int parameterIndex, DateTimeOffset dateTime)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterIndex*  
  
 Index de la colonne à définir.  
  
 *DateTimeOffset*  
  
 Objet DateTimeOffset.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Le format DateTimeOffset est « AAAA-MM-JJ HH-MM-SS[.nnnnnnn] [+][-] HH:MM ». Utilisez le tableau suivant à titre de référence.  
  
|Type SQL|Insert|  
|--------------|------------|  
|datetime|Peut insérer uniquement : « AAAA-MM-JJ hh:mm:ss[.nnn] »|  
|smalldatetime|Peut insérer uniquement : « AAAA-MM-JJ hh:mm:ss »|  
|Time|Peut insérer uniquement : « hh:mm:ss[.nnnnnnn] »|  
|Date|Peut insérer uniquement : « AAAA-MM-JJ »|  
|datetime2|Peut insérer uniquement : « AAAA-MM-JJ hh:mm:ss[.nnnnnnn] »|  
  
## <a name="see-also"></a>Voir aussi  
 [getDateTimeOffset &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [Membres de SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
