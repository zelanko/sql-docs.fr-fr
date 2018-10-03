---
title: Explorer les données dans une vue de Source de données (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- exploring data [Analysis Services]
- data source views [Analysis Services], exploring data
- viewing source data
ms.assetid: 2c922c35-fbcb-45b2-96b1-c7a846d8b419
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f02ffda65cfd981f84a41f62ed310a06b8dfbd63
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48094901"
---
# <a name="explore-data-in-a-data-source-view-analysis-services"></a>Explorer des données dans une vue de source de données (Analysis Services)
  Vous pouvez utiliser la boîte de dialogue **Explorer les données** du Concepteur de vue de source de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pour parcourir les données d’une table, d’une vue ou d’une requête nommée dans une vue de source de données (DSV). Si vous explorez les données dans le Concepteur de vue de source de données, vous pouvez afficher le contenu de chacune des colonnes de données d'une table, d'une vue ou d'une requête nommée sélectionnée. Cet affichage vous permet de déterminer si toutes les colonnes sont nécessaires, si des calculs nommés sont nécessaires pour améliorer la convivialité, et si les requêtes nommées ou les calculs nommés existants retournent les valeurs prévues.  
  
 Pour afficher les données, vous devez disposer d'une connexion active aux sources de données pour l'objet sélectionné dans la vue de source de données (DSV). Le cas échéant, tous les calculs nommés d'une table sont également envoyés dans la requête.  
  
 Données retournées dans un format tabulaire que vous pouvez trier et copier. Cliquez sur les en-têtes de colonnes pour re-trier les lignes par cette colonne. Vous pouvez également mettre en surbrillance des données dans la grille et appuyer sur Ctrl+C pour copier la sélection dans le presse-papiers.  
  
 Vous pouvez également contrôler la méthode d'échantillonnage et le nombre d'échantillons. Par défaut, les 5000 premières lignes sont retournées.  
  
## <a name="to-browse-data-or-change-sampling-options"></a>Pour parcourir les données ou modifier les options d'échantillonnage  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet ou connectez-vous à la base de données qui contient la vue de source de données dans laquelle vous souhaitez explorer les données.  
  
2.  Dans l’Explorateur de solutions, développez le dossier **Vues des sources de données** , puis double-cliquez sur la vue de source de données.  
  
3.  Cliquez avec le bouton droit sur la table, la vue ou la requête nommée contenant les données que vous voulez consulter, puis sélectionnez **Explorer les données**.  
  
     Les données source sous-jacente de la table, vue, ou requête nommée dans la vue de source de données sont des requêtes et les résultats s’affichent dans le **Explorer \<nom_objet > Table** onglet.  
  
4.  Sur le **Explorer \<nom_objet > Table** barre d’outils, cliquez sur le **options d’échantillonnage** icône.  
  
     La boîte de dialogue **Options d'exploration de données** s'ouvre. Dans cette boîte de dialogue, vous pouvez spécifier la méthode d’échantillonnage (et augmenter ou diminuer le nombre d’enregistrements par rapport à la taille d’échantillonnage par défaut de 5000 lignes) ou le nombre d’échantillons.  
  
5.  Selon le cas, cliquez sur **OK** ou sur **Annuler** .  
  
6.  Pour rééchantillonner les données, cliquez sur **Rééchantillonner des données** sur le **Explorer \<nom_objet > Table** barre d’outils.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de sources de données dans les modèles multidimensionnels](data-source-views-in-multidimensional-models.md)  
  
  
