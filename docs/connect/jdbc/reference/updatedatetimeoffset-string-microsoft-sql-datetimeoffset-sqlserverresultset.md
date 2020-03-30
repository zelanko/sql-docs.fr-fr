---
title: updateDateTimeOffset(string) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 952947ce-7c6e-4364-b035-46cb7fe621b2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1543d6412df3370bd25d89a47dc60f915e286fd3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67999047"
---
# <a name="updatedatetimeoffsetstring-microsoftsqldatetimeoffset-sqlserverresultset"></a>updateDateTimeOffset(string, microsoft.sql.DateTimeOffset) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Cette méthode a été ajoutée dans [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0.  
  
 Met à jour la valeur de la colonne spécifiée avec la valeur [DateTimeOffset Class](../../../connect/jdbc/reference/datetimeoffset-class.md), en fonction un nom de colonne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateDateTimeOffset(String columnName, microsoft.sql.DateTimeOffset x)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnName*  
  
 Nom d'une colonne.  
  
 *x*  
  
 Objet [DateTimeOffset Class](../../../connect/jdbc/reference/datetimeoffset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Vous pouvez récupérer un [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) valeur [SQLServerResultSet.getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md).  
  
## <a name="see-also"></a>Voir aussi  
 [updateDateTimeOffset &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatedatetimeoffset-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
