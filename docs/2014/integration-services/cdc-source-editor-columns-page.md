---
title: Éditeur de Source CDC (Page colonnes) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.designer.cdcsource.columns.f1
ms.assetid: bcf3030e-98d8-4445-967c-33c3f8ecb4fc
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 87d5d9b1096e2068759a2100b4daf504849fba0e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050863"
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
 [Éditeur de Source CDC &#40;Page Gestionnaire de connexions&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md)   
 [Éditeur de Source CDC &#40;Page sortie d’erreur&#41;](../../2014/integration-services/cdc-source-editor-error-output-page.md)  
  
  