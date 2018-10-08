---
title: Méthode setHostNameInCertificate (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setHostNameInCertificate Method (SQLServerDataSource)
apilocation:
- setHostNameInCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 2bcf4f2e-a103-4374-abc4-ffad4ce8e3c0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 012073c9d1f8f3646c9bea5fd35cb12e0e0343c8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601779"
---
# <a name="sethostnameincertificate-method-sqlserverdatasource"></a>Méthode setHostNameInCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nom d’hôte à utiliser pour valider le certificat SSL (Secure Sockets Layer) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setHostNameInCertificate(java.lang.String hostNameInCertificate)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *hostNameInCertificate*  
  
 **Chaîne** qui contient le nom d’hôte.  
  
## <a name="remarks"></a>Notes   
 La valeur hostNameInCertificate est utilisée pour valider le certificat SSL [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] quand la couche de communication est chiffrée à l’aide du protocole SSL. La valeur par défaut est null.  
  
 Si la propriété hostNameInCertificate est définie sur Null ou n’est pas spécifiée, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] utilise la valeur de la propriété serverName pour effectuer une validation par rapport au certificat SSL [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si la propriété hostNameInCertificate est définie avec une chaîne ou une valeur vide « », le pilote utilise cette valeur pour valider le certificat SSL du serveur.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
