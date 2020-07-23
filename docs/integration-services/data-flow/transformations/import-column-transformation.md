---
title: Importation de colonne, transformation | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.importcolumntrans.f1
helpviewer_keywords:
- Import Column transformation [Integration Services]
- columns [Integration Services], importing
- importing data, SSIS packages
- inserting data
ms.assetid: ac3b74c1-ef54-4297-8062-1734324fffcc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1db13057275f9a255ad247bd5f86ca35d7bd29d3
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86919260"
---
# <a name="import-column-transformation"></a>Transformation d'importation de colonne

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  La transformation d'importation de colonne lit des données dans des fichiers puis les ajoute à des colonnes dans un flux de données. Grâce à cette transformation, un package peut ajouter à un flux de données du texte et des images stockés dans des fichiers distincts. Par exemple, un flux de données qui charge des données dans une table stockant des informations sur des produits peut inclure la transformation d'importation de colonne pour importer depuis des fichiers les commentaires des clients sur chaque produit, puis ajouter ces commentaires au flux de données.  
  
 Vous pouvez configurer la transformation d'importation de colonne comme suit :  
  
-   Spécifiez les colonnes auxquelles la transformation ajoute des données.  
  
-   Indiquez si la transformation attend une marque d'ordre d'octet (BOM, Byte-Order Mark).  
  
    > [!NOTE]  
    >  Une marque d'ordre d'octet n'est attendue que si les données sont du type de données DT_NTEXT.  
  
 Une colonne de l'entrée de transformation contient les noms des fichiers dans lesquels les données sont stockées. Chaque ligne de l'ensemble de données peut spécifier un fichier différent. Lorsque la transformation d'importation de colonne traite une ligne, elle lit le nom de fichier, ouvre le fichier correspondant dans le système de fichiers et charge le contenu du fichier dans une colonne de sortie. Le type de données de la colonne de sortie doit être DT_TEXT, DT_NTEXT ou DT_IMAGE. Pour plus d’informations, consultez [Types de données Integration Services](../../../integration-services/data-flow/integration-services-data-types.md).  
  
 Cette transformation a une entrée, une sortie et une sortie d'erreur.  
  
## <a name="configuration-of-the-import-column-transformation"></a>Configuration de la transformation d’importation de colonne  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Propriétés personnalisées des transformations](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur la définition des propriétés de ce composant, consultez [Définir les propriétés d’un composant de flux de données](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Transformation d'exportation de colonne](../../../integration-services/data-flow/transformations/export-column-transformation.md)   
 [Flux de données](../../../integration-services/data-flow/data-flow.md)   
 [Transformations Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  
