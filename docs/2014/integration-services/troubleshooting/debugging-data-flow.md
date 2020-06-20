---
title: Débogage d’un flux de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- progress reporting [Integration Services]
- data viewers [Integration Services]
- data flow [Integration Services], debugging
- debugging [Integration Services], data flow
- counting rows
ms.assetid: 1c574f1b-54f7-4c05-8e42-8620e2c1df0f
author: janinezhang
ms.author: janinez
ms.openlocfilehash: cc99e29d95aa08ce9363ca1fa6971d7602824868
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972760"
---
# <a name="debugging-data-flow"></a>Débogage d'un flux de données
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] incluent des fonctionnalités et des outils permettant de résoudre les problèmes des flux de données d’un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   [!INCLUDE[ssIS](../../includes/ssis-md.md)] - Le concepteur SSIS fournit des visionneuses de données.  
  
-   [!INCLUDE[ssIS](../../includes/ssis-md.md)] - Le concepteur SSIS et les transformations [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] fournissent des nombres de lignes.  
  
-   [!INCLUDE[ssIS](../../includes/ssis-md.md)] - Le concepteur SSIS fournit des rapports de progression au moment de l’exécution.  
  
## <a name="data-viewers"></a>Visionneuses de données  
 Les visionneuses de données affichent les données entre deux composants d'un flux de données. Elles permettent d'afficher les données lorsque celles-ci sont extraites d'une source de données et intègrent pour la première fois un flux de données, avant et après la mise à jour des données par une transformation et avant le chargement des données dans leur destination.  
  
 Pour afficher les données, vous devez attacher des visionneuses au chemin d'accès qui connecte deux composants de flux de données. Le fait de pouvoir afficher les données entre deux composants de flux de données facilite l'identification des valeurs de données inattendues, permet de voir les modifications apportées par une transformation aux valeurs des colonnes et permet de découvrir la raison pour laquelle une transformation échoue. Par exemple, si vous découvrez qu'une recherche dans une table de référence échoue et que vous souhaitez corriger cette erreur, vous voudrez peut-être ajouter une transformation qui fournit des données par défaut pour les colonnes vides.  
  
 Une visionneuse de données peut afficher des données dans une grille. Dans une grille, vous sélectionnez les colonnes à afficher. Les valeurs des colonnes sélectionnées s'affichent sous forme de tableau.  
  
 Vous pouvez également inclure plusieurs visionneuses de données dans un chemin d'accès. Vous pouvez afficher les mêmes données dans différents formats ; par exemple créer un graphique et une grille des données, ou créer des visionneuses de données distinctes pour différentes colonnes de données.  
  
 Quand vous ajoutez une visionneuse de données à un chemin, le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ajoute une icône de visionneuse de données sur l’aire de conception de l’onglet **Flux de données** , en regard du chemin. Les transformations acceptant les sorties multiples (telles que la transformation de fractionnement conditionnel) peuvent inclure une visionneuse de données sur chaque chemin d'accès.  
  
 Au moment de l’exécution, une fenêtre **Visionneuse de données** s’ouvre et affiche les informations spécifiées par le format de la visionneuse de données. Par exemple, une visionneuse de données qui utilise le format de grille affiche les données des colonnes sélectionnées, le nombre de lignes de sortie transmises au composant du flux de données et le nombre de lignes affichées. Ces informations s'affichent tampon par tampon et, selon la largeur des lignes dans le flux de données, un tampon peut contenir plus ou moins de lignes.  
  
 Dans la boîte de dialogue **Visionneuse de données** , vous pouvez copier les données dans le Presse-papiers, effacer toutes les données de la table, reconfigurer la visionneuse de données, reprendre le flux de données, ainsi que détacher ou attacher la visionneuse de données.  
  
#### <a name="to-add-a-data-viewer"></a>Pour ajouter une visionneuse de données  
  
-   [Ajouter une visionneuse de données à un flux de données](../add-a-data-viewer-to-a-data-flow.md)  
  
## <a name="row-counts"></a>Nombres de lignes  
 Le nombre de lignes transférées via un chemin est affiché sur l’aire de conception de l’onglet **Flux de données** du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] en regard du chemin. Ce nombre est mis à jour régulièrement quand les données empruntent le chemin.  
  
 Vous pouvez également ajouter une transformation de nombre de lignes au flux de données pour capturer le nombre de lignes final dans une variable. Pour plus d’informations, voir [Row Count Transformation](../data-flow/transformations/row-count-transformation.md).  
  
## <a name="progress-reporting"></a>Rapport de progression  
 Quand vous exécutez un package, le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] indique la progression sur l’aire de conception de l’onglet **Flux de données** en affichant chaque composant du flux de données dans une couleur qui indique son état. Lorsque les composants commencent à effectuer leur travail, ils passent à la couleur jaune et une fois terminés, ils passent à la couleur verte. Une couleur rouge indique que le composant a échoué.  
  
 Le tableau suivant décrit les codes de couleur.  
  
|Couleur|Description|  
|-----------|-----------------|  
|Aucune couleur|En attente d'être appelé par le moteur de flux de données.|  
|Jaune|Exécution d'une transformation, extraction de données ou chargement de données en cours.|  
|Vert|Exécuté avec succès.|  
|rouge|Exécuté avec des erreurs.|  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de dépannage pour le développement des packages](troubleshooting-tools-for-package-development.md)  
  
  
