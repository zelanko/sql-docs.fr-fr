---
title: Méthode setIntegratedSecurity (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setIntegratedSecurity
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4c968ee4-b041-424a-bf69-cc2c4a4f51c6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 79d9090df19851af3a778e23b7919f28081f32ef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974146"
---
# <a name="setintegratedsecurity-method-sqlserverdatasource"></a>Méthode setIntegratedSecurity (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit une valeur **booléenne** qui indique si la propriété integratedSecurity est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setIntegratedSecurity(boolean enable)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *enable*  
  
 **true** si IntegratedSecurity est activé. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Définissez sa valeur sur **true** pour indiquer que les informations d’identification Windows seront utilisées par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour authentifier l’utilisateur de l’application. Si la valeur est **true**, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] recherche les informations d’identification déjà fournies lors de la connexion à l’ordinateur ou au réseau dans le cache des informations d’identification de l’ordinateur local. Si la valeur est **false**, le nom d’utilisateur et le mot de passe doivent être fournis.  
  
> [!NOTE]  
>  Cette propriété de connexion est prise en charge seulement sur les systèmes d’exploitation [!INCLUDE[msCoName](../../../includes/msconame_md.md)] Windows.  
  
 Pour plus d’informations sur l’utilisation de l’authentification intégrée, consultez [génération de l’URL de connexion](../../../connect/jdbc/building-the-connection-url.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
