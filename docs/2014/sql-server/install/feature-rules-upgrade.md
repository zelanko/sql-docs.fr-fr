---
title: Fonctionnalité des règles (mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 653b15db-a984-4b4b-b224-81b0285b099b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 998ff700a63274c2a57f7e3dc9d6981b2e43bb53
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48193106"
---
# <a name="feature-rules-upgrade"></a>Règles de fonctionnalité (mise à niveau)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le programme d’installation valide la configuration de votre ordinateur avant la fin de l’opération d’installation. Pendant l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le système analyse l'ordinateur où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sera installé et vérifie les conditions qui empêchent une installation réussie de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Avant que le programme d'installation ne démarre l'Assistant Mise à niveau, il extrait l'état de chaque élément. Puis, il compare le résultat avec les conditions requises et fournit une aide pour la suppression des problèmes importants.  
  
 La vérification de la configuration du système génère un rapport qui contient une brève description de chaque règle exécutée et de l'état d'exécution. Le rapport d’analyse de configuration système se trouve dans % ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< aaaammjj_hhmm >\\.  
  
 Avant d'exécuter l'opération d'installation, examinez les rubriques suivantes :  
  
1.  [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [Considérations sur la sécurité pour une installation SQL Server](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [Versions linguistiques locales dans SQL Server](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 Autres références :  
  
1.  [Mises à niveau de la version et de l’édition prises en charge](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [Avant l'installation du clustering de basculement](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Règles d’installation](../../../2014/sql-server/install/install-rules.md)  
  
  
