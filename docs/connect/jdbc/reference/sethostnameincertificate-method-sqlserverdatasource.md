---
description: Méthode setHostNameInCertificate (SQLServerDataSource)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 886a32898b04cc8907a832d54a3051222e4d0fb7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431821"
---
# <a name="sethostnameincertificate-method-sqlserverdatasource"></a>Méthode setHostNameInCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nom d’hôte à utiliser dans la validation du certificat TLS (Transport Layer Security), anciennement SSL (Secure Sockets Layer), [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setHostNameInCertificate(java.lang.String hostNameInCertificate)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *hostNameInCertificate*  
  
 **Chaîne** qui contient le nom d’hôte.  
  
## <a name="remarks"></a>Notes  
 La valeur hostNameInCertificate est utilisée pour valider le certificat TLS/SSL [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] quand la couche de communication est chiffrée à l’aide du protocole TLS. La valeur par défaut est null.  
  
 Si la propriété hostNameInCertificate est Null ou n’est pas spécifiée, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] utilise la valeur de la propriété serverName pour effectuer une validation par rapport au certificat TLS/SSL [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si la propriété hostNameInCertificate est définie avec une chaîne ou une chaîne vide (""), le pilote utilise cette valeur pour valider le certificat TLS/SSL du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
