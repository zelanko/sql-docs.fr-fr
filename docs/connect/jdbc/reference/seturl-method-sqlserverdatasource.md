---
title: "Méthode setURL (SQLServerDataSource) | Documents Microsoft"
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
- SQLServerDataSource.setURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bea70100-ac98-4625-8748-ef7cc0b111ea
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dd1f100fcf00678741675c113512eb95a3484368
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="seturl-method-sqlserverdatasource"></a>Méthode setURL (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit l’URL qui est utilisé pour se connecter à la source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setURL(java.lang.String url)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *URL*  
  
 A **chaîne** qui contient l’URL.  
  
## <a name="remarks"></a>Notes  
 Pour des raisons de sécurité, vous ne devez pas inclure le mot de passe dans l’URL fournie à la méthode setURL. En effet, les serveurs d'applications Java tiers affichent très souvent la valeur définie pour la propriété URL dans l'interface utilisateur de configuration de la source de données. Utilisez plutôt le [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md) méthode pour définir la valeur de mot de passe. Les serveurs d'applications Java n'affichent pas de mot de passe défini dans leur source de données à l'intérieur de l'interface utilisateur de configuration.  
  
> [!NOTE]  
>  Si la méthode setURL n’est pas appelée avant d’appeler le [getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md) méthode getURL retourne la valeur par défaut « SQLServer : / / ».  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
