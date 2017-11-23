---
title: "Méthode getShort (int) | Documents Microsoft"
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
apiname: SQLServerCallableStatement.getShort (int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: cd9773c1-b598-4adb-aaf6-0c0f589cbef5
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e074b62c3685d852bcf817f0a9a3acf61fa7b09c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getshort-method-int"></a>Méthode getShort (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant qu’un **court** en fonction de l’index de paramètre de langage de programmation Java.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public short getShort(int index)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 Un **int** qui indique l’index de paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 A **court** valeur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getShort est spécifiée par la méthode getShort dans l’interface java.sql.CallableStatement.  
  
 Cette méthode est prise en charge uniquement sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] des types de données qui peuvent retourner en toute sécurité une valeur entière de telles que **smallint**, **tinyint**, et **bits**. L'utilisation de cette méthode sur n'importe quel autre type de données entraîne la levée d'une exception.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getShort &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getshort-method-sqlservercallablestatement.md)   
 [Membres de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
