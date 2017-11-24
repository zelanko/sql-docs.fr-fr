---
title: "Méthode setString (long, java.lang.String) | Documents Microsoft"
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
apiname: SQLServerClob.setString (long, java.lang.String)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 1b2190e9-5ace-497a-8554-0e913ea9b0cb
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 491f4148e34714829156572d9832d3d4753c291c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="setstring-method-long-javalangstring"></a>Méthode setString (long, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Écrit la donnée **chaîne** dans le CLOB, en commençant à la position donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int setString(long pos,  
                     java.lang.String s)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *bons de commande*  
  
 Position à laquelle démarrer l'écriture dans l'objet CLOB.  
  
 *s*  
  
 Le **chaîne** à écrire dans le CLOB.  
  
## <a name="return-value"></a>Valeur retournée  
 Nombre de caractères écrits.  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode setString est spécifiée par la méthode setString dans l’interface java.sql.Clob.  
  
 Les données de caractères sont remplacées en démarrant à la position spécifiée et peuvent dépasser la longueur initiale de l'objet CLOB. La spécification d'une valeur position+1 permet d'ajouter la chaîne. La spécification d'une valeur position+2 ou supérieure (ou de zéro ou d'une valeur inférieure) entraîne la levée d'une erreur de position.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode setString &#40; SQLServerClob &#41;](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)   
 [Méthodes SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Membres de SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob, classe](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
