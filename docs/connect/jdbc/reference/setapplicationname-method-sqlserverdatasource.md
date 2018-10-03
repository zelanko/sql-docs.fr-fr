---
title: Méthode setApplicationName (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setApplicationName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 24d6e48d-53c4-4da2-a6de-1cdff463c9cd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 54fadc7402489ce4811347d252c061bb2d42e713
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721479"
---
# <a name="setapplicationname-method-sqlserverdatasource"></a>Méthode setApplicationName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nom de l'application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setApplicationName(java.lang.String applicationName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *applicationName*  
  
 **Chaîne** qui contient le nom de l’application.  
  
## <a name="remarks"></a>Notes   
 Le nom d’application est utilisé pour identifier l’application spécifique dans différents de profilage et de journalisation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si le nom d’application n’est pas défini, la méthode getApplicationName retourne la chaîne non localisée « [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ».  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
