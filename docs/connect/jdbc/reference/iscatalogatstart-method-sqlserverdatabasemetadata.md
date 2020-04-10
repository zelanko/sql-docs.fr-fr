---
title: Méthode isCatalogAtStart (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.isCatalogAtStart
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 665173d2-14c7-4ce1-954e-4adb53fb9b39
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ee035ae51b99fc325acbbd545d98555416bf6a02
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928690"
---
# <a name="iscatalogatstart-method-sqlserverdatabasemetadata"></a>Méthode isCatalogAtStart (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si un catalogue s'affiche au début d'un nom de table complet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isCatalogAtStart()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si le nom du catalogue apparaît en premier. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode isCatalogAtStart est spécifiée par la méthode isCatalogAtStart de l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
