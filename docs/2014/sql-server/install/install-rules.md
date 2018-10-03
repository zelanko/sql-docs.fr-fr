---
title: Règles d’installation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
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
ms.openlocfilehash: 6105444259697caa655145c40f795469a9b6304f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48127425"
---
# <a name="install-rules"></a>Règles d'installation
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le programme d’installation valide la configuration de votre ordinateur avant la fin de l’opération d’installation. Lors de l'exécution du programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , l'outil d'analyse de configuration système (SCC) analyse l'ordinateur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sera installé. L'outil SCC recherche toute anomalie susceptible d'empêcher une installation correcte de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Avant que le programme d'installation ne démarre l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le SCC extrait l'état de chaque élément. Puis, il compare le résultat avec les conditions requises et fournit une aide pour la suppression des problèmes importants.  
  
 La vérification de la configuration du système génère un rapport qui contient une brève description de chaque règle exécutée et de l'état d'exécution. Le rapport d’analyse de configuration système se trouve dans % ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< aaaammjj_hhmm >\\.  
  
 Avant d'exécuter l'opération d'installation, examinez les rubriques suivantes :  
  
1.  [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [Considérations sur la sécurité pour une installation SQL Server](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [Versions linguistiques locales dans SQL Server](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 Autres références :  
  
1.  [Mises à niveau de la version et de l’édition prises en charge](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [Avant l'installation du clustering de basculement](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="additional-rule-topics"></a>Rubriques supplémentaires relatives aux règles  
 Consultez les rubriques suivantes pour des règles d'installation spécifiques au scénario :  
  
-   [Règles d’installation](../../../2014/sql-server/install/installation-rules.md)  
  
-   [Fonctionnalité des règles &#40;mise à niveau&#41;](../../../2014/sql-server/install/feature-rules-upgrade.md)  
  
-   [Règles de mise à niveau d’édition](../../../2014/sql-server/install/edition-upgrade-rules.md)  
  
-   [Règles de désinstallation](../../../2014/sql-server/install/uninstallation-rules.md)  
  
-   [Règles de préparation d’image](../../../2014/sql-server/install/prepare-image-rules.md)  
  
-   [Règles de finalisation d’image](../../../2014/sql-server/install/complete-image-rules.md)  
  
  
