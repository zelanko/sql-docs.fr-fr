---
title: Paramètres de l’outil d’analyse de configuration système | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing SQL Server, system configuration checks
- failed system configuration checks [SQL Server]
- verifying configuration before installation
- SCC [SQL Server]
- system configuration checker
- scanning computer before installation [SQL Server]
- checking configuration before installation
- status information [SQL Server], system configuration checker
- parameters [SQL Server], system configuration checker
- configuration checkers [SQL Server]
- Setup [SQL Server], system configuration checker
ms.assetid: 8e712c15-6bfa-4d71-b303-9526101e5594
caps.latest.revision: 44
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6385a1174bdb5d64279dfcee18e71343bc98a77d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152870"
---
# <a name="check-parameters-for-the-system-configuration-checker"></a>Paramètres de l'outil d'analyse de configuration système
  Lors de l'exécution du programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , l'outil d'analyse de configuration système (SCC) analyse l'ordinateur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sera installé. L'outil SCC recherche toute anomalie susceptible d'empêcher une installation correcte de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Avant que le programme d'installation ne démarre l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le SCC extrait l'état de chaque élément. Puis, il compare le résultat avec les conditions requises et fournit une aide pour la suppression des problèmes importants.  
  
 L'Outil d'analyse de configuration système génère un rapport qui contient une brève description de chaque règle exécutée et de l'état d'exécution. Le rapport d’analyse de configuration système se trouve à l’emplacement %ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< aaaammjj_hhmm >\\.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)   
 [Considérations sur la sécurité pour une installation SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   
 [Mises à niveau de la version et de l’édition prises en charge](supported-version-and-edition-upgrades.md)  
  
  