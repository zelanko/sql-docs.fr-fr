---
title: Implémentation d’assemblys | Microsoft Docs
description: Apprenez à utiliser les assemblys hébergés sur SQL Server, notamment la création/modification d’assemblys, la suppression ou l’activation/la désactivation d’assemblys et la gestion des versions.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], implementing
ms.assetid: c228d7bf-a906-4f37-a057-5d464d962ff8
author: rothja
ms.author: jroth
ms.openlocfilehash: 8d97ef8c7dfc617cb6cd56dbcc6d83e0540051d7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85695367"
---
# <a name="assemblies---implementing"></a>Assemblys - Implémentation
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette rubrique fournit des informations sur les concepts suivants, afin de vous aider à implémenter et à utiliser les assemblys dans vos bases de données :  
  
-   Création d'assemblys  
  
-   Modification des assemblys  
  
-   Suppression, désactivation et activation d’assemblys  
  
-   Gestion des versions d’assembly  
  
## <a name="creating-assemblies"></a>Création d'assemblys  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les assemblys sont créés à l'aide de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY, et dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], au moyen de l'éditeur assisté d'assemblys. En outre, le déploiement d’un projet de SQL Server dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] inscrit un assembly dans la base de données qui a été spécifiée pour le projet. Pour plus d’informations, consultez [Déploiement d’objets de base de données CLR](../../relational-databases/clr-integration/deploying-clr-database-objects.md).  
  
 **Pour créer un assembly à l'aide de Transact-SQL**  
  
-   [CREATE ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/create-assembly-transact-sql.md)  
  
 **Pour créer un assembly à l'aide de SQL Server Management Studio**  
  
-   [Propriétés de l’assembly &#40;&#41;page général](../../relational-databases/clr-integration/assemblies-properties.md)  
  
## <a name="modifying-assemblies"></a>Modification des assemblys  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous modifiez les assemblys au moyen de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous utilisez pour cela l'éditeur assisté d'assemblys. Vous pouvez modifier un assembly pour effectuer les tâches suivantes :  
  
-   Changer l'implémentation de l'assembly en chargeant une nouvelle version de ses binaires. Pour plus d’informations, consultez [gestion des versions d’assembly](#_managing) plus loin dans cette rubrique.  
  
-   Changer le jeu d'autorisations de l'assembly. Pour plus d’informations, consultez [Conception d’assemblys](../../relational-databases/clr-integration/assemblies-designing.md).  
  
-   Modifier la visibilité de l'assembly. Les assemblys visibles sont disponibles pour référencement dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les assemblys non visibles ne sont pas disponibles, même s'ils ont été chargés dans la base de données. Par défaut, les assemblys chargés dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont visibles.  
  
-   Ajouter ou supprimer un fichier de débogage ou source associé avec l'assembly.  
  
 **Pour modifier un assembly à l'aide de Transact-SQL**  
  
-   [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-assembly-transact-sql.md)  
  
 **Pour modifier un assembly à l'aide de SQL Server Management Studio**  
  
-   [Propriétés de l’assembly &#40;&#41;page général](../../relational-databases/clr-integration/assemblies-properties.md)  
  
## <a name="dropping-disabling-and-enabling-assemblies"></a>Suppression, désactivation et activation des assemblys  
 Vous supprimez les assemblys à l'aide de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP ASSEMBLY ou dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Pour supprimer un assembly à l'aide de Transact-SQL**  
  
-   [DROP ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)  
  
 **Pour supprimer un assembly à l'aide de SQL Server Management Studio**  
  
-   [Supprimer les objets](../../ssms/object/delete-objects.md)  
  
 Par défaut, l'exécution de tous les assemblys créés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est désactivée. Vous pouvez utiliser l’option **CLR activé** de la procédure stockée système **sp_configure** pour désactiver ou activer l’exécution de tous les assemblys téléchargés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La désactivation de l'exécution d'un assembly empêche l'exécution des fonctions CLR (Common Language Runtime), des procédures stockées, des déclencheurs, des agrégats et des types définis par l'utilisateur, de même qu'elle arrête leur exécution si celle-ci est en cours. Elle n'entrave cependant pas la possibilité de créer, de modifier ou de supprimer des assemblys. Pour plus d’informations, consultez [clr enabled (option de configuration de serveur)](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md).  
  
 **Pour désactiver et activer la création d'assemblys**  
  
-   [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
##  <a name="managing-assembly-versions"></a><a name="_managing"></a>Gestion des versions d’assembly  
 Quand un assembly est chargé dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il est stocké et géré dans les catalogues système de la base de données. Toutes les modifications apportées à la définition de l’assembly dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] doivent être propagées à l’assembly qui est stocké dans le catalogue de la base de données.  
  
 Quand vous modifiez un assembly, vous devez émettre une instruction ALTER ASSEMBLY pour le mettre à jour dans la base de données, de façon à le remplacer par la dernière copie des modèles [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] contenant son implémentation.  
  
 La clause WITH UNCHECKED DATA de l'instruction ALTER ASSEMBLY prescrit à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'actualiser jusqu'aux assemblys dont dépendent des données persistantes de la base de données. En particulier, vous devez spécifier WITH UNCHECKED DATA en présence d'au moins un des éléments suivants :  
  
-   des colonnes calculées persistantes référençant des méthodes de l'assembly, soit directement, soit indirectement via des méthodes ou des fonctions [!INCLUDE[tsql](../../includes/tsql-md.md)] ;  
  
-   Des colonnes d’un type CLR défini par l’utilisateur dépendant de l’assembly, ce type implémentant un format de sérialisation **UserDefined** (non-**Native**).  
  
> [!CAUTION]  
>  Si WITH UNCHECKED DATA n'est pas spécifié, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tente d'empêcher ALTER ASSEMBLY de s'exécuter si la nouvelle version de l'assembly affecte des données existantes dans des tables, des index ou dans d'autres sites persistants. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne garantit cependant pas que les colonnes, les index, les vues indexées ou les expressions calculés seront cohérents avec les routines et les types sous-jacents une fois l'assembly CLR mis à jour. Soyez prudent lorsque vous exécutez ALTER ASSEMBLY pour vous assurer qu'il n'y a pas de discordance entre le résultat d'une expression et une valeur basée sur cette expression stockée dans l'assembly.  
  
 Seuls les membres du rôle de base de données fixe **db_owner** et **db_ddlowner** peuvent exécuter l’instruction ALTER assembly à l’aide de la clause with unchecked Data.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] publie un message dans le journal des événements des applications Windows indiquant que l'assembly a été modifié avec les données non vérifiées des tables. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] marque ensuite les tables contenant les données dépendant de l'assembly comme comportant des données non vérifiées. La colonne **has_unchecked_assembly_data** de l’affichage catalogue **sys. tables** contient la valeur 1 pour les tables qui contiennent des données non vérifiées, et 0 pour les tables sans données non vérifiées.  
  
 Pour résoudre l’intégrité des données non vérifiées, exécutez DBCC CHECKDB avec EXTENDED_LOGICAL_CHECKS sur chaque table qui contient des données non vérifiées. Si DBCC CHECKDB avec EXTENDED_LOGICAL_CHECKS échoue, vous devez soit supprimer les lignes de la table qui ne sont pas valides, soit modifier le code de l’assembly pour résoudre les problèmes, puis émettre des instructions ALTER ASSEMBLy supplémentaires.  
  
 ALTER ASSEMBLY modifie la version de l'assembly. La culture et le jeton de clé publique de l’assembly restent identiques. SQL Server n’autorise pas l’inscription de différentes versions d’un assembly avec le même nom, la même culture et la même clé publique.  
  
### <a name="interactions-with-computer-wide-policy-for-version-binding"></a>Interactions avec la stratégie de l'ordinateur en matière de liaison des versions  
 Si des références à des assemblys stockés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont redirigées vers des versions spécifiques à l'aide de la stratégie du serveur de publication ou de la stratégie de l'administrateur de l'ordinateur, vous devez procéder de l'une des façons suivantes :  
  
-   Assurez-vous que la nouvelle version vers laquelle s'effectue cette redirection se trouve dans la base de données.  
  
-   Modifiez les instructions pointant vers les fichiers de stratégie externes de l'ordinateur ou la stratégie du serveur de publication pour vous assurer qu'elles référencent la version spécifique figurant dans la base de données.  
  
 Sans cela, la tentative de chargement d'une nouvelle version d'assembly dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] échouera.  
  
 **Pour mettre à jour la version de l'assembly**  
  
-   [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-assembly-transact-sql.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Assemblys &#40;Moteur de base de données&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md)   
 [Obtention d'informations sur les assemblys](../../relational-databases/clr-integration/assemblies-getting-information.md)  
  
  
