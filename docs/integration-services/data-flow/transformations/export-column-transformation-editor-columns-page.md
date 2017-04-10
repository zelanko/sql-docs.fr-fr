---
title: "&#201;diteur de transformation d&#39;exportation de colonne (page Colonnes) | Microsoft Docs"
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
  - "sql13.dts.designer.fileextractortransformation.columns.f1"
helpviewer_keywords: 
  - "Éditeur de transformation d'exportation de colonne"
ms.assetid: b659a5c2-5509-4b5b-9c82-136c971d5c7f
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# &#201;diteur de transformation d&#39;exportation de colonne (page Colonnes)
  Utilisez la page **Colonnes** de la boîte de dialogue **Éditeur de transformation d'exportation de colonne** pour spécifier les colonnes du flux de données à extraire dans des fichiers. Vous pouvez préciser si la transformation d'exportation de colonne ajoute des données à la fin d'un fichier ou écrase le fichier existant.  
  
 Pour en savoir plus sur la transformation d'exportation de colonne, consultez [Export Column Transformation](../../../integration-services/data-flow/transformations/export-column-transformation.md).  
  
## Options  
 **Colonne d'extraction**  
 Permet de sélectionner à partir de la liste d'entrée des colonnes contenant des données texte ou image. Toutes les lignes doivent avoir des définitions pour les options **Colonne d'extraction** et **Colonne du chemin d'accès**.  
  
 **Colonne du chemin d'accès**  
 Permet de sélectionner à partir de la liste d'entrée des colonnes contenant les chemins d'accès aux fichiers ainsi que les noms de fichiers. Toutes les lignes doivent avoir des définitions pour les options **Colonne d'extraction** et **Colonne du chemin d'accès**.  
  
 **Autoriser l'ajout**  
 Permet de préciser si la transformation ajoute ou non des données à la fin des fichiers existants. La valeur par défaut est **false**.  
  
 **Forcer la troncation**  
 Permet de préciser si la transformation supprime le contenu des fichiers existants avant d'écrire des données. La valeur par défaut est **false**.  
  
 **Écrire la marque d'ordre d'octet**  
 Indique s'il est nécessaire d'écrire une marque d'ordre d'octet (BOM, Byte-Order Mark) dans le fichier. Une BOM est écrite uniquement quand les données sont de type **DT_NTEXT** ou DT_WSTR et qu’elles ne sont pas ajoutées à un fichier de données existant.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de transformation d’exportation de colonne &#40;page Sortie d’erreur&#41;](../../../integration-services/data-flow/transformations/export-column-transformation-editor-error-output-page.md)  
  
  