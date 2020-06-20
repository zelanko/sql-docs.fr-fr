---
title: Détails de la liaison de table (boîte de dialogue source de partition) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitiontableselection.f1
ms.assetid: 67d05389-81ae-4a6b-947b-986d37ec72b1
author: minewiskan
ms.author: owend
ms.openlocfilehash: ca06f4267edd65885bf4fec1838ecc4360c304fd
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84940150"
---
# <a name="table-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a>Détails de la liaison de table (boîte de dialogue Source de partition) (Analysis Services - Données multidimensionnelles)
  Utilisez l'option **Liaison de table** de la boîte de dialogue **Source de la partition** pour définir la table de faits qui fournit les données de la partition. Vous pouvez afficher ce volet en sélectionnant **Liaison de table** dans l'option **Type de liaison** de la boîte de dialogue **Source de la partition** .  
  
## <a name="options"></a>Options  
 **Groupe de mesures**  
 Affiche le groupe de mesures de la partition.  
  
 **Chercher dans**  
 Permet d'indiquer la source de données ou la vue de source de données contenant les tables source destinées à cette partition. La vue de source de vue de données utilisée par le groupe de mesures sélectionné est sélectionnée par défaut.  
  
 **Filtrer les tables**  
 Permet d’entrer la chaîne utilisée pour restreindre les tables affichées dans **Tables disponibles**d’après leur nom.  
  
 **Rechercher des tables**  
 Permet d’actualiser la liste des tables répertoriées dans **Tables disponibles**, et d’affiner la liste d’après les critères d’une chaîne indiquée dans **Filtrer les tables**, le cas échéant.  
  
 **Tables disponibles**  
 Cliquez pour sélectionner la table à utiliser comme table source pour la partition.  
  
 Si aucun filtre n'est défini dans **Filtrer les tables**, toutes les tables dans la source de données ou la vue de source de données définie dans **Rechercher dans** , qui sont similaires, en terme de structure, à la table des faits utilisée par le groupe de mesures défini dans **Groupe de mesures** , sont affichées.  
  
 Si un filtre est défini dans **Filtrer les tables**, la liste est encore limitée en comparant le filtre aux noms de tables qui répondent aux critères ci-dessous. Ainsi, seules les tables contenant la chaîne spécifiée dans **Filtrer les tables** sont affichées.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue source de partition &#40;Analysis Services-données multidimensionnelles&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  
