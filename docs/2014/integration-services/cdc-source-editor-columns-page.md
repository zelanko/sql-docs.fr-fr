---
title: Éditeur de Source CDC (Page colonnes) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.columns.f1
ms.assetid: bcf3030e-98d8-4445-967c-33c3f8ecb4fc
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 980b9cf22e2c50cd1de3eb90a06e6496c01cc093
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66061029"
---
# <a name="cdc-source-editor-columns-page"></a>Éditeur de source CDC (page Colonnes)
  Utilisez la page **Colonnes** de la boîte de dialogue **Éditeur de source CDC** pour mapper une colonne de sortie à chaque colonne externe (source).  
  
 Pour en savoir plus sur la source CDC, consultez [CDC Source](data-flow/cdc-source.md).  
  
## <a name="task-list"></a>Liste des tâches  
 **Pour ouvrir l'Éditeur de source CDC (page Colonnes)**  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] qui possède la source CDC.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la source CDC.  
  
3.  Dans l' **Éditeur de source CDC**, cliquez sur **Colonnes**.  
  
## <a name="options"></a>Options  
 **Colonnes externes disponibles**  
 Liste des colonnes externes disponibles dans la source de données. Vous ne pouvez pas ajouter ou supprimer des colonnes à l'aide de cette table. Sélectionnez les colonnes à utiliser dans la source. Les colonnes sélectionnées sont ajoutées à la liste **Colonne externe** dans l'ordre de leur sélection.  
  
 **Colonne externe**  
 Vue des colonnes externes (sources) selon l'ordre dans lequel vous les visualisez lorsque vous configurez des composants qui consomment des données à partir de la source CDC. Vous pouvez modifier cet ordre en supprimant d'abord les colonnes sélectionnées dans la liste **Colonnes externes disponibles** , puis en choisissant des colonnes externes dans la liste selon un ordre différent. Les colonnes sélectionnées sont ajoutées à la liste **Colonne externe** dans l'ordre de leur sélection.  
  
 **Colonne de sortie**  
 Spécifiez un nom unique pour chaque colonne de sortie. Le nom par défaut est celui de la colonne externe (source) sélectionnée ; toutefois, vous pouvez choisir n'importe quel nom unique et descriptif. Le nom entré est affiché dans le concepteur SSIS.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de source CDC &#40;page Gestionnaire de connexions&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md)   
 [Éditeur de source CDC &#40;page Sortie d’erreur&#41;](../../2014/integration-services/cdc-source-editor-error-output-page.md)  
  
  
