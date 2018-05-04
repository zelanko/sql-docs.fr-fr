---
title: Méthode getExtraNameCharacters (SQLServerDatabaseMetaData) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getExtraNameCharacters
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a22becfe-0f07-4a15-8d11-06d4054b2369
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 43aeda1b5e4c502233195e807e631edccedb6bda
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="getextranamecharacters-method-sqlserverdatabasemetadata"></a>Méthode getExtraNameCharacters (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère tous les caractères supplémentaires qui peuvent être utilisés dans les noms d'identificateurs sans guillemets, par exemple, au-delà de a-z, A-Z, 0-9 et _.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getExtraNameCharacters()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 A **chaîne** qui contient les caractères supplémentaires.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getExtraNameCharacters est spécifiée par la méthode getExtraNameCharacters dans l’interface java.sql.DatabaseMetaData.  
  
 Lorsque vous utilisez la [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] avec un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] base de données, cette méthode retourne le $, # et @ caractères supplémentaires.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membres de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
