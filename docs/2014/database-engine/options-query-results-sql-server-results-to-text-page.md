---
title: Options (résultats de SQL Server-résultats de la requête à la Page de texte) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLResultsToText
ms.assetid: 2ccbdf17-e14f-42f1-a836-ca999a3432c9
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 190d508cc4e1e637d95516a8c9daf148692aa2df
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053138"
---
# <a name="options-query-results-sql-server-results-to-text-page"></a>Options (résultats de SQL Server-résultats de la requête à la Page de texte)
  Utilisez cette page pour définir les options d'affichage d'un jeu de résultats de requête au format texte. Les modifications apportées à ces options sont appliquées uniquement aux nouvelles requêtes [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Pour que ces modifications s’appliquent aux requêtes en cours, cliquez sur **Options de requête** dans le menu **Requête** ou cliquez avec le bouton droit sur la fenêtre Requête [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et sélectionnez **Options de requête**. Dans la boîte de dialogue **Options de requête**, sous **Résultats**, cliquez sur **Texte**.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Format de sortie**  
 Par défaut, la sortie est affichée sous la forme de colonnes créées par le remplissage des résultats à l'aide d'espaces. Vous pouvez également utiliser des virgules, des tabulations ou des espaces pour séparer les colonnes. Sélectionnez **Délimiteur personnalisé** dans cette liste déroulante pour spécifier un autre séparateur dans la zone de texte **Délimiteur personnalisé**.  
  
 **Séparateur personnalisé**  
 Indiquez le caractère à utiliser pour séparer les colonnes. Cette zone de texte est disponible uniquement si vous avez cliqué sur Délimiteur personnalisé dans la zone de liste déroulante **Format de sortie**.  
  
 **Inclure des en-têtes de colonne dans le jeu de résultats**  
 Désactivez cette case à cocher si vous ne voulez pas que chaque colonne soit étiquetée au moyen d'un titre de colonne.  
  
 **Inclure la requête dans le jeu de résultats**  
 Activez cette case à cocher pour inclure le texte de la requête en cours d'exécution dans le volet de résultats avant les résultats de la requête.  
  
 **Défilement pendant réception des résultats**  
 Activez cette case à cocher pour suivre l'exécution de la requête et afficher les enregistrements les plus récents à la fin de l'ensemble de résultats. Désactivez-la pour cibler l'affichage sur les premières lignes retournées.  
  
 **Aligner les valeurs numériques à droite**  
 Activez cette case à cocher pour aligner les valeurs numériques à droite de la colonne. Cela peut faciliter l'analyse de nombres comportant un nombre de décimales invariable.  
  
 **Ignorer les résultats après l’exécution de requête**  
 Activez cette case à cocher pour ignorer les résultats de la requête une fois qu'ils sont affichés dans le volet de résultats de la fenêtre de la requête.  
  
 **Afficher les résultats dans un onglet séparé**  
 Activez cette case à cocher pour afficher l'ensemble de résultats dans une nouvelle fenêtre de document, et non au bas de la fenêtre de document de la requête.  
  
 **Basculer vers l’onglet des résultats après l’exécution de la requête**  
 Activez cette case à cocher pour afficher automatiquement l'ensemble de résultats à l'écran.  
  
 **Nombre maximal de caractères affichés dans chaque colonne**  
 Cette valeur est par défaut 256. Augmentez cette valeur pour afficher des jeux de résultats plus grands sans les tronquer. La valeur maximale est 8 192.  
  
 **Réinitialiser les valeurs par défaut**  
 Rétablit toutes les valeurs par défaut initiales des options de cette page.  
  
  