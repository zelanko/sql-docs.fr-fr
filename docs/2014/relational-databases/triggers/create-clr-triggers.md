---
title: Créer des déclencheurs CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- CRL triggers
- DML triggers, CLR triggers
- DDL triggers, CLR triggers
ms.assetid: 31f41703-134d-49fc-9850-76c297351c2c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b68531b962b10785927c6212b2483f2d9c1d7d3a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62698830"
---
# <a name="create-clr-triggers"></a>Créer des déclencheurs CLR
  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez créer un objet de base de données programmée en fonction d’un assembly créé dans le CLR (Common Language Runtime) [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Les objets de base de données qui peuvent tirer parti du modèle de programmation puissant qu'offre le CLR sont les déclencheurs DML, les déclencheurs DDL, les procédures stockées, les fonctions, les fonctions d'agrégation et les types.  
  
 La création d'un déclencheur CLR (DML ou DDL) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implique les étapes suivantes :  
  
-   Définissez le déclencheur en tant que classe dans un langage .NET Framework. Pour plus d’informations sur la programmation de déclencheurs dans le CLR, consultez [Déclencheurs CLR](../../database-engine/dev-guide/clr-triggers.md). Ensuite, compilez la classe pour créer un assembly dans le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] à l'aide du compilateur du langage approprié.  
  
-   Inscrivez l'assembly dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de l'instruction CREATE ASSEMBLY. Pour plus d’informations sur les assemblys dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Assemblys &#40;moteur de base de données&#41;](../clr-integration/assemblies-database-engine.md).  
  
-   Créez le déclencheur qui fait référence à l'assembly inscrit.  
  
> [!NOTE]  
>  Le déploiement d’un projet SQL Server dans [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a pour effet d’inscrire un assembly dans la base de données qui a été spécifiée pour le projet. Le déploiement du projet crée aussi les déclencheurs CLR dans la base de données pour toutes les méthodes annotées par l'attribut `SqlTrigger`. Pour plus d’informations, consultez [Déploiement d’objets de base de données CLR](../clr-integration/deploying-clr-database-objects.md).  
  
> [!NOTE]  
>  La fonctionnalité d'exécution du code CLR par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est désactivée par défaut. Vous pouvez créer, modifier et supprimer des objets de base de données qui font référence à des modules de code managé, mais ces références ne s’exécutent pas dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si l’option [CLR activé](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) n’est pas activée à l’aide de [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).  
  
 **Pour créer, modifier ou supprimer un assembly**  
  
-   [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [DROP ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 **Pour créer un déclencheur CLR**  
  
-   [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)  
  
## <a name="see-also"></a>Voir aussi  
 [Déclencheurs DML](dml-triggers.md)   
 [Concepts de programmation pour l’intégration du CLR &#40;Common Language Runtime&#41;](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md)   
 [Accès aux données à partir d'objets de base de données CLR](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
