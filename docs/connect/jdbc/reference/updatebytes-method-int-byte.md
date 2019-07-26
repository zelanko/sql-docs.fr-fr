---
title: Méthode updateBytes (int, Byte) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateBytes (int, byte[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 625f48ba-53d0-45a6-8fcb-643f1e0cbe8a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 60de0b0fd051ed67a2f2804443e419d454c2cb5c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67996908"
---
# <a name="updatebytes-method-int-byte"></a>updateBytes, méthode (int, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec un tableau de valeurs **byte** en fonction de l’index de colonne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateBytes(int index,  
                        byte[] x)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 **Entier** qui indique l’index de colonne.  
  
 *x*  
  
 Tableau de valeurs d' **octets** .  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateBytes est spécifiée par la méthode updateBytes de l’interface java.sql.ResultSet.  
  
 Dans la version précédente de [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], vous pouviez utiliser SQLServerResultSet.updateBytes pour convertir des valeurs entre des tableaux d’octets et le type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **date**, **time**, **datetime2** ou **datetimeoffset**. À présent, l'utilisation de cette méthode avec ces types de données lève une exception indiquant que la conversion n'est pas prise en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [updateBytes, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebytes-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
