---
description: Méthode getExtraNameCharacters (SQLServerDatabaseMetaData)
title: Méthode getExtraNameCharacters (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getExtraNameCharacters
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a22becfe-0f07-4a15-8d11-06d4054b2369
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7701c2fe192e5f60acf78c2e59e562c8688e6d40
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436101"
---
# <a name="getextranamecharacters-method-sqlserverdatabasemetadata"></a>Méthode getExtraNameCharacters (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère tous les caractères supplémentaires qui peuvent être utilisés dans les noms d'identificateurs sans guillemets, par exemple, au-delà de a-z, A-Z, 0-9 et _.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getExtraNameCharacters()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **Chaîne** contenant les caractères supplémentaires.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getExtraNameCharacters est spécifiée par la méthode getExtraNameCharacters de l’interface java.sql.DatabaseMetaData.  
  
 Lors de l’utilisation du [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] avec une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], cette méthode retourne les caractères supplémentaires $, # et \@.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
