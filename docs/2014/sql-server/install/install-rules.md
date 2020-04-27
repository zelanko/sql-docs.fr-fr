---
title: Règles d’installation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SCC
- System Configuration Check, Setup
helpviewer_keywords:
- System Configuration Check page [SQL Server Installation Wizard]
- SQL Server Installation Wizard, System Configuration Check page
- SCC [SQL Server]
ms.assetid: 168c0445-5651-42fc-91f4-d9f27d9e2281
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fa3cbb7b78577bc1fd01115ddae792efa1d8fc92
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66094479"
---
# <a name="install-rules"></a>Règles d'installation
  Le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide la configuration de votre ordinateur avant la fin de l'opération d'installation. Lors de l'exécution du programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , l'outil d'analyse de configuration système (SCC) analyse l'ordinateur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sera installé. L'outil SCC recherche toute anomalie susceptible d'empêcher une installation correcte de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Avant que le programme d'installation ne démarre l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le SCC extrait l'état de chaque élément. Puis, il compare le résultat avec les conditions requises et fournit une aide pour la suppression des problèmes importants.  
  
 La vérification de la configuration du système génère un rapport qui contient une brève description de chaque règle exécutée et de l'état d'exécution. Le rapport d’analyse de la configuration système se trouve à\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]l’emplacement\\ % ProgramFiles% \\\120\Setup Bootstrap\Log<YYYYMMDD_HHMM>.  
  
 Avant d'exécuter l'opération d'installation, examinez les rubriques suivantes :  
  
1.  [Configuration matérielle et logicielle requise pour l’installation de SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [Considérations sur la sécurité pour une installation SQL Server](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [Versions linguistiques locales dans SQL Server](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 Autres références :  
  
1.  [Mises à niveau de la version et de l’édition prises en charge](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [Avant l'installation du clustering de basculement](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="additional-rule-topics"></a>Rubriques supplémentaires relatives aux règles  
 Consultez les rubriques suivantes pour des règles d'installation spécifiques au scénario :  
  
-   [Règles d'installation](../../../2014/sql-server/install/installation-rules.md)  
  
-   [Règles de fonctionnalité &#40;mettre à niveau&#41;](../../../2014/sql-server/install/feature-rules-upgrade.md)  
  
-   [Règles de mise à niveau de l'édition](../../../2014/sql-server/install/edition-upgrade-rules.md)  
  
-   [Règles de désinstallation](../../../2014/sql-server/install/uninstallation-rules.md)  
  
-   [Règles de préparation d'image](../../../2014/sql-server/install/prepare-image-rules.md)  
  
-   [Règles de finalisation d'image](../../../2014/sql-server/install/complete-image-rules.md)  
  
  
