---
title: "&#201;diteur de source de fichier plat (page Colonnes) | Microsoft Docs"
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
  - "sql13.dts.designer.flatfilesourceadapter.columns.f1"
helpviewer_keywords: 
  - "Éditeur de source de fichier plat"
ms.assetid: b5af5f65-c087-44fd-b5ae-d0441245fef2
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# &#201;diteur de source de fichier plat (page Colonnes)
  Utilisez le nœud **Colonnes** de la boîte de dialogue **Éditeur de source de fichier plat** pour mapper une colonne de sortie à chaque colonne externe (source).  
  
> [!NOTE]  
>  La propriété **FileNameColumnName** de la source de fichier plat et la propriété **FastParse** de ses colonnes de sortie ne sont pas disponibles dans l' **Éditeur de source de fichier plat**, mais elles peuvent être définie à l'aide de l' **Éditeur avancé**. Pour plus d'informations sur ces propriétés, consultez la section sur la source de fichier plat de [Flat File Custom Properties](../../integration-services/data-flow/flat-file-custom-properties.md).  
  
 Pour en savoir plus sur la source de fichier plat, consultez [Flat File Source](../../integration-services/data-flow/flat-file-source.md).  
  
## Options  
 **Colonnes externes disponibles**  
 Affiche la liste des colonnes externes disponibles dans la source de données. Vous ne pouvez pas ajouter ou supprimer des colonnes à l'aide de cette table.  
  
 **Colonne externe**  
 Affiche les colonnes externes (sources) dans l'ordre de lecture de la tâche. Vous pouvez modifier cet ordre en supprimant d'abord les colonnes sélectionnées dans la table, puis en choisissant des colonnes externes dans la liste selon un ordre différent.  
  
 **Colonne de sortie**  
 Spécifiez un nom unique pour chaque colonne de sortie. Le nom par défaut est celui de la colonne externe (source) sélectionnée ; vous pouvez néanmoins choisir n'importe quel nom unique et significatif. Le nom fourni sera affiché dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de source de fichier plat &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/flat-file-source-editor-connection-manager-page.md)   
 [Éditeur de source de fichier plat &#40;page Sortie d’erreur&#41;](../../integration-services/data-flow/flat-file-source-editor-error-output-page.md)   
 [Gestionnaire de connexions de fichiers plats](../../integration-services/connection-manager/flat-file-connection-manager.md)  
  
  