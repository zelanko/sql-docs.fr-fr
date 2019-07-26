---
title: Méthode updateBytes (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3050c836-fbb3-4475-99e5-05637a48a932
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0d395e016ad6d84edb17fc826f39036be95b6815
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67996856"
---
# <a name="updatebytes-method-sqlserverresultset"></a>Méthode updateBytes (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec un tableau de valeurs **byte**.  
  
## <a name="overload-list"></a>Liste de surcharge  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|[updateBytes (int, byte&#91;&#93;)](../../../connect/jdbc/reference/updatebytes-method-int-byte.md)|Met à jour la colonne désignée avec un tableau de valeurs **byte** en fonction de l’index de colonne.|  
|[updateBytes (java.lang.String, byte&#91;&#93;)](../../../connect/jdbc/reference/updatebytes-method-java-lang-string-byte.md)|Met à jour la colonne désignée avec un tableau de valeurs **byte** en fonction du nom de la colonne.|  
  
## <a name="remarks"></a>Notes  
 Dans la version précédente de [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], vous pouviez utiliser SQLServerResultSet.updateBytes pour convertir des valeurs entre des tableaux d’octets et le type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **date**, **time**, **datetime2** ou **datetimeoffset**. À présent, l'utilisation de cette méthode avec ces types de données lève une exception indiquant que la conversion n'est pas prise en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
