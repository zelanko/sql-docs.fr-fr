---
title: contained database authentication (option de configuration de serveur) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- contained database, enabling
- contained database authentication option
ms.assetid: b80768d2-ac20-4035-a335-d9adb74b3f6e
caps.latest.revision: "11"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 1c0a1178973c9e9bc5dcd2be9cc2fe8d84b7c329
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="contained-database-authentication-server-configuration-option"></a>contained database authentication (option de configuration de serveur)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilisez l'option **contained database authentication** pour activer des bases de données à relation contenant-contenu sur l'instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
 Cette option de serveur vous permet de contrôler l' **authentification de la base de données à relation contenant-contenu**.  
  
-   Lorsque l’option **contained database authentication** est désactivée (0) pour l’instance, les bases de données à relation contenant-contenu ne peuvent pas être créées ou attachées au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
-   Lorsque l’option **contained database authentication** est activée (1) pour l’instance, les bases de données à relation contenant-contenu peuvent être créées ou attachées au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Une base de données à relation contenant-contenu inclut tous les paramètres et métadonnées de la base de données requis pour définir la base de données ; sa configuration ne dépend pas de l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] où la base de données est installée. Les utilisateurs peuvent se connecter à la base de données sans authentifier de connexion au niveau du [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Isoler la base de données du moteur de base de données permet de la déplacer facilement vers une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Inclure tous les paramètres de base de données dans la base de données permet aux propriétaires de base de données de gérer tous les paramètres de configuration pour la base de données. Pour plus d'informations sur les bases de données à relation contenant-contenu, consultez [Bases de données à relation contenant-contenu](../../relational-databases/databases/contained-databases.md).  

> [!NOTE]
> Les bases de données à relation contenant-contenu sont toujours activées pour [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] et [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] , et ne peuvent pas être désactivées.
  
 Si une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comporte des bases de données à relation contenant-contenu, le paramètre **contained database authentication** peut avoir la valeur 0 grâce à l'instruction **RECONFIGURE WITH OVERRIDE** . Lorsque le paramètre **contained database authentication** a la valeur 0, l'authentification des base de données à relation contenant-contenu est désactivée.  
  
> [!IMPORTANT]  
>  Quand des bases de données contenues sont activées, les utilisateurs de base de données dotés de l'autorisation ALTER ANY USER, comme les membres des rôles de base de données db_owner et db_accessadmin, peuvent accorder l'accès aux bases de données et ce faisant, accorder l'accès à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cela signifie que le contrôle de l'accès au serveur n'est plus limité aux membres du rôle serveur fixe sysadmin et securityadmin et aux connexions avec le niveau de serveur CONTROL SERVER et l'autorisation ALTER ANY LOGIN. Avant d'autoriser des bases de données à relation contenant-contenu, vous devez comprendre les risques qui leur sont associés. Pour plus d'informations, consultez [Bonnes pratiques de sécurité avec les bases de données à relation contenant-contenu](../../relational-databases/databases/security-best-practices-with-contained-databases.md).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant active des bases de données à relation contenant-contenu sur l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
```tsql  
sp_configure 'contained database authentication', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
