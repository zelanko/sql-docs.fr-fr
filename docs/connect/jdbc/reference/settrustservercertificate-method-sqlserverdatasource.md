---
title: Méthode setTrustServerCertificate (SQLServerDataSource) | Documents Microsoft
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
ms.topic: article
apiname:
- setTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- setTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 6c37b518-147e-4cd9-9eff-b48a3f5888c6
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2b4a1788fc4e4578cf8b80893d6d1f2c80fa6e3e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="settrustservercertificate-method-sqlserverdatasource"></a>Méthode setTrustServerCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit un **booléenne** valeur qui indique si la propriété trustServerCertificate est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setTrustServerCertificate(boolean trustServerCertificate)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *TrustServerCertificate*  
  
 **true** si le certificat du serveur Secure Sockets Layer (SSL) doit être automatiquement approuvé lorsque la couche de communication est chiffrée à l’aide de SSL. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Si la propriété trustServerCertificate a la valeur **true**, le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] certificat SSL est automatiquement approuvé lorsque la couche de communication est chiffrée à l’aide de SSL. En d’autres termes, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ne validera pas le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] certificat SSL. La valeur par défaut est **false**.  
  
 Si la propriété trustServerCertificate a la valeur **false**, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] validera le certificat SSL du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
