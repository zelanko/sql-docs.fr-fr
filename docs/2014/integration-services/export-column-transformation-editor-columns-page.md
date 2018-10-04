---
title: Exporter l’éditeur de Transformation de colonne (Page colonnes) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileextractortransformation.columns.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: b659a5c2-5509-4b5b-9c82-136c971d5c7f
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e12fa5ca9d9295ffe1311062215217044ada2135
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048389"
---
# <a name="export-column-transformation-editor-columns-page"></a>Éditeur de transformation d'exportation de colonne (page Colonnes)
  Utilisez la page **Colonnes** de la boîte de dialogue **Éditeur de transformation d'exportation de colonne** pour spécifier les colonnes du flux de données à extraire dans des fichiers. Vous pouvez préciser si la transformation d'exportation de colonne ajoute des données à la fin d'un fichier ou écrase le fichier existant.  
  
 Pour en savoir plus sur la transformation d'exportation de colonne, consultez [Export Column Transformation](data-flow/transformations/export-column-transformation.md).  
  
## <a name="options"></a>Options  
 **Colonne d'extraction**  
 Permet de sélectionner à partir de la liste d'entrée des colonnes contenant des données texte ou image. Toutes les lignes doivent avoir des définitions pour les options **Colonne d'extraction** et **Colonne du chemin d'accès**.  
  
 **Colonne du chemin d'accès**  
 Permet de sélectionner à partir de la liste d'entrée des colonnes contenant les chemins d'accès aux fichiers ainsi que les noms de fichiers. Toutes les lignes doivent avoir des définitions pour les options **Colonne d'extraction** et **Colonne du chemin d'accès**.  
  
 **Autoriser l'ajout**  
 Permet de préciser si la transformation ajoute ou non des données à la fin des fichiers existants. La valeur par défaut est `false`.  
  
 **Forcer la troncation**  
 Permet de préciser si la transformation supprime le contenu des fichiers existants avant d'écrire des données. La valeur par défaut est `false`.  
  
 **Écrire la marque d'ordre d'octet**  
 Indique s'il est nécessaire d'écrire une marque d'ordre d'octet (BOM, Byte-Order Mark) dans le fichier. Un BOM est écrite uniquement si les données ont le `DT_NTEXT` ou type de données DT_WSTR et ne sont pas ajoutées à un fichier de données existant.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Exporter l’éditeur de Transformation de colonne &#40;Page sortie d’erreur&#41;](../../2014/integration-services/export-column-transformation-editor-error-output-page.md)  
  
  
