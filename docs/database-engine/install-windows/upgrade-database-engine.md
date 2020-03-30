---
title: Mettre à niveau le moteur de base de données | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], databases
- compatibility levels [SQL Server], after upgrade
- Database Engine [SQL Server], upgrading
ms.assetid: 3c036813-36cf-4415-a0c9-248d0a433859
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 7dcf58da00887f396568367982da97b9c75e32ad
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "73531560"
---
# <a name="upgrade-database-engine"></a>Mettre à niveau le moteur de base de données

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
  Les articles de cette section vous aideront à mettre à niveau le moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
1.  [Choisir une méthode de mise à niveau du moteur de base de données](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md). Avant de commencer une mise à niveau, vous devez comprendre les différentes méthodes de mise à niveau. Cet article décrit les méthodes de mise à niveau ainsi que les étapes correspondantes.  
  
2.  [Planifier et tester le plan de mise à niveau du moteur de base de données](../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md). Après avoir examiné les méthodes de mise à niveau, vous pourrez développer la méthode de mise à niveau correspondant à votre environnement, puis tester la méthode de mise à niveau avant la mise à niveau de l’environnement existant. Cet article explique comment développer et tester un plan de mise à niveau et de test.  
  
3.  [Mettre à niveau le moteur de base de données](../../database-engine/install-windows/complete-the-database-engine-upgrade.md). Une fois que le moteur de base de données a été mis à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et que les bases de données sont en ligne, vous devez effectuer des étapes supplémentaires, notamment exécuter une nouvelle sauvegarde, mettre à niveau les fonctionnalités de base de données pour activer de nouvelles fonctionnalités et renseigner à nouveau les catalogues de texte intégral. Cet article décrit ces étapes.  
  
4.  Mettre à niveau le [niveau de compatibilité de base de données](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md#compatibility-levels-and-database-engine-upgrades) (**S’applique à :** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]). L’une des étapes à suivre après la mise en ligne de vos bases de données dans la nouvelle version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] peut consister à mettre à niveau le mode des fonctionnalités de base de données pour activer de nouvelles fonctionnalités, en modifiant le niveau de compatibilité de base de données. Cette opération peut être effectuée manuellement ou par le biais de l’Assistant Paramétrage de requêtes. 

    - [Changer le mode de compatibilité de la base de données et utiliser le magasin des requêtes](../../database-engine/install-windows/change-the-database-compatibility-mode-and-use-the-query-store.md). Après avoir modifié manuellement le niveau de compatibilité de la base de données, utilisez le magasin des requêtes pour superviser les performances et identifier les régressions possibles. Cet article traite du processus recommandé et fournit un workflow recommandé.  

    - [Changer le mode de compatibilité de la base de données avec l’Assistant Paramétrage de requêtes](../../relational-databases/performance/upgrade-dbcompat-using-qta.md). En guise d’alternative à une modification manuelle, utilisez l’**Assistant Paramétrage de requêtes** pour vous guider dans le processus recommandé de modification du niveau de compatibilité de la base de données. Cet article traite de ce processus et fournit des instructions sur le workflow de l’Assistant Paramétrage de requêtes.  

    Pour plus d’informations sur les nouvelles fonctionnalités et les comportements améliorés disponibles après avoir modifié un niveau de compatibilité de base de données, consultez [Différences entre les niveaux de compatibilité](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md#compatibility-levels-and-stored-procedures).

5.  [Tirer parti des nouvelles fonctionnalités SQL Server](https://www.microsoft.com/sql-server/sql-server-2019). Enfin, une fois que vous avez exécuté les étapes précédentes, vous pouvez découvrir comment bénéficier des nouvelles améliorations spécifiques du moteur de base de données. Cet article suggère quelques exemples d’améliorations et fournit des liens contenant davantage d’informations.  
  
  
