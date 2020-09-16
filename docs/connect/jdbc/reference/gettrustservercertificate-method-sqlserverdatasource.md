---
description: Méthode getTrustServerCertificate (SQLServerDataSource)
title: Méthode getTrustServerCertificate (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- getTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- getTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: e4f443cc-b5d7-4859-81df-836a8642ed07
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c3a5de057e6a9363f4e3feeace35f2b5105d3cd3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434051"
---
# <a name="gettrustservercertificate-method-sqlserverdatasource"></a>Méthode getTrustServerCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne une valeur **booléenne** qui indique si la propriété trustServerCertificate est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean getTrustServerCertificate()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si trustServerCertificate est activé. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Si la propriété trustServerCertificate a la valeur **true**, le certificat TLS (Transport Layer Security) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], anciennement SSL (Secure Sockets Layer), est automatiquement approuvé quand la couche de communication est chiffrée avec TLS. En d’autres termes, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ne valide pas le certificat TLS/SSL [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La valeur par défaut est **false**.  
  
 Si la propriété trustServerCertificate a la valeur **false**, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] valide le certificat TLS/SSL du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
