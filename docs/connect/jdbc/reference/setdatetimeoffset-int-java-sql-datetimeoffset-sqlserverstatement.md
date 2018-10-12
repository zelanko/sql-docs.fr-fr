---
title: setDateTimeOffset (int, java.sql.DateTimeOffset) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e8b6e380-6b53-489b-be73-73fcb5258269
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ecbdb1496ed0128d6f8e1c4ff37f26b7009171ca
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810697"
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
|DATETIME|Peut insérer uniquement : « AAAA-MM-JJ hh:mm:ss[.nnn] »|  
|smalldatetime|Peut insérer uniquement : « AAAA-MM-JJ hh:mm:ss »|  
|Time|Peut insérer uniquement : « hh:mm:ss[.nnnnnnn] »|  
|Date|Peut insérer uniquement : « AAAA-MM-JJ »|  
|datetime2|Peut insérer uniquement : « AAAA-MM-JJ hh:mm:ss[.nnnnnnn] »|  
  
## <a name="see-also"></a> Voir aussi  
 [getDateTimeOffset &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
