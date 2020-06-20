---
title: Options (résultats de la requête-SQL Server-multi-serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqleditors.multiserverresultssettings
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLMultiServerResults
ms.assetid: d6768bd8-9cb5-4606-a726-a33a1df9e1bb
author: rothja
ms.author: jroth
ms.openlocfilehash: 8273ad5edc65dd7351533209e9fa670c49f75f7a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84929980"
---
# <a name="options-query-results-sql-server-multi-server"></a>Options (Résultats de la requête/SQL Server/Multiserveur)
  Lorsque vous interrogez plusieurs serveurs en même temps, utilisez cette page pour spécifier les options d'affichage des jeux de résultats. Les résultats de fusion combinent les jeux de résultats provenant de tous les serveurs en un jeu de résultats unique. Lors de la fusion de résultats, le premier serveur à répondre définit le schéma pour le jeu de résultats. Pour fusionner les jeux de résultats, la requête doit retourner le même nombre de colonnes avec les mêmes noms de colonnes à partir de chaque serveur. Lors de la fusion de résultats, un message s'affiche pour chaque serveur qui ne correspond pas au schéma (nombre de colonnes et noms des colonnes) retourné par le premier serveur ayant retourné des résultats.  
  
 Lorsque vous ne fusionnez pas de résultats, le jeu de résultats de chaque serveur est affiché dans sa propre grille avec son propre schéma.  
  
## <a name="ui-element-list"></a>Liste des éléments d’interface utilisateur  
 **Fusionner les résultats**  
 Activez cette case à cocher pour combiner les jeux de résultats de plusieurs serveurs dans la même grille.  
  
 **Ajouter le nom de serveur aux résultats**  
 Activez cette case à cocher pour inclure une colonne supplémentaire qui indique le nom du serveur ayant produit chaque ligne.  
  
 **Ajouter le nom de connexion aux résultats**  
 Activez cette case à cocher pour inclure une colonne supplémentaire qui indique la connexion utilisée pour se connecter au serveur ayant fourni chaque ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un serveur de gestion centralisée et un groupe de serveurs &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)   
 [Exécuter des instructions simultanément sur plusieurs serveurs &#40;SQL Server Management Studio&#41;](../ssms/register-servers/execute-statements-against-multiple-servers-simultaneously.md)  
  
  
