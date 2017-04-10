---
title: "Transformation d&#39;exportation de colonne | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.exportcolumntrans.f1"
helpviewer_keywords: 
  - "exportation de données"
  - "options d'ajout [Integration Services]"
  - "transformation d'exportation de colonne [Integration Services]"
  - "colonnes [Integration Services], exportation"
  - "insertion de données"
  - "options de troncation [Integration Services]"
ms.assetid: 678d2dfc-e40c-4fbb-b2cc-42fffc44478a
caps.latest.revision: 45
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 45
---
# Transformation d&#39;exportation de colonne
  La transformation d'exportation de colonne lit des données dans un flux de données puis les insère dans un fichier. Par exemple, si le flux de données contient des informations sur les produits, telles qu'une image de chaque produit, vous pouvez utiliser la transformation d'exportation de colonne pour enregistrer les images dans des fichiers.  
  
## Options d'ajout et de troncation  
 Le tableau suivant décrit l'impact des paramètres des options d'ajout et de troncation sur les résultats.  
  
|Ajouter|Tronqué|Le fichier existe|Résultats|  
|------------|--------------|-----------------|-------------|  
|False|False|Non|La transformation crée un nouveau fichier et y écrit les données.|  
|True|False|Non|La transformation crée un nouveau fichier et y écrit les données.|  
|False|True|Non|La transformation crée un nouveau fichier et y écrit les données.|  
|True|True|Non|La validation de la transformation au moment de la conception a échoué. Vous ne pouvez pas attribuer aux deux propriétés la valeur **true**.|  
|False|False|Oui|Une erreur d'exécution se produit. Le fichier existe, mais la transformation ne peut pas y écrire.|  
|False|True|Oui|La transformation supprime et recrée le fichier, puis y écrit les données.|  
|True|False|Oui|La transformation ouvre le fichier, à la fin duquel elle ajoute les données.|  
|True|True|Oui|La validation de la transformation au moment de la conception a échoué. Vous ne pouvez pas attribuer aux deux propriétés la valeur **true**.|  
  
## Configuration de la transformation d'exportation de colonne  
 Vous pouvez configurer la transformation d'exportation de colonne comme suit :  
  
-   Spécifier les colonnes de données et les colonnes qui contiennent le chemin d'accès aux fichiers dans lesquels les données doivent être écrites.  
  
-   Indiquer si l'opération d'insertion de données tronque des fichiers existants ou y ajoute les données.  
  
-   Indiquer si une marque d'ordre d'octet (BOM, Byte-Order Mark) est écrite dans le fichier.  
  
    > [!NOTE]  
    >  Une marque d'ordre d'octet n'est écrite que lorsque les données ne sont pas ajoutées à un fichier existant et qu'elles sont du type de données DT_NTEXT.  
  
 La transformation utilise des paires de colonnes d'entrée : une colonne contient un nom de fichier, l'autre comporte des données. Chaque ligne du jeu de données peut spécifier un fichier différent. À mesure que la transformation traite des lignes, les données sont insérées dans le fichier spécifié. Au moment de l'exécution, la transformation crée les fichiers, s'ils n'existent pas déjà, puis y écrit les données. Les données à écrire doivent être du type de données DT_TEXT, DT_NTEXT ou DT_IMAGE. Pour plus d’informations, consultez [Integration Services Data Types](../../../integration-services/data-flow/integration-services-data-types.md).  
  
 Cette transformation a une entrée, une sortie et une sortie d'erreur.  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de transformation d’exportation de colonne**, consultez [Éditeur de transformation d’exportation de colonne &#40;page Colonnes&#41;](../../../integration-services/data-flow/transformations/export-column-transformation-editor-columns-page.md).  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../Topic/Common%20Properties.md)  
  
-   [Propriétés personnalisées des transformations](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Pour plus d’informations sur la définition des propriétés, consultez [Définir les propriétés d’un composant de flux de données](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  