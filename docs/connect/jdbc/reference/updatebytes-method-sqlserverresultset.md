---
title: "Méthode updateBytes (SQLServerResultSet) | Documents Microsoft"
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
- SQLServerResultSet.updateBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3050c836-fbb3-4475-99e5-05637a48a932
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e20e126945f11a2cba5d4b1171dc762f2a2efbac
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="updatebytes-method-sqlserverresultset"></a>Méthode updateBytes (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour de la colonne désignée avec un tableau de **octets** valeurs.  
  
## <a name="overload-list"></a>Liste de surcharge  
  
|Nom| Description|  
|----------|-----------------|  
|[updateBytes (int, byte &#91; &#93;)](../../../connect/jdbc/reference/updatebytes-method-int-byte.md)|Met à jour de la colonne désignée avec un tableau de **octets** valeurs en fonction de l’index de colonne.|  
|[updateBytes (java.lang.String, byte &#91; &#93;)](../../../connect/jdbc/reference/updatebytes-method-java-lang-string-byte.md)|Met à jour de la colonne désignée avec un tableau de **octets** valeurs en fonction du nom de colonne.|  
  
## <a name="remarks"></a>Notes  
 Dans une version antérieure de [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], vous pouviez utiliser SQLServerResultSet.updateBytes pour convertir des valeurs entre des tableaux d’octets et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] type de données **date**, **temps**, ** datetime2**, ou **datetimeoffset**. À présent, l'utilisation de cette méthode avec ces types de données lève une exception indiquant que la conversion n'est pas prise en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
