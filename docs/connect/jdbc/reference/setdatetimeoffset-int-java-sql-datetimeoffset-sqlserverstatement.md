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
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
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
  
|Type SQL|Insérer|  
|--------------|------------|  
|DATETIME|Peut insérer uniquement : « AAAA-MM-JJ hh:mm:ss[.nnn] »|  
|smalldatetime|Peut insérer uniquement : « AAAA-MM-JJ hh:mm:ss »|  
|Temps|Peut insérer uniquement : « hh:mm:ss[.nnnnnnn] »|  
|Date|Peut insérer uniquement : « AAAA-MM-JJ »|  
|DateTime2|Peut insérer uniquement : « AAAA-MM-JJ hh:mm:ss[.nnnnnnn] »|  
  
## <a name="see-also"></a>Voir aussi  
 [getDateTimeOffset &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
