---
title: Éditeur de Source ODBC (Page colonnes) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.columns.f1
ms.assetid: 565984eb-8318-4be7-bebc-262209cf5065
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2e7a9fb71dca2e99bebe3f23486ff6331bd843de
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62890643"
---
# <a name="odbc-source-editor-columns-page"></a>Éditeur de source ODBC (page Colonnes)
  Utilisez la page **Colonnes** de la boîte de dialogue **Éditeur de source ODBC** pour mapper une colonne de sortie à chaque colonne externe (source).  
  
 Pour en savoir plus sur la source ODBC, consultez [ODBC Source](data-flow/odbc-source.md).  
  
## <a name="task-list"></a>Liste des tâches  
 **Pour ouvrir l'Éditeur de source ODBC (page Colonnes)**  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] qui possède la source ODBC.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la source ODBC.  
  
3.  Dans l' **Éditeur de source ODBC**, cliquez sur **Colonnes**.  
  
## <a name="options"></a>Options  
  
### <a name="available-external-columns"></a>Colonnes externes disponibles  
 Liste des colonnes externes disponibles dans la source de données. Vous ne pouvez pas ajouter ou supprimer des colonnes à l'aide de cette table. Sélectionnez les colonnes à utiliser dans la source. Les colonnes sélectionnées sont ajoutées à la liste **Colonne externe** dans l'ordre de leur sélection.  
  
 Activez la case à cocher **Sélectionner tout** pour sélectionner toutes les colonnes.  
  
### <a name="external-column"></a>Colonne externe  
 Vue des colonnes externes (sources) selon l'ordre dans lequel vous les visualisez lorsque vous configurez des composants qui consomment des données à partir de la source ODBC.  
  
### <a name="output-column"></a>Colonne de sortie  
 Spécifiez un nom unique pour chaque colonne de sortie. Le nom par défaut est celui de la colonne externe (source) sélectionnée ; vous pouvez néanmoins choisir n'importe quel nom unique et significatif. Le nom entré est affiché dans le concepteur SSIS.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de source ODBC &#40;page Gestionnaire de connexions&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md)   
 [Éditeur de source ODBC &#40;page Sortie d’erreur&#41;](../../2014/integration-services/odbc-source-editor-error-output-page.md)  
  
  
