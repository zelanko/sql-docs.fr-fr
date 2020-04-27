---
title: Récupérer à partir d’une défaillance d’instance de cluster de basculement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], recovery from failure
- failover clustering [SQL Server], recovery from failure
- hardware failures [SQL Server]
- recovering failover cluster failures [SQL Server]
ms.assetid: 3d151d0c-e841-4325-8606-c094de37d7d1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0c4da45e57342288cc23a9783709666f4c02d0bc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63050010"
---
# <a name="recover-from-failover-cluster-instance-failure"></a>Récupérer à partir d'une défaillance d'instance de cluster de basculement
  Cette rubrique explique comment récupérer des échecs de cluster à l'aide du composant logiciel enfichable Gestionnaire du cluster de basculement après un basculement dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Le composant logiciel enfichable Gestionnaire du cluster de basculement est l'application de gestion du service de cluster de basculement Windows Server (WSFC).  
  
-   [Récupération suite à une défaillance irréparable](#Scenario1)  
  
-   [Récupérer en cas d'erreur logicielle](#Scenario2)  
  
##  <a name="recover-from-an-irreparable-failure"></a><a name="Scenario1"></a> Récupérer en cas d'erreur irréparable  
 Utilisez les étapes suivantes pour récupérer une erreur irréparable. L'erreur peut être provoquée, par exemple, par la défaillance d'un contrôleur de disque ou du système d'exploitation. Dans ce cas, l'erreur est due à une défaillance matérielle dans le nœud 1 d'un cluster à deux nœuds.  
  
1.  Après la défaillance du nœud 1, la FCI de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bascule sur le nœud 2.  
  
2.  Supprimez le nœud 1 de la FCI. Pour cela, à partir du nœud 2, ouvrez le composant logiciel enfichable Gestionnaire du cluster de basculement, cliquez avec le bouton droit sur Node1, cliquez sur **Déplacer des actions**, puis sur **Supprimer le nœud**.  
  
3.  Assurez-vous que le nœud 1 a été supprimé de la définition de cluster.  
  
4.  Installez le nouveau matériel pour remplacer le matériel défaillant dans le nœud 1.  
  
5.  Ajoutez le nœud 1 au cluster existant à l'aide du composant logiciel enfichable Gestionnaire du cluster de basculement. Pour plus d’informations, consultez [Avant l’installation du clustering de basculement](../install/before-installing-failover-clustering.md).  
  
6.  Vérifiez que les comptes administrateurs sont bien les mêmes sur tous les nœuds de cluster.  
  
7.  Exécutez le programme d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] afin d'ajouter le nœud 1 à la FCI. Pour plus d’informations, consultez [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;d’installation&#41;](../install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
##  <a name="recover-from-a-reparable-failure"></a><a name="Scenario2"></a> Récupérer d'une erreur réparable  
 Utilisez les étapes suivantes pour récupérer suite à une erreur réparable. Dans ce cas, la défaillance est causée par le nœud 1, défectueux ou hors connexion, mais il n'est pas rompu de manière irrémédiable. Cette erreur peut être due à une défaillance du système d'exploitation, à une défaillance matérielle ou à une défaillance dans l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] elle-même.  
  
1.  Après la défaillance du nœud 1, la FCI bascule sur le nœud 2.  
  
2.  Résolvez le problème du nœud 1.  
  
3.  Vérifiez que le service WSFC fonctionne et que tous les nœuds sont en ligne.  
  
4.  Effectuez le basculement de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vers le nœud récupéré.  
  
  
