---
title: Vue d’ensemble de l’intégration du Common Language Runtime (CLR) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- managed code [SQL Server]
- common language runtime [SQL Server], about CLR integration
- cross-language integration
- integrating CLR [SQL Server]
- .NET Framework [SQL Server], common language runtime
- code access security [CLR integration]
- managed code [SQL Server], CLR integration
ms.assetid: 7be9e644-36a2-48fc-9206-faf59fdff4d7
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a7764c6e8e45b56e43e592e70b1c85b8d4744b69
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62919324"
---
# <a name="common-language-runtime-clr-integration-overview"></a>Vue d'ensemble de l'intégration du CLR (Common Language Runtime)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] intègre désormais l’intégration du composant Common Language Runtime (CLR) de l' .NET Framework pour [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Le CLR fournit le code managé avec des services tels que l'intégration interlangage, la sécurité d'accès du code, la gestion de la durée de vie des objets et la prise en charge du débogage et des profils. Pour les utilisateurs et les développeurs d'applications [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'intégration du CLR permet désormais d'écrire des procédures stockées, des déclencheurs, des types définis par l'utilisateur, des fonctions définies par l'utilisateur (fonctions scalaires et fonctions table) et des fonctions d'agrégation définies par l'utilisateur, à l'aide de langages du .NET Framework, tels que [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET et [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] inclut la version 4 préinstallée du .NET Framework.  
  
 Citons quelques-uns des avantages majeurs de cette intégration :  
  
-   **Un meilleur modèle de programmation.** Les langages .NET Framework sont à bien des égards plus riches que Transact-SQL, en proposant des constructions et des fonctions qui n'étaient pas jusque-là accessibles aux développeurs [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les développeurs peuvent aussi tirer parti de la puissance de la bibliothèque du .NET Framework, qui propose un ensemble complet de classes pour résoudre rapidement et efficacement les problèmes de programmation.  
  
-   **Sécurité améliorée.** Le code managé s'exécute dans un environnement CLR, hébergé par le moteur de base de données. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] met celui-ci à profit pour fournir une alternative plus sûre et plus sécurisée aux procédures stockées étendues disponibles dans les versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   **Possibilité de définir des types de données et des fonctions d'agrégation.** Les types et les agrégats définis par l'utilisateur sont deux nouveaux objets de base de données managés qui étendent les fonctions de stockage et d'interrogation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   **Développement simplifié via un environnement standardisé.** Le développement de bases de données est intégré aux prochaines versions de l'environnement de développement  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio .NET. Les développeurs se servent des mêmes outils pour développer et déboguer les objets de base de données et les scripts que ceux qu'ils utilisent pour écrire des composants et services .NET Framework de couche intermédiaire ou client.  
  
-   **Potentiel pour des performances et une extensibilité améliorées.** Dans de nombreux cas, la compilation du langage .NET Framework et les modèles d'exécution offrent des performances améliorées par rapport à Transact-SQL.  
  
 Le tableau ci-dessous répertorie les rubriques de cette section.  
  
 [Vue d'ensemble de l'intégration du CLR](clr-integration-overview.md)  
 Décrit les types d'objets qui peuvent être créés à l'aide de l'intégration du CLR et passe en revue les spécifications requises pour générer des objets de base de données à l'aide de l'intégration du CLR.  
  
 [Nouveautés dans l'intégration du CLR](clr-integration-what-s-new.md)  
 Décrit les nouvelles fonctionnalités de cette version.  
  
 [Architecture d'intégration du CLR](../../database-engine/dev-guide/architecture-of-clr-integration.md)  
 Décrit les objectifs de conception de l'intégration du CLR.  
  
 [Activation de l'intégration du CLR](clr-integration-enabling.md)  
 Décrit comment activer l'intégration du CLR.  
  
## <a name="see-also"></a>Voir aussi  
 [Installation du .NET Framework](https://technet.microsoft.com/library/ms166014\(v=SQL.105\).aspx)   
 [Performances de l'intégration du CLR](clr-integration-architecture-performance.md)  
  
  
