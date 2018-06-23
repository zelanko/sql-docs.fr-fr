---
title: Importer à partir de PowerPivot (SSAS tabulaire) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.bidtoolset.importfromppt.f1
ms.assetid: ac1a6a79-bda3-4122-a717-8b1e2f77da02
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4636578c435ac158f92ef4968072e374af7fb4f9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051356"
---
# <a name="import-from-powerpivot-ssas-tabular"></a>Importer à partir de PowerPivot (SSAS Tabulaire)
  Cette rubrique décrit la procédure de création d'un projet de modèle tabulaire en important les métadonnées et les données d'un classeur PowerPivot à l'aide du modèle de projet Importer à partir de PowerPivot dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
## <a name="create-a-new-tabular-model-from-a-powerpivot-for-excel-file"></a>Créer un nouveau modèle tabulaire à partir d'un fichier PowerPivot pour Excel  
 Lors de la création d'un nouveau projet de modèle tabulaire par importation à partir d'un classeur PowerPivot, les métadonnées qui définissent la structure du classeur sont utilisées pour créer et définir la structure du projet de modèle tabulaire dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Les objets tels que les tables, les colonnes, les mesures et les relations sont conservés et apparaîtront dans le projet de modèle tabulaire tels qu'ils s'affichent dans le classeur PowerPivot. Aucune modification n'est apportée au fichier de classeur .xlsx.  
  
> [!NOTE]  
>  Les modèles tabulaires ne prennent pas en charge les tables liées. Lors de l'importation d'un classeur PowerPivot qui contient une table liée, les données de la table liée sont traitées comme des données copiées/collées et stockées dans le fichier Model.bim. Pendant la consultation des propriétés d’une table copiée\collée, la propriété **Données source** est désactivée et la boîte de dialogue **Propriétés de la table** est désactivée dans le menu **Table** .  
>   
>  Il existe une limite de 10 000 lignes qui peuvent être ajoutées aux données incorporées dans le modèle. Si vous importez un modèle PowerPivot et rencontrez l'erreur « Données tronquées. Les tables collées ne peuvent pas contenir plus de 10 000 lignes », vous devez modifier le modèle PowerPivot en déplaçant les données incorporées dans une autre source de données, telle qu'une table dans SQL Server, puis réimporter.  
  
 Il existe des considérations spéciales selon que la base de données d'espace de travail se trouve dans une instance Analysis Services sur le même ordinateur (local) que [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou dans une instance Analysis Services distante.  
  
 Si la base de données d'espace de travail se trouve sur une instance Analysis Services locale, vous pouvez importer les métadonnées et les données depuis le classeur PowerPivot. Les métadonnées sont copiées depuis le classeur et utilisées pour créer le projet de modèle tabulaire. Les données sont ensuite copiées depuis le classeur et stockées dans la base de données d'espace de travail du projet (sauf pour les données copiées/collées, qui sont stockées dans le fichier Model.bim).  
  
 Si la base de données d'espace de travail se trouve dans une instance Analysis Services distante, vous ne pouvez pas importer de données depuis un classeur PowerPivot pour Excel. Vous pouvez toujours importer les métadonnées de classeur ; toutefois, cela provoque l'exécution d'un script sur l'instance Analysis Services distante. Vous devez uniquement importer des métadonnées d'un classeur PowerPivot approuvé. Les données doivent être importées à partir des sources définies dans les connexions à la source de données. Les données de table liée et copiées/collées dans le classeur PowerPivot doivent être copiées et collées dans le projet de modèle tabulaire.  
  
#### <a name="to-create-a-new-tabular-model-project-from-a-powerpivot-for-excel-file"></a>Pour créer un nouveau projet de modèle tabulaire à partir d'un fichier PowerPivot pour Excel  
  
1.  Dans le menu [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]Fichier **de** , cliquez sur **Nouveau**, puis sur **Projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue **modèles installés**, cliquez sur **Business Intelligence**, puis cliquez sur **importation à partir de PowerPivot**.  
  
3.  Pour le  **Nom**, tapez un nom pour le projet, puis spécifiez un emplacement et le nom de la solution et cliquez sur **OK**.  
  
4.  Dans la boîte de dialogue **Ouvrir** , sélectionnez le fichier [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] qui contient les données et les métadonnées de modèle que vous souhaitez importer, puis cliquez sur **Ouvrir**.  
  
## <a name="see-also"></a>Voir aussi  
 [Base de données de l’espace de travail &#40;SSAS tabulaire&#41;](workspace-database-ssas-tabular.md)   
 [Copier et coller des données &#40;SSAS tabulaire&#41;](../copy-and-paste-data-ssas-tabular.md)  
  
  