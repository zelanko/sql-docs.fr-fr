---
title: Options (requête résultats de SQL Server--multiserveur) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.sqleditors.multiserverresultssettings
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLMultiServerResults
ms.assetid: d6768bd8-9cb5-4606-a726-a33a1df9e1bb
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a1465defc783d0fde352a29648af61c0bb99ff59
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043205"
---
# <a name="options-query-results-sql-server-multi-server"></a>Options (requête SQL de résultats multiples-serveur)
  Lorsque vous interrogez plusieurs serveurs en même temps, utilisez cette page pour spécifier les options d'affichage des jeux de résultats. Les résultats de fusion combinent les jeux de résultats provenant de tous les serveurs en un jeu de résultats unique. Lors de la fusion de résultats, le premier serveur à répondre définit le schéma pour le jeu de résultats. Pour fusionner les jeux de résultats, la requête doit retourner le même nombre de colonnes avec les mêmes noms de colonnes à partir de chaque serveur. Lors de la fusion de résultats, un message s'affiche pour chaque serveur qui ne correspond pas au schéma (nombre de colonnes et noms des colonnes) retourné par le premier serveur ayant retourné des résultats.  
  
 Lorsque vous ne fusionnez pas de résultats, le jeu de résultats de chaque serveur est affiché dans sa propre grille avec son propre schéma.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Fusionner les résultats**  
 Activez cette case à cocher pour combiner les jeux de résultats de plusieurs serveurs dans la même grille.  
  
 **Ajouter le nom du serveur aux résultats**  
 Activez cette case à cocher pour inclure une colonne supplémentaire qui indique le nom du serveur ayant produit chaque ligne.  
  
 **Ajouter le nom de connexion aux résultats**  
 Activez cette case à cocher pour inclure une colonne supplémentaire qui indique la connexion utilisée pour se connecter au serveur ayant fourni chaque ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un serveur d’administration centrale et le groupe de serveurs &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)   
 [Exécuter des instructions simultanément sur plusieurs serveurs &#40;SQL Server Management Studio&#41;](../ssms/register-servers/execute-statements-against-multiple-servers-simultaneously.md)  
  
  