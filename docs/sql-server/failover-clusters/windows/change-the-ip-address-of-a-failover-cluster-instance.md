---
title: "Modifier l’adresse IP d’une instance de cluster de basculement | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying IP addresses
- failover clustering [SQL Server], IP addresses
- IP addresses [SQL Server]
- clusters [SQL Server], IP addresses
ms.assetid: b685f400-cbfe-4c5d-a070-227a1123dae4
caps.latest.revision: 33
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d30ca9ae2885d25bd0b62a17501ae7dfe94f26e9
ms.lasthandoff: 04/11/2017

---
# <a name="change-the-ip-address-of-a-failover-cluster-instance"></a>Modifier l'adresse IP d'une instance de cluster de basculement
  Cette rubrique explique comment modifier la ressource d’adresse IP d’une instance de cluster de basculement (FCI) Always On à l’aide du composant logiciel enfichable Gestionnaire du cluster de basculement. Le composant logiciel enfichable Gestionnaire du cluster de basculement est l'application de gestion du service de cluster de basculement Windows Server (WSFC).  
  
-   **Before you begin:**  [Security](#Security)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
 Avant de commencer, consultez la rubrique [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Avant l’installation du clustering de basculement [dans la documentation en ligne de](../../../sql-server/failover-clusters/install/before-installing-failover-clustering.md).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Pour maintenir ou mettre à jour une FCI, vous devez être un administrateur local et disposer des autorisations requises pour vous connecter en tant que service sur tous les nœuds de la FCI.  
  
##  <a name="WSFC"></a> Utilisation du composant logiciel enfichable Gestionnaire du cluster de basculement  
 **Pour modifier la ressource d'adresse IP pour une FCI**  
  
1.  Ouvrez le composant logiciel enfichable Gestionnaire du cluster de basculement.  
  
2.  Développez le nœud **Services et applications** dans le volet gauche et cliquez sur la FCI.  
  
3.  Dans le volet droit, sous la catégorie **Nom du serveur** , cliquez avec le bouton droit sur l’instance SQL Server et sélectionnez l’option **Propriétés** pour ouvrir la boîte de dialogue **Propriétés** .  
  
4.  Dans l'onglet **Général** , modifiez la ressource d'adresse IP.  
  
5.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
6.  Dans le volet droit, cliquez avec le bouton droit sur l’adresse IP SQL 1 (nom d’instance du cluster de basculement), puis sélectionnez **Mettre hors ligne**. Vous voyez l'adresse IP SQL 1 (nom d'instance du cluster de basculement), le nom de réseau SQL (nom d'instance du cluster de basculement), ainsi que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] passant de l'état Connecté à l'état Déconnexion en cours, puis à l'état Déconnecté.  
  
7.  Dans le volet droit, cliquez avec le bouton droit sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], puis sélectionnez **Mettre en ligne**. Vous voyez l'adresse IP SQL 1 (nom d'instance du cluster de basculement), le nom de réseau SQL (nom d'instance du cluster de basculement), ainsi que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] passant de l'état Déconnecté à l'état Connexion en cours, puis à l'état Connecté.  
  
8.  Fermez le composant logiciel enfichable Gestionnaire du cluster de basculement  
  
  
