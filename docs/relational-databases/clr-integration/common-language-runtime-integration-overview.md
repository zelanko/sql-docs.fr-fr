---
title: Présentation de l’intégration de Common Language Runtime (CLR) | Microsoft Docs
ms.custom: ''
ms.date: 06/20/2017
ms.prod: sql
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
ms.openlocfilehash: 922489d1145204a4ae5d2dcf8e483149f1b11bcf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68068463"
---
# <a name="common-language-runtime-integration"></a>Intégration du Common Language Runtime
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-index) vous permettent d’implémenter certaines des fonctionnalités à l’aide des langages .net à l’aide de l’intégration du common language runtime (CLR) natif en tant que modules SQL Server côté serveur (procédures, fonctions et déclencheurs). Le CLR fournit le code managé avec des services tels que l'intégration interlangage, la sécurité d'accès du code, la gestion de la durée de vie des objets et la prise en charge du débogage et des profils. Pour les utilisateurs et les développeurs d'applications [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'intégration du CLR permet désormais d'écrire des procédures stockées, des déclencheurs, des types définis par l'utilisateur, des fonctions définies par l'utilisateur (fonctions scalaires et fonctions table) et des fonctions d'agrégation définies par l'utilisateur, à l'aide de langages du .NET Framework, tels que [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inclut la version 4 préinstallée du .NET Framework.  

> [!WARNING]
>  CLR utilise la sécurité d’accès du code (CAS) dans le .NET Framework, qui n’est plus pris en charge comme limite de sécurité. Un assembly CLR créé avec `PERMISSION_SET = SAFE` peut être en mesure d’accéder à des ressources système externes, d’appeler du code non managé et d’acquérir des privilèges sysadmin. À compter de [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)], une option de `sp_configure` appelée `clr strict security` est introduite pour renforcer la sécurité des assemblys CLR. `clr strict security` est activée par défaut et traite les assemblys `SAFE` et `EXTERNAL_ACCESS` comme s’ils étaient marqués `UNSAFE`. L’option `clr strict security` peut être désactivée pour assurer une compatibilité descendante, mais ceci n’est pas recommandé. Microsoft recommande que tous les assemblys soient signés par un certificat ou une clé asymétrique avec une connexion correspondante à laquelle a été accordée l’autorisation `UNSAFE ASSEMBLY` dans la base de données master. Pour plus d’informations, consultez [CLR strict security](../../database-engine/configure-windows/clr-strict-security.md). Les administrateurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent également ajouter des assemblys à une liste d’assemblys, que le moteur de base de données doit approuver. Pour plus d’informations, consultez [sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md).

## <a name="when-to-use-clr-modules"></a>Quand utiliser des modules CLR ?

Intégration du CLR vous permet d’implémenter des fonctionnalités complexes qui sont disponibles dans .net Framework telles que les expressions régulières, de code pour accéder aux ressources externes (serveurs, services web, bases de données), chiffrement personnalisé, etc. Certains des avantages de l’intégration de CLR côté serveur sont :
  
-   **Un meilleur modèle de programmation.** Les langages .NET Framework sont à bien des égards plus riches que Transact-SQL, en proposant des constructions et des fonctions qui n'étaient pas jusque-là accessibles aux développeurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les développeurs peuvent aussi tirer parti de la puissance de la bibliothèque du .NET Framework, qui propose un ensemble complet de classes pour résoudre rapidement et efficacement les problèmes de programmation.  
  
-   **Sécurité améliorée et la sécurité.** Le code managé s'exécute dans un environnement CLR, hébergé par le moteur de base de données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] met celui-ci à profit pour fournir une alternative plus sûre et plus sécurisée aux procédures stockées étendues disponibles dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Possibilité de définir des types de données et les fonctions d’agrégation.** Les types et les agrégats définis par l'utilisateur sont deux nouveaux objets de base de données managés qui étendent les fonctions de stockage et d'interrogation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Développement simplifié via un environnement standardisé.** Le développement de bases de données est intégré aux prochaines versions de l'environnement de développement  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio .NET. Les développeurs se servent des mêmes outils pour développer et déboguer les objets de base de données et les scripts que ceux qu'ils utilisent pour écrire des composants et services .NET Framework de couche intermédiaire ou client.  
  
-   **Potentiel pour améliorer les performances et évolutivité.** Dans de nombreux cas, la compilation du langage .NET Framework et les modèles d'exécution offrent des performances améliorées par rapport à Transact-SQL.  
  
 Le tableau ci-dessous répertorie les rubriques de cette section.  
  
 [Vue d’ensemble de l’intégration du CLR](../../relational-databases/clr-integration/clr-integration-overview.md)  
 Décrit les types d'objets qui peuvent être créés à l'aide de l'intégration du CLR et passe en revue les spécifications requises pour générer des objets de base de données à l'aide de l'intégration du CLR.  
  
 [Nouveautés de l’intégration du CLR](../../relational-databases/clr-integration/clr-integration-what-s-new.md)  
 Décrit les nouvelles fonctionnalités de cette version.  
  
 [Architecture d’intégration du CLR](https://msdn.microsoft.com/library/05e4b872-3d21-46de-b4d5-739b5f2a0cf9)  
 Décrit les objectifs de conception de l'intégration du CLR.  
  
 [Activation de l’intégration du CLR](../../relational-databases/clr-integration/clr-integration-enabling.md)  
 Décrit comment activer l'intégration du CLR.  
  
## <a name="see-also"></a>Voir aussi  
 [Installation du .NET Framework](https://technet.microsoft.com/library/ms166014\(v=SQL.105\).aspx) ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uniquement)   
 [Performances de l’intégration du CLR](../../relational-databases/clr-integration/clr-integration-architecture-performance.md)  
  
  
