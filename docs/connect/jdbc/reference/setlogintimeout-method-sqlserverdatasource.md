---
title: Méthode setLoginTimeout (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b63d1cf4-dc1b-4e35-9a56-50436642eaaf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b655449b2b15e7fbf1f31f7045bc5f0051951a2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47681117"
---
# <a name="setlogintimeout-method-sqlserverdatasource"></a>Méthode setLoginTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nombre de secondes pendant lesquelles cet objet [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) patiente lors de la tentative de connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setLoginTimeout(int loginTimeout)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *loginTimeout*  
  
 Valeur **int** représentant le nombre de secondes à attendre. Zéro indique que le délai d'attente correspond au délai d'attente système par défaut, lequel est de 15 secondes.  
  
## <a name="remarks"></a>Notes   
 Cette méthode setLoginTimeout est spécifiée par la méthode setLoginTimeout dans l’interface javax.sql.DataSource.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
