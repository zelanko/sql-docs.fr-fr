---
title: TRUSTWORTHY, propriété de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database property
ms.assetid: 64b2a53d-4416-4a19-acc0-664a61b45348
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 9ac99b46c31d67b0175fffa882dcf5411194930c
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43025549"
---
# <a name="trustworthy-database-property"></a>TRUSTWORTHY, propriété de base de données
  La propriété de base de données TRUSTWORTHY permet d'indiquer si l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] approuve la base de données et son contenu. Par défaut, cette propriété a la valeur OFF, mais peut être définie sur ON à l'aide de l'instruction ALTER DATABASE. Par exemple, `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;`.  
  
> [!NOTE]  
>  Pour définir cette option, vous devez être membre du rôle serveur fixe **sysadmin** .  
  
 Cette propriété permet de minimiser certaines menaces résultant de l'attachement d'une base de données contenant l'un des objets suivants :  
  
-   Assemblys malveillants dotés d'une autorisation EXTERNAL_ACCESS ou UNSAFE. Pour plus d’informations, consultez [Sécurité de l’intégration du CLR](../clr-integration/security/clr-integration-security.md).  
  
-   Modules malveillants définis dans le but de s'exécuter en tant qu'utilisateurs à privilèges élevés. Pour plus d’informations, consultez [Clause EXECUTE AS &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql).  
  
 Ces deux situations exigent un niveau spécifique de privilèges et sont mises en défaut par des mécanismes appropriés dès lors qu'elles sont utilisées dans le cadre d'une base de données déjà attachée à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Toutefois, si la base de données est mise hors ligne, un utilisateur qui a accès au fichier de la base de données peut éventuellement l'attacher à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de son choix et ajouter un contenu malveillant à la base de données. En cas de détachement et d'attachement de bases de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], certaines autorisations sont définies dans des fichiers de données et des fichiers journaux pour restreindre l'accès aux fichiers de la base de données.  
  
 Dans la mesure où il est impossible de faire immédiatement confiance à une base de données qui est attachée à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , la base de données n'a pas le droit d'accéder aux ressources au-delà de son étendue tant qu'elle n'a pas été explicitement déclarée fiable. De plus, les modules conçus pour accéder aux ressources extérieures à la base de données et les assemblys dotés des autorisations EXTERNAL_ACCESS ou UNSAFE ont des impératifs supplémentaires à respecter pour pouvoir s'exécuter correctement.  
  
## <a name="related-content"></a>Contenu associé  
 [Centre de sécurité pour le moteur de base de données SQL Server et la base de données SQL Azure](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
