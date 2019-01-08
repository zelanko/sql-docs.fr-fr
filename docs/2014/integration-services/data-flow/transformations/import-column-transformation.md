---
title: Importation de colonne, transformation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.importcolumntrans.f1
helpviewer_keywords:
- Import Column transformation [Integration Services]
- columns [Integration Services], importing
- importing data, SSIS packages
- inserting data
ms.assetid: ac3b74c1-ef54-4297-8062-1734324fffcc
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 96996f6aa7d3b16a696f0147570fed91a9323e69
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52755021"
---
# <a name="import-column-transformation"></a>Transformation d'importation de colonne
  La transformation d'importation de colonne lit des données dans des fichiers puis les ajoute à des colonnes dans un flux de données. Grâce à cette transformation, un package peut ajouter à un flux de données du texte et des images stockés dans des fichiers distincts. Par exemple, un flux de données qui charge des données dans une table stockant des informations sur des produits peut inclure la transformation d'importation de colonne pour importer depuis des fichiers les commentaires des clients sur chaque produit, puis ajouter ces commentaires au flux de données.  
  
 Vous pouvez configurer la transformation d'importation de colonne comme suit :  
  
-   Spécifiez les colonnes auxquelles la transformation ajoute des données.  
  
-   Indiquez si la transformation attend une marque d'ordre d'octet (BOM, Byte-Order Mark).  
  
    > [!NOTE]  
    >  Une marque d'ordre d'octet n'est attendue que si les données sont du type de données DT_NTEXT.  
  
 Une colonne de l'entrée de transformation contient les noms des fichiers dans lesquels les données sont stockées. Chaque ligne de l'ensemble de données peut spécifier un fichier différent. Lorsque la transformation d'importation de colonne traite une ligne, elle lit le nom de fichier, ouvre le fichier correspondant dans le système de fichiers et charge le contenu du fichier dans une colonne de sortie. Le type de données de la colonne de sortie doit être DT_TEXT, DT_NTEXT ou DT_IMAGE. Pour plus d’informations, consultez [Integration Services Data Types](../integration-services-data-types.md).  
  
 Cette transformation a une entrée, une sortie et une sortie d'erreur.  
  
## <a name="configuration-of-the-import-column-transformation"></a>Configuration de la transformation d’importation de colonne  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../../common-properties.md)  
  
-   [Propriétés personnalisées des transformations](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur la définition des propriétés de ce composant, consultez [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Transformation d'exportation de colonne](export-column-transformation.md)   
 [Flux de données](../data-flow.md)   
 [Transformations Integration Services](integration-services-transformations.md)  
  
  
