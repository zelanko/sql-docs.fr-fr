---
title: getbinarystream, méthode (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBinaryStream (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: de22a6c4-1ba3-4ed0-91a2-bf235c2ceec3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ddd2f46d67285d95150f185319e0fb327d34e8dd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47826797"
---
# <a name="getbinarystream-method-int"></a>Méthode getBinaryStream (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur de l’index de la colonne désignée dans la ligne actuelle de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) en tant que flux binaire d’octets non interprétés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.io.InputStream getBinaryStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnIndex*  
  
 Un **int** qui indique l’index de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet InputStream.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getBinaryStream est spécifiée par la méthode getBinaryStream dans l’interface java.sql.ResultSet.  
  
 Cette méthode peut être utilisée seulement avec des types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] binary, varbinary, varbinary(max) et image. Si vous essayez de l'utiliser avec d'autres types de données, une exception est levée.  
  
 Une fois que cette méthode a obtenu la valeur sous forme de flux, cette valeur peut être lue par segments à partir du flux. Cette méthode convient particulièrement à la récupération de grandes valeurs LONGVARBINARY.  
  
> [!NOTE]  
>  Toutes les données figurant dans le flux retourné doivent être lues avant d'obtenir la valeur de toute autre colonne. L'appel suivant à une méthode getter fermera implicitement le flux. De même, un flux peut retourner 0 quand la méthode InputStream.available est appelée, que des données soient ou non disponibles.  
  
## <a name="see-also"></a> Voir aussi  
 [getBinaryStream, méthode (SQLServerResultSet)](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
