---
title: Exportation de colonne, transformation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exportcolumntrans.f1
helpviewer_keywords:
- exporting data
- append options [Integration Services]
- Export Column transformation [Integration Services]
- columns [Integration Services], exporting
- inserting data
- truncate options [Integration Services]
ms.assetid: 678d2dfc-e40c-4fbb-b2cc-42fffc44478a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ecb72ee0cb9d6e94a672f46ed523096ac4cc096e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62900155"
---
# <a name="export-column-transformation"></a>Transformation d'exportation de colonne
  La transformation d'exportation de colonne lit des données dans un flux de données puis les insère dans un fichier. Par exemple, si le flux de données contient des informations sur les produits, telles qu'une image de chaque produit, vous pouvez utiliser la transformation d'exportation de colonne pour enregistrer les images dans des fichiers.  
  
## <a name="append-and-truncate-options"></a>Options d'ajout et de troncation  
 Le tableau suivant décrit l'impact des paramètres des options d'ajout et de troncation sur les résultats.  
  
|Ajouter|Tronqué|Le fichier existe|Résultats|  
|------------|--------------|-----------------|-------------|  
|False|False|Non|La transformation crée un nouveau fichier et y écrit les données.|  
|True|False|Non|La transformation crée un nouveau fichier et y écrit les données.|  
|False|True|Non|La transformation crée un nouveau fichier et y écrit les données.|  
|True|True|Non|La validation de la transformation au moment de la conception a échoué. Vous ne pouvez pas attribuer aux deux propriétés la valeur `true`.|  
|False|False|Oui|Une erreur d'exécution se produit. Le fichier existe, mais la transformation ne peut pas y écrire.|  
|False|True|Oui|La transformation supprime et recrée le fichier, puis y écrit les données.|  
|True|False|Oui|La transformation ouvre le fichier, à la fin duquel elle ajoute les données.|  
|True|True|Oui|La validation de la transformation au moment de la conception a échoué. Vous ne pouvez pas attribuer aux deux propriétés la valeur `true`.|  
  
## <a name="configuration-of-the-export-column-transformation"></a>Configuration de la transformation d'exportation de colonne  
 Vous pouvez configurer la transformation d'exportation de colonne comme suit :  
  
-   Spécifier les colonnes de données et les colonnes qui contiennent le chemin d'accès aux fichiers dans lesquels les données doivent être écrites.  
  
-   Indiquer si l'opération d'insertion de données tronque des fichiers existants ou y ajoute les données.  
  
-   Indiquer si une marque d'ordre d'octet (BOM, Byte-Order Mark) est écrite dans le fichier.  
  
    > [!NOTE]  
    >  Une marque d'ordre d'octet n'est écrite que lorsque les données ne sont pas ajoutées à un fichier existant et qu'elles sont du type de données DT_NTEXT.  
  
 La transformation utilise des paires de colonnes d'entrée : une colonne contient un nom de fichier, l'autre comporte des données. Chaque ligne du jeu de données peut spécifier un fichier différent. À mesure que la transformation traite des lignes, les données sont insérées dans le fichier spécifié. Au moment de l'exécution, la transformation crée les fichiers, s'ils n'existent pas déjà, puis y écrit les données. Les données à écrire doivent être du type de données DT_TEXT, DT_NTEXT ou DT_IMAGE. Pour plus d’informations, consultez [Types de données Integration Services](../integration-services-data-types.md).  
  
 Cette transformation a une entrée, une sortie et une sortie d'erreur.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de transformation d’exportation de colonne**, consultez [Éditeur de transformation d’exportation de colonne &#40;page Colonnes&#41;](../../export-column-transformation-editor-columns-page.md).  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../../common-properties.md)  
  
-   [Propriétés personnalisées des transformations](transformation-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir des propriétés, consultez [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md).  
  
  
