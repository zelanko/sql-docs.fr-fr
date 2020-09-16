---
description: Méthode acceptsURL (SQLServerDriver)
title: Méthode acceptsURL (SQLServerDriver) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDriver.acceptsURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fc744566-7191-4b15-9f76-b4b8087fb14a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 17dad07495a7297a70f005e95162ea3edd968296
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438301"
---
# <a name="acceptsurl-method-sqlserverdriver"></a>Méthode acceptsURL (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Vérifie si l'URL donnée est valide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean acceptsURL(java.lang.String url)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *url*  
  
 Valeur **String** contenant l’URL utilisée pour la connexion à la base de données.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si l’URL donnée est valide. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode acceptsURL est spécifiée par la méthode acceptsURL dans l'interface java.sql.Driver.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDriver, méthodes](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [SQLServerDriver, membres](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [Classe SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
