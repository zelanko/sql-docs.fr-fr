---
title: "Méthode getBytes (int) (SQLServerResultSet) | Documents Microsoft"
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
apiname: SQLServerResultSet.getBytes (int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 1385d7d4-9288-4cbd-8606-4b919e9b07b2
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0a257288c4519d73503c6a53d534d5dad9fe13f4
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getbytes-method-int-sqlserverresultset"></a>Méthode getBytes (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur de l’index de colonne désigné dans la ligne actuelle de ce [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) de l’objet en un **octets** tableau dans le langage de programmation Java.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public byte[] getBytes(int columnIndex)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnIndex*  
  
 Un **int** qui indique l’index de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 Un tableau de **octets** valeurs.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getBytes est spécifiée par la méthode getBytes dans l’interface java.sql.ResultSet.  
  
 Cette méthode prend en charge la récupération de toutes les colonnes sous forme d'une lecture brute d'octets à partir du serveur. Elle retourne un tableau d'octets directement à partir du serveur, au format stocké sur le serveur.  
  
 Dans une version précédente de la [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], vous pouviez utiliser SQLServerResultSet.getBytes pour convertir des valeurs entre des tableaux d’octets et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] type de données **date**, **temps**,  **datetime2**, ou **datetimeoffset**. À présent, l'utilisation de cette méthode avec ces types de données lève une exception indiquant que la conversion n'est pas prise en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getBytes &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getbytes-method-sqlserverresultset.md)   
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
