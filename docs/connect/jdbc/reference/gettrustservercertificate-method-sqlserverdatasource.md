---
title: "Méthode getTrustServerCertificate (SQLServerDataSource) | Documents Microsoft"
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
apiname: getTrustServerCertificate Method (SQLServerDataSource)
apilocation: getTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: e4f443cc-b5d7-4859-81df-836a8642ed07
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fbc992d3ae27a2c519e653d77ec8acbb160d2fe5
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="gettrustservercertificate-method-sqlserverdatasource"></a>Méthode getTrustServerCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne un **booléenne** valeur qui indique si la propriété trustServerCertificate est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean getTrustServerCertificate()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si trustServerCertificate est activée. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Si la propriété trustServerCertificate a la valeur **true**, le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] les certificats Secure Sockets Layer (SSL) sont automatiquement approuvé lorsque la couche de communication est chiffrée à l’aide de SSL. En d’autres termes, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ne validera pas le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] certificat SSL. La valeur par défaut est **false**.  
  
 Si la propriété trustServerCertificate a la valeur **false**, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] validera le certificat SSL du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
