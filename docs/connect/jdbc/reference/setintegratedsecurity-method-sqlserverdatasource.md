---
title: Méthode setIntegratedSecurity (SQLServerDataSource) | Documents Microsoft
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
- SQLServerDataSource.setIntegratedSecurity
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4c968ee4-b041-424a-bf69-cc2c4a4f51c6
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 320db4baa925a55039623180d092dd3845e0d691
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="setintegratedsecurity-method-sqlserverdatasource"></a>Méthode setIntegratedSecurity (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit un **booléenne** valeur qui indique si la propriété integratedSecurity est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setIntegratedSecurity(boolean enable)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *enable*  
  
 **true** si integratedSecurity est activée. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 La valeur «**true**» pour indiquer que les informations d’identification Windows seront utilisées par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] pour authentifier l’utilisateur de l’application. Si «**true**», le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] recherche le cache des informations d’identification qui ont déjà été fournis à l’ouverture de session d’ordinateur ou réseau ordinateur local. Si «**false**», le nom d’utilisateur et un mot de passe doivent être fournis.  
  
> [!NOTE]  
>  Cette propriété est uniquement prise en charge sur [!INCLUDE[msCoName](../../../includes/msconame_md.md)] systèmes d’exploitation Windows.  
  
 Pour plus d’informations sur l’utilisation de l’authentification intégrée, consultez [générer l’URL de connexion](../../../connect/jdbc/building-the-connection-url.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
