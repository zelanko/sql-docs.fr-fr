---
title: Ajouter le nœud de Cluster de basculement SQL Server | Documents Microsoft
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e5035122-784f-40ee-8188-7f485a9ae3e8
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f1acda3ae51a6b248347defad1c2cad1d022ac9a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140219"
---
# <a name="add-sql-server-failover-cluster-node"></a>Ajouter un nœud de cluster de basculement SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le programme d’installation valide la configuration de votre ordinateur avant la fin de l’opération d’installation. Lors de l'exécution du programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , l'outil d'analyse de configuration système (SCC) analyse l'ordinateur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sera installé. L'outil SCC recherche toute anomalie susceptible d'empêcher une installation correcte de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Avant que le programme d'installation ne démarre l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le SCC extrait l'état de chaque élément. Puis, il compare le résultat avec les conditions requises et fournit une aide pour la suppression des problèmes importants.  
  
 La vérification de la configuration du système génère un rapport qui contient une brève description de chaque règle exécutée et de l'état d'exécution. Le rapport d’analyse de configuration système se trouve sous %programfiles%\Microsoft SQL Server\120\Setup Bootstrap\Log\\< aaaammjj_hhmm >\\.  
  
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
  
  