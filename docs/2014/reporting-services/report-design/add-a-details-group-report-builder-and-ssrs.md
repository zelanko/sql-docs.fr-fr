---
title: Ajouter un groupe de détails (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ef8efba-6d48-4aeb-a3b9-a02ba5a44614
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fe6fffc96a816c9b71c003926d6267e8287a1c48
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66106857"
---
# <a name="add-a-details-group-report-builder-and-ssrs"></a>Ajouter un groupe de détails (Générateur de rapports et SSRS)
  Les données de détail d'un dataset de rapport sont spécifiées en tant que groupe sans expression de groupe. Ajoutez un groupe de détails à une région de données de tableau matriciel existante lorsque vous souhaitez afficher les données de détail d'une matrice, rajouter des données de détail que vous avez supprimées d'une table ou d'une liste ou ajouter d'autres groupes de détails. Pour plus d’informations sur les groupes, consultez [Fonctionnement des groupes &#40;Générateur de rapports et SSRS&#41;](understanding-groups-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-details-group-to-a-tablix-data-region"></a>Pour ajouter un groupe de détails à une région de données de tableau matriciel  
  
1.  Sur l'aire de conception, cliquez n'importe où dans une région de données de tableau matriciel pour la sélectionner. Le volet Regroupement affiche les groupes de lignes et de colonnes de la région de données sélectionnée.  
  
2.  Dans le volet Regroupement, cliquez avec le bouton droit sur un groupe correspondant à un groupe enfant des plus profonds. Cliquez sur **Ajouter un groupe**, puis sur **Groupe enfant**. La boîte de dialogue **Groupe de tableaux matriciels** s'affiche.  
  
3.  Dans **Expression Groupe**, laissez l'expression vide. Un groupe de détails ne possède aucune expression.  
  
4.  Sélectionnez **Afficher les données de détail**.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Un nouveau groupe de détails est ajouté en tant que groupe enfant dans le volet Regroupement et le descripteur de ligne du groupe que vous avez sélectionné au cours de l'étape 1 affiche l'icône du groupe de détails. Pour plus d’informations sur les descripteurs, consultez [Cellules, lignes et colonnes de région de données de tableau matriciel &#40;Générateur de rapports et SSRS&#41;](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter ou supprimer un groupe dans une région de données &#40;Générateur de rapports et SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)   
 [Fonctionnement des groupes &#40;Générateur de rapports et SSRS&#41;](understanding-groups-report-builder-and-ssrs.md)   
 [Région de données de tableau matriciel &#40;Générateur de rapports et SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Tables &#40;Générateur de rapports et SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [Matrices &#40;Générateur de rapports et SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [Listes &#40;Générateur de rapports et SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Tables, matrices et listes &#40;Générateur de rapports et SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
