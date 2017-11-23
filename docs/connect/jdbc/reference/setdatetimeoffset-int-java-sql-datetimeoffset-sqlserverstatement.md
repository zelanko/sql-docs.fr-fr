---
title: setDateTimeOffset (int, java.sql.DateTimeOffset) | Documents Microsoft
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
ms.assetid: e8b6e380-6b53-489b-be73-73fcb5258269
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b9b18af7823f8d02f80ba636fe57b5d6cd807770
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
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
  
 *dateTimeOffset*  
  
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
 [getDateTimeOffset &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [Membres de SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
