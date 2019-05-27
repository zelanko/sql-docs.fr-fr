---
title: Options de requête (Page texte) de résultats | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.text.f1
ms.assetid: fd2fb409-58f9-4ede-8349-ce007126b68d
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 8d96384a4a4f4adbb52855a45f1bc00d3aadd85d
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66088982"
---
# <a name="query-options-results-text-page"></a>Options de requête — Résultats de requête (page Texte)
  Utilisez cette page pour définir les options d'affichage d'un jeu de résultats de requête au format texte. Ses paramètres s'appliquent également lorsque **Résultats dans un fichier** est sélectionné.  
  
 **Format de sortie**  
 Par défaut, la sortie est affichée sous la forme de colonnes créées par le remplissage des résultats à l'aide d'espaces. Il est également possible de séparer les colonnes à l'aide de virgules, de tabulations ou d'espaces. Activez la case à cocher **Séparateur personnalisé** pour définir un autre **caractère de délimitation** dans la zone de même nom.  
  
 **Séparateur personnalisé**  
 Indiquez le caractère à utiliser pour séparer les colonnes. Cette option n'est disponible que lorsque la case à cocher **Séparateur personnalisé** est activée dans la zone **Format de sortie** .  
  
 **Inclure des en-têtes de colonne dans l'ensemble de résultats**  
 Désactivez cette case à cocher si vous ne voulez pas que chaque colonne soit étiquetée au moyen d'un titre de colonne.  
  
 **Défilement pendant réception des résultats**  
 Activez cette case à cocher pour cibler l'affichage sur les derniers enregistrements retournés au bas de la fenêtre. Désactivez-la pour cibler l'affichage sur les premières lignes retournées.  
  
 **Aligner les valeurs numériques à droite**  
 Activez cette case à cocher pour aligner les valeurs numériques à droite de la colonne. Cela peut faciliter l'analyse de nombres comportant un nombre de décimales invariable.  
  
 **Ignorer les résultats après l'exécution de la requête**  
 Libère de la mémoire en ignorant les résultats de la requête une fois ceux-ci affichés à l'écran.  
  
 **Afficher les résultats dans un onglet séparé**  
 Activez cette case à cocher pour afficher l'ensemble de résultats dans une nouvelle fenêtre de document, et non au bas de la fenêtre de document de la requête.  
  
 **Basculer vers l'onglet des résultats après l'exécution de la requête**  
 Cliquez sur cette option pour que l'affichage soit automatiquement ciblé sur l'ensemble de résultats.  
  
 **Nombre maximal de caractères affichés dans chaque colonne**  
 Cette valeur est par défaut 256. Augmentez cette valeur pour afficher des jeux de résultats plus grands sans les tronquer.  
  
 **Rétablir les valeurs par défaut**  
 Rétablit toutes les valeurs par défaut initiales des options de cette page.  
  
## <a name="saving-a-text-result-set-with-headers"></a>Enregistrement d'un ensemble de résultats sous la forme de texte avec des en-têtes  
 Pour enregistrer les résultats de la requête sous forme de fichier texte avec en-têtes, activez la case à cocher **Inclure des en-têtes de colonne dans l'ensemble de résultats** et spécifiez un format de sortie délimité. Le fichier de rapport contiendra alors des en-têtes si vous cliquez sur **Résultats dans un fichier** dans la barre d’outils ou si vous cliquez avec le bouton droit sur des résultats de requête et que vous cliquez sur **Enregistrer les résultats sous**, que vous tapez un nom de fichier, puis que vous cliquez sur **Enregistrer**.  
  
  
