---
title: Méthode getBytes (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getBytes (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8c2973e6-d57f-4f64-b812-350ce4098ce6
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 51eaf47a34a11d813c096e77f61bead4ea142ef2
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66804037"
---
# <a name="getbytes-method-int"></a>Méthode getBytes (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant que valeur de tableau d'octets en fonction de l'index de paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public byte[] getBytes(int index)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 Un **int** qui indique l’index de paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Un tableau de **octets** valeurs.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Dans la version précédente du [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], vous pouviez utiliser SQLServerCallableStatement.getBytes pour convertir des valeurs entre des tableaux d’octets et le type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **date**, **time**, **datetime2** ou **datetimeoffset**. À présent, l'utilisation de cette méthode avec ces types de données lève une exception indiquant que la conversion n'est pas prise en charge.  
  
 Cette méthode getBytes est spécifiée par la méthode getBytes de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [getBytes, méthode (SQLServerCallableStatement)](../../../connect/jdbc/reference/getbytes-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
