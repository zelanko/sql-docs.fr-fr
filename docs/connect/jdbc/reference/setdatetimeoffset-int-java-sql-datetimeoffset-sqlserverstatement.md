---
title: setDateTimeOffset(int, java.sql.DateTimeOffset) | Microsoft Docs
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
ms.openlocfilehash: 166c9ddbd4b5c11b3c032a5a4ecf43c95f183473
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974532"
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
  
## <a name="see-also"></a>Voir aussi  
 [getDateTimeOffset &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
