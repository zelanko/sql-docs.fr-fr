---
title: "Méthode setApplicationName (SQLServerDataSource) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.setApplicationName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 24d6e48d-53c4-4da2-a6de-1cdff463c9cd
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dddba9b465d2b9bd2edfe42f850af6a3b64cd503
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

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
  
 A **chaîne** qui contient le nom de l’application.  
  
## <a name="remarks"></a>Notes  
 Le nom de l’application est utilisé pour identifier l’application dans différentes [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] profilage et outils de journalisation. Si le nom de l’application n’est pas défini, la méthode getApplicationName retourne la chaîne non localisée «[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]».  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

