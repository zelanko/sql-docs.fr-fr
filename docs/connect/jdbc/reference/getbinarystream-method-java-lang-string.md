---
title: Méthode getBinaryStream (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBinaryStream (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 149609b5-a6de-4e23-a440-7061775d0899
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a0ee14b90dd8aaffb178c81ea46e5ec914752e28
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953696"
---
# <a name="getbinarystream-method-javalangstring"></a>Méthode getBinaryStream (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du nom de la colonne désignée dans la ligne actuelle de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) en tant que flux binaire d’octets non interprétés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.io.InputStream getBinaryStream(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnName*  
  
 Valeur **String** qui contient le nom de la colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet InputStream.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getBinaryStream est spécifiée par la méthode getBinaryStream dans l’interface java. Sql. ResultSet.  
  
 Cette méthode peut être utilisée seulement avec des types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] binary, varbinary, varbinary(max) et image. Si vous essayez de l'utiliser avec d'autres types de données, une exception est levée.  
  
 Une fois que cette méthode a obtenu la valeur sous forme de flux, cette valeur peut être lue par segments à partir du flux. Cette méthode convient particulièrement à la récupération de grandes valeurs LONGVARBINARY.  
  
> [!NOTE]  
>  Toutes les données figurant dans le flux retourné doivent être lues avant d'obtenir la valeur de toute autre colonne. L'appel suivant à une méthode getter fermera implicitement le flux. De même, un flux peut retourner 0 quand la méthode InputStream.available est appelée, que des données soient ou non disponibles.  
  
## <a name="see-also"></a>Voir aussi  
 [getBinaryStream, méthode (SQLServerResultSet)](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
