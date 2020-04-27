---
title: Créer des agrégats définis par l’utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- aggregate functions [SQL Server], user-defined
- user-defined functions [CLR integration]
ms.assetid: c278b746-6323-4b32-b460-239915acc067
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 23d5180928f4f3335aa17dff61b50e6fdd19549f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "68196470"
---
# <a name="create-user-defined-aggregates"></a>Créer des agrégats définis par l'utilisateur
  Vous pouvez créer un objet de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] programmé dans un assembly CLR. Les objets de base de données qui peuvent tirer parti du modèle de programmation riche fourni par le CLR sont notamment les déclencheurs, les procédures stockées, les fonctions, les fonctions d'agrégation et les types.  
  
 Au même titre que les fonctions d'agrégation intégrées fournies dans [!INCLUDE[tsql](../../includes/tsql-md.md)], les fonctions d'agrégation définies par l'utilisateur réalisent un calcul sur un ensemble de valeurs et retournent une seule valeur.  
  
 La création d'une fonction d'agrégation définie par l'utilisateur dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suppose les étapes suivantes :  
  
-   Définissez la fonction d'agrégation définie par l'utilisateur en tant que classe dans un langage [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework. Pour plus d’informations sur la programmation d’agrégats définis par l’utilisateur dans le CLR, consultez [Agrégats CLR définis par l’utilisateur](../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md). Compilez cette classe pour créer un assembly CLR à l'aide du compilateur de langage approprié.  
  
-   Inscrivez l'assembly dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de l'instruction CREATE ASSEMBLY. Pour plus d’informations sur les assemblys dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Assemblys &#40;moteur de base de données&#41;](../clr-integration/assemblies-database-engine.md).  
  
-   Créez l'agrégat défini par l'utilisateur qui fait référence à l'assembly inscrit à l'aide de l'instruction CREATE AGGREGATE.  
  
> [!NOTE]  
>  Le déploiement d’un projet SQL Server dans [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a pour effet d’inscrire un assembly dans la base de données qui a été spécifiée pour le projet. Le déploiement du projet crée aussi une agrégation définie par l'utilisateur dans la base de données pour toutes les définitions de classe annotées par l'attribut `SqlUserDefinedAggregate`. Pour plus d’informations, consultez [Déploiement d’objets de base de données CLR](../clr-integration/deploying-clr-database-objects.md).  
  
> [!NOTE]  
>  La fonctionnalité d'exécution du code CLR par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est désactivée par défaut. Vous pouvez créer, modifier et supprimer des objets de base de données qui font référence à des modules de code managé, mais ces références ne s’exécutent pas dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si l’option [clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) n’est pas activée à l’aide de [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).  
  
 **Pour créer, modifier ou supprimer un assembly**  
  
-   [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [DROP ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 **Pour créer un agrégat défini par l'utilisateur**  
  
-   [CREATE AGGREGATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-aggregate-transact-sql)  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de programmation pour l’intégration du CLR &#40;Common Language Runtime&#41;](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
