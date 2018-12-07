---
title: Analyser un plan d’exécution réel | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- analyzing execution plans
- analyzing actual execution plans
- execution plans [SQL Server], analyzing
ms.assetid: 9e583a18-5f4a-4054-bfe1-4b2a76630db6
author: pmasl
ms.author: pelopes
manager: amitban
ms.openlocfilehash: e0f23ceb75856db921e4c6303a8013d351f364e8
ms.sourcegitcommit: 60739bcb48ccce17bca4e11a85df443e93ca23e3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52439911"
---
# <a name="analyze-an-actual-execution-plan"></a>Analyser un plan d’exécution réel
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Cette rubrique explique comment analyser des plans d’exécution graphiques réels à l’aide de la fonctionnalité d’analyse de plan de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

> [!NOTE]
> Les plans d’exécution réels sont générés une fois que les requêtes ou les lots [!INCLUDE[tsql](../../includes/tsql-md.md)] ont été exécutés. Pour cette raison, un plan d’exécution réel contient des informations d’exécution, comme la quantité réelle de lignes, les avertissements d’exécution (s’il y en a) et les métriques d’utilisation des ressources. Pour plus d’informations, consultez [Afficher un plan d’exécution réel](../../relational-databases/performance/display-an-actual-execution-plan.md).
  
Le dépannage des performances de requêtes nécessite une réelle expertise en ce qui concerne les plans d’exécution et le traitement des requêtes, afin d’être en mesure de trouver et de corriger les causes racines.

[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] inclut une fonctionnalité qui implémente un certain degré d’automatisation dans la tâche d’analyse de plan d’exécution réel, en particulier pour les plans volumineux et complexes. L’objectif est de faciliter l’identification des scénarios d’[Estimation de cardinalité](../../relational-databases/performance/cardinality-estimation-sql-server.md) inexacte, et d’obtenir des recommandations concernant les solutions d’atténuation disponibles.

> [!IMPORTANT]
> Veillez à effectuer des tests appropriés des solutions d’atténuation proposées avant de les appliquer dans des environnements de production.
  
## <a name="to-analyze-an-execution-plan-for-a-query"></a>Pour analyser un plan d’exécution pour une requête  
  
1.  Ouvrez un fichier de plan d’exécution de requête précédemment enregistré (.sqlplan) en cliquant sur **Ouvrir un fichier** dans le menu **Fichier**, ou en faisant glisser un fichier de plan vers la fenêtre [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)]. En guise d’alternative, si vous venez d’exécuter une requête et que vous avez choisi d’afficher son plan d’exécution, accédez à l’onglet **Plan d’exécution** dans le volet de résultats. 

2.  Cliquez avec le bouton droit dans une zone vide du plan d’exécution et cliquez sur **Analyser le plan d’exécution réel**. 

    ![Cliquez avec le bouton droit sur Analyser le plan d’exécution réel](../../relational-databases/performance/media/plananalysismenuoption.png "Cliquez avec le bouton droit sur Analyser le plan d’exécution réel")   

3.  La fenêtre **Analyse du plan d’exécution de requêtes** s’ouvre dans la partie inférieure. L’onglet **Instructions multiples** est utile lors de l’analyse des plans comprenant plusieurs instructions, car il permet d’analyser la bonne instruction.

4.  Sélectionnez l’onglet Scénarios pour afficher des détails sur les problèmes détectés pour le plan d’exécution réel. Pour chaque opérateur listé dans le volet gauche, le volet droit affiche des détails sur le scénario dans le lien *Cliquez ici pour plus d’informations sur ce scénario*, et les raisons possibles pouvant expliquer ce scénario sont listées.

    ![Résultats de l’analyse du plan d’exécution](../../relational-databases/performance/media/plananalysis-scenarios.png "Résultats de l’analyse du plan d’exécution") 
