---
title: Propriétés de l'Agent SQL Server (page Connexion)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e2edbc16241c3817ca6cd8ba17e3e82ec1b3471f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755135"
---
# <a name="sql-server-agent-properties-connection-page"></a>Propriétés de l'Agent SQL Server (page Connexion)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Utilisez cette page pour afficher et modifier les paramètres de la connexion du service [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Options  
**Alias du serveur hôte local**  
Spécifie l'alias à utiliser pour se connecter à l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous ne pouvez pas utiliser les options de connexion par défaut pour l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , définissez un alias pour l'instance et spécifiez l'alias à cet endroit.  
  
**Utiliser l'authentification Windows**  
Définit l'authentification [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows comme la méthode d'authentification utilisée pour se connecter à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se connecte sous le compte utilisé par le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
**Utiliser l’authentification SQL Server**  
Définit l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comme la méthode d'authentification utilisée pour se connecter à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!IMPORTANT]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est fournie dans un souci de compatibilité descendante. Pour une sécurité renforcée, utilisez l'authentification Windows dans la mesure du possible.  
  
**Connexion**  
Permet de spécifier le nom d’accès à utiliser pour la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Mot de passe**  
Permet de spécifier le mot de passe à utiliser pour la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
