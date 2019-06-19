---
title: Afficher un plan d’exécution réel | Microsoft Docs
ms.custom: ''
ms.date: 11/21/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- displaying execution plans
- actual execution plans
- viewing execution plans
- execution plans [SQL Server], displaying
ms.assetid: 9e583a18-5f4a-4054-bfe1-4b2a76630db6
author: julieMSFT
ms.author: jrasnick
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5a0954180b7fc0aa707c9c8175c872cda2298d9c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62652580"
---
# <a name="display-an-actual-execution-plan"></a>Afficher un plan d'exécution réel
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Cette rubrique explique comment générer des plans d'exécution graphiques réels à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Les plans d’exécution réels sont générés une fois que les requêtes ou les lots [!INCLUDE[tsql](../../includes/tsql-md.md)] ont été exécutés. Pour cette raison, un plan d’exécution réel contient des informations d’exécution, comme des avertissements d’exécution (s’il y en a) et des métriques d’utilisation des ressources réelles. Le plan d’exécution généré affiche le plan d’exécution réel que le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] a utilisé pour exécuter les requêtes.  
  
 Pour être en mesure d'utiliser cette fonction, les utilisateurs doivent bénéficier des autorisations permettant d'exécuter les requêtes [!INCLUDE[tsql](../../includes/tsql-md.md)] pour lesquelles un plan d'exécution graphique est actuellement généré. Qui plus est, les utilisateurs doivent se voir accorder l'autorisation SHOWPLAN pour toutes les bases de données référencées par la requête.  
  
## <a name="to-include-an-execution-plan-for-a-query-during-execution"></a>Pour inclure un plan d'exécution pour une requête durant l'exécution  
  
1.  Dans la barre d’outils [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , cliquez sur **Requête de moteur de base de données**. Vous pouvez également ouvrir une requête existante et afficher le plan d’exécution estimé en cliquant sur le bouton **Ouvrir un fichier** dans la barre d’outils puis en choisissant la requête existante. 
  
2.  Entrez la requête pour laquelle vous souhaitez afficher le plan d'exécution réel.  
  
3.  Dans le menu **Requête**, cliquez sur **Inclure le plan d’exécution réel** ou cliquez sur le bouton de la barre d’outils **Inclure le plan d’exécution réel**.

    ![Bouton Plan d’exécution réel dans la barre d’outils](../../relational-databases/performance/media/actualexecplantoolbar.png "Bouton Plan d’exécution réel dans la barre d’outils")   
  
4.  Exécutez la requête en cliquant sur le bouton de la barre d’outils **Exécuter** . Le plan utilisé par l’optimiseur de requête est affiché sous l’onglet **Plan d’exécution** dans le volet de résultats. 

    ![Plan d’exécution réel](../../relational-databases/performance/media/actualexecplan.png "Plan d’exécution réel")   

5.  Placez la souris sur les opérateurs logiques et physiques pour afficher la description et les propriétés des opérateurs dans l’info-bulle affichée, notamment les propriétés du plan d’exécution global, en sélectionnant l’opérateur de nœud racine (le nœud SELECT dans l’image ci-dessus).   
  
    Il est également possible d'afficher les propriétés des opérateurs dans la fenêtre Propriétés. Si les propriétés ne sont pas visibles, cliquez avec le bouton droit sur un opérateur, puis cliquez sur **Propriétés**. Sélectionnez l'opérateur de votre choix.  

    ![Cliquez avec le bouton droit sur Propriétés dans l’opérateur de plan](../../relational-databases/performance/media/planproperties.png "Cliquez avec le bouton droit sur Propriétés dans l’opérateur de plan")    
  
6.  Si vous voulez modifier l’affichage du plan d’exécution, cliquez avec le bouton droit sur le plan d’exécution et sélectionnez **Zoom avant**, **Zoom arrière**, **Zoom personnalisé**ou **Zoom pour ajuster**. Les options**Zoom avant** et **Zoom arrière** vous permettent d’effectuer un zoom avant ou arrière sur le plan d’exécution. Quant à l’option **Zoom personnalisé** , elle vous permet de définir votre propre zoom, par exemple, un pourcentage de zoom de 80. Enfin, l’option**Zoom pour ajuster** agrandit le plan de sorte que sa taille soit ajustée en fonction de celle du volet de résultats. Vous pouvez également utiliser une combinaison de la touche Ctrl et de la roulette de votre souris pour activer le **zoom dynamique**.  

7.  Pour naviguer dans l’affichage du plan d’exécution, utilisez les barres de défilement horizontale et verticale, ou **cliquez sur une zone vide** du plan d’exécution et maintenez le bouton de la souris enfoncé, puis **faites glisser la souris**. Vous pouvez également cliquer sur le signe plus (+) dans le coin inférieur droit de la fenêtre du plan d’exécution et maintenir le bouton de la souris enfoncé pour afficher une carte miniature du plan d’exécution complet.

> [!NOTE] 
> Vous pouvez également utiliser [SET STATISTICS XML](../../t-sql/statements/set-statistics-xml-transact-sql.md) pour retourner les informations du plan d’exécution pour chaque instruction après l’avoir exécuté. En cas d’utilisation dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], l’onglet *Résultats* contient un lien pour ouvrir le plan d’exécution sous forme de graphique.   
> Pour plus d’informations, consultez [Infrastructure du profilage de requête](../../relational-databases/performance/query-profiling-infrastructure.md).
