---
title: Moniteur d’activité | Microsoft Docs
ms.custom: ''
ms.date: 04/07/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server]
ms.assetid: 1e6c430d-3a2a-468e-a3d5-ef5459c36c15
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 45d2e41fa88d0ea586832ab91a927832b82ab0fa
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85787497"
---
# <a name="activity-monitor"></a>Moniteur d'activité
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
Le Moniteur d'activité affiche des informations sur les processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et sur la façon dont ces processus affectent l'instance actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Le moniteur d’activité est une fenêtre de document à onglets, qui comprend les volets extensibles et réductibles suivants : **Vue d’ensemble**, **Processus**, **Attentes de ressources**, **E/S du fichier de données**, **Requêtes coûteuses récentes** et **Requêtes coûteuses actives**. Lorsqu'un volet est développé, le Moniteur d'activité interroge l'instance pour obtenir des informations. Lorsqu'un volet est réduit, toutes les activités d'interrogation cessent pour ce volet. Vous pouvez développer en même temps un ou plusieurs volets pour afficher différents types d’activité sur l’instance.  
 
## <a name="customize-columns"></a>Personnaliser les colonnes 
Pour les colonnes incluses dans les volets **Processus**, **Attentes de ressources**, **E/S du fichier de données** et **Requêtes coûteuses récentes** et **Requêtes coûteuses actives**, personnalisez l’affichage comme suit :  
  
1.  Pour réorganiser l’ordre des colonnes, cliquez sur l’en-tête de colonne et faites-le glisser vers un autre emplacement dans le ruban de titre.  
  
2.  Pour trier une colonne, cliquez sur son nom.  
  
3.  Pour effectuer un filtrage sur une ou plusieurs colonnes, cliquez sur la flèche de déroulement de l'en-tête de colonne, puis sélectionnez une valeur.  

## <a name="more-information"></a>Informations complémentaires  
   
|||  
|-|-|  
|Décrit comment ouvrir le Moniteur d'activité et définir son intervalle d'actualisation.|[Ouvrir le Moniteur d’activité &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)|  
|Liens vers des rubriques relatives à la surveillance des performances et de l'activité du serveur.|[Analyse des performances et surveillance de l'activité du serveur](../../relational-databases/performance/server-performance-and-activity-monitoring.md)|  
  
  
