---
title: Mettre à niveau le moteur de base de données | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2017
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
manager: craigg
ms.openlocfilehash: 99d1b87ac5584f05911ebfb16387babc408e26f5
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51600929"
---
# <a name="upgrade-database-engine"></a>Mettre à niveau le moteur de base de données

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  
  Les articles de cette section vous aideront à mettre à niveau le moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
1.  [Choisir une méthode de mise à niveau du moteur de base de données](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md) Avant de commencer une mise à niveau, vous devez comprendre les différentes méthodes de mise à niveau. Cet article décrit les méthodes de mise à niveau ainsi que les étapes correspondantes.  
  
2.  [Planifier et tester le plan de mise à niveau du moteur de base de données](../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md) Après avoir examiné les méthodes de mise à niveau, vous pourrez développer la méthode de mise à niveau correspondant à votre environnement, puis tester la méthode de mise à niveau avant la mise à niveau de l’environnement existant. Cet article explique comment développer et tester un plan de mise à niveau et de test.  
  
3.  [Mettre à niveau le moteur de base de données](../../database-engine/install-windows/complete-the-database-engine-upgrade.md) Une fois vos bases de données mises à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], il vous reste quelques étapes à effectuer : exécuter une nouvelle sauvegarde, activer les nouvelles fonctionnalités et renseigner à nouveau les catalogues de texte intégral. Cet article décrit ces étapes.  
  
4.  [Modifier le mode de compatibilité de base de données et utiliser le magasin des requêtes](../../database-engine/install-windows/change-the-database-compatibility-mode-and-use-the-query-store.md) Une des étapes à effectuer après la mise à niveau de vos bases de données vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] consiste à activer les nouvelles fonctionnalités en modifiant le mode de compatibilité de base de données, puis en utilisant le magasin des requêtes pour surveiller les performances. Cet article traite de ce processus et fournit un flux de travail recommandé.  
  
5.  [Tirer parti des nouvelles fonctionnalités SQL Server](https://www.microsoft.com/sql-server/sql-server-2017) Enfin, une fois que vous avez exécuté les étapes précédentes, vous pouvez découvrir comment bénéficier des nouvelles améliorations spécifiques du moteur de base de données. Cet article suggère quelques exemples d’améliorations et fournit des liens contenant davantage d’informations.  
  
  
