---
title: Méthode setHostNameInCertificate (SQLServerDataSource) | Documents Microsoft
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
- setHostNameInCertificate Method (SQLServerDataSource)
apilocation:
- setHostNameInCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 2bcf4f2e-a103-4374-abc4-ffad4ce8e3c0
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 84fe40795339ad4cc858716fbf73417363fb1673
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sethostnameincertificate-method-sqlserverdatasource"></a>Méthode setHostNameInCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nom d’hôte à utiliser pour valider la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] les certificats Secure Sockets Layer (SSL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setHostNameInCertificate(java.lang.String hostNameInCertificate)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *hostNameInCertificate*  
  
 A **chaîne** qui contient le nom d’hôte.  
  
## <a name="remarks"></a>Notes  
 La valeur hostNameInCertificate sert à valider le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] certificat SSL lors de la couche de communication est chiffrée à l’aide de SSL. La valeur par défaut est null.  
  
 Si la propriété hostNameInCertificate est définie à null ou non spécifié, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] utilise la valeur de propriété serverName pour valider par rapport à la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] certificat SSL. Si la propriété hostNameInCertificate est définie avec une chaîne ou une valeur vide « », le pilote utilise cette valeur pour valider le certificat SSL du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
