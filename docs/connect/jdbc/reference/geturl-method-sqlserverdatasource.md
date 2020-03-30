---
title: Méthode getURL (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dd0d5d2c-91fe-4b0f-a162-69d898ba176e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6f3922e5cf97b6c7b5a795f295249950fd21a9f3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67978199"
---
# <a name="geturl-method-sqlserverdatasource"></a>Méthode getURL (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne l'URL utilisée pour la connexion à la source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getURL()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **Chaîne** qui contient l’URL.  
  
## <a name="remarks"></a>Notes  
 Pour des raisons de sécurité, n’incluez pas le mot de passe dans l’URL fournie à la méthode [setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md). En effet, les serveurs d'applications Java tiers affichent très souvent la valeur définie pour la propriété URL dans l'interface utilisateur de configuration de la source de données. Utilisez plutôt la méthode [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md) pour définir la valeur du mot de passe. Les serveurs d'applications Java n'affichent pas de mot de passe défini dans leur source de données à l'intérieur de l'interface utilisateur de configuration.  
  
> [!NOTE]  
>  Si la méthode setURL n’est pas appelée avant la méthode getURL, getURL retourne la valeur par défaut (« jdbc:sqlserver:// »).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
