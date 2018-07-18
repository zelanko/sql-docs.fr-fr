---
title: Supprimer une Source de données dans l’Explorateur de solutions (SSAS multidimensionnel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.deleteobjects.f1
helpviewer_keywords:
- data sources [Analysis Services], deleting
- deleting data sources
- removing data sources
ms.assetid: b45441ef-f909-4736-98b9-cc80d0acac99
caps.latest.revision: 45
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7be5e8a95a340794e2754f272a223c31a27e8a58
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169680"
---
# <a name="delete-a-data-source-in-solution-explorer-ssas-multidimensional"></a>Supprimer une source de données dans l'Explorateur de solutions (SSAS Multidimensionnel)
  Vous pouvez supprimer un objet de source de données afin de l'effacer définitivement d'un projet de modèle multidimensionnel Analysis Services.  
  
 Dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], les sources de données constituent la base sur laquelle les vues de sources de données sont construites et les vues de sources de données servent à leur tour à définir des dimensions, des cubes et des structures d'exploration de données dans un projet ou une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Par conséquent, la suppression d'une source de données peut rendre d'autres objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] d'un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non valides. Pensez à toujours vérifier la liste des objets dépendants qui est fournie avant de supprimer l'objet.  
  
> [!IMPORTANT]  
>  Les sources de données dont dépendent d’autres objets ne peuvent pas être supprimées d’une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ouverte par [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] en mode en ligne. Vous devez supprimer tous les objets de la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui dépendent de cette source de données avant de supprimer la source de données. Pour plus d’informations sur le mode en ligne, consultez [Connexion en mode en ligne à une base de données Analysis Services](connect-in-online-mode-to-an-analysis-services-database.md).  
  
### <a name="to-delete-a-data-source"></a>Pour supprimer une source de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet ou connectez-vous à la base de données dans laquelle vous souhaitez supprimer une source de données.  
  
2.  Dans **l’Explorateur de solutions**, développez le dossier **Sources de données** .  
  
3.  Cliquez avec le bouton droit sur la source de données, puis sélectionnez **Supprimer**. La boîte de dialogue **Supprimer les objets**  qui s’affiche indique les objets qui seront rendus non valides si vous supprimez la source de données. Examinez soigneusement cette liste avant de cliquer sur **OK** pour supprimer la source de données.  
  
4.  Enregistrez le projet.  
  
     Après avoir supprimé une source de données dans un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vous devez enregistrer le projet modifié. Dans le cas contraire, vous recevrez un message d’erreur la prochaine fois que vous ouvrirez le projet, car le fichier XML sous-jacent de la source de données supprimée sera manquant lorsque le projet tentera de charger la source de données supprimée.  
  
## <a name="see-also"></a>Voir aussi  
 [Sources de données dans les modèles multidimensionnels](data-sources-in-multidimensional-models.md)   
 [Sources de données prises en charge &#40;SSAS multidimensionnel&#41;](supported-data-sources-ssas-multidimensional.md)  
  
  
