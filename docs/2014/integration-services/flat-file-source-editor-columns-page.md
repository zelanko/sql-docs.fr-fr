---
title: Flat File Source Editor (Page colonnes) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.columns.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: b5af5f65-c087-44fd-b5ae-d0441245fef2
caps.latest.revision: 28
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0d0007a98a02da095887aa0faedb12ba629f5e01
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37171020"
---
# <a name="flat-file-source-editor-columns-page"></a>Éditeur de source de fichier plat (page Colonnes)
  Utilisez le nœud **Colonnes** de la boîte de dialogue **Éditeur de source de fichier plat** pour mapper une colonne de sortie à chaque colonne externe (source).  
  
> [!NOTE]  
>  Le `FileNameColumnName` propriété de la source de fichier plat et la `FastParse` propriété de ses colonnes de sortie ne sont pas disponibles dans le **éditeur de Source de fichier plat**, mais peut être définie à l’aide de la **éditeur avancé** . Pour plus d'informations sur ces propriétés, consultez la section sur la source de fichier plat de [Flat File Custom Properties](data-flow/flat-file-custom-properties.md).  
  
 Pour en savoir plus sur la source de fichier plat, consultez [Flat File Source](data-flow/flat-file-source.md).  
  
## <a name="options"></a>Options  
 **Colonnes externes disponibles**  
 Affiche la liste des colonnes externes disponibles dans la source de données. Vous ne pouvez pas ajouter ou supprimer des colonnes à l'aide de cette table.  
  
 **Colonne externe**  
 Affiche les colonnes externes (sources) dans l'ordre de lecture de la tâche. Vous pouvez modifier cet ordre en supprimant d'abord les colonnes sélectionnées dans la table, puis en choisissant des colonnes externes dans la liste selon un ordre différent.  
  
 **Colonne de sortie**  
 Spécifiez un nom unique pour chaque colonne de sortie. Le nom par défaut est celui de la colonne externe (source) sélectionnée ; vous pouvez néanmoins choisir n'importe quel nom unique et significatif. Le nom fourni sera affiché dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Flat File Source Editor &#40;Page Gestionnaire de connexions&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md)   
 [Flat File Source Editor &#40;Page sortie d’erreur&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md)   
 [Gestionnaire de connexions de fichiers plats](connection-manager/file-connection-manager.md)  
  
  
