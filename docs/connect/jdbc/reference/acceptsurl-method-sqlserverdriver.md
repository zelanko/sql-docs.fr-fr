---
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
ms.openlocfilehash: 68e12a39cb4a27f170b7f12705f17791bb40b649
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923703"
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
 [SQLServerDriver, classe](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
