---
title: "Résoudre l’éditeur de référence de colonne | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.resolvereferences.preview.F1
- sql13.dts.designer.resolvereferences.mapper.F1
ms.assetid: bb3ee33c-79c4-4c76-a82f-71581b4a60f1
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f2ff8a97d45d75c3e93d4aa3111b653c9612b889
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="resolve-column-reference-editor"></a>Éditeur de restauration de références de colonnes
  Lorsqu'un chemin d'accès d'entrée est déconnecté ou s'il existe des colonnes non mappées dans le chemin d'accès, une icône d'erreur s'affiche en regard du chemin d'accès aux données correspondant. Pour simplifier la résolution des erreurs de référence de colonne, l’éditeur de résolution des références vous permet de lier des colonnes de sortie non mappées avec des colonnes d’entrée non mappées pour tous les chemins d’accès dans l’arborescence d’exécution. L'éditeur de résolution des références met également en surbrillance les chemins d'accès pour indiquer ceux qui sont résolus.  
  
> [!NOTE]  
>  Il est possible de modifier un composant même lorsque son chemin d’accès d’entrée est déconnecté.  
  
 Une fois toutes les références de colonnes résolues, s'il n'y a pas d'autres erreurs de chemin d'accès aux données, aucune icône d'erreur ne s'affiche en regard des chemins d'accès aux données.  
  
## <a name="options"></a>Options  
 **Colonnes de sortie non mappées (Source)**    
 Colonnes du chemin d'accès en amont qui ne sont pas mappées  
  
**Colonnes mappées (Source)**    
 Colonnes du chemin d'accès en amont qui sont mappées à des colonnes du chemin d'accès en aval  
  
**Colonnes mappées (Destination)**    
 Colonnes du chemin d'accès en amont qui sont mappées à des colonnes du chemin d'accès en aval  
  
**Colonnes d’entrée non mappées (Destination)**    
 Colonnes du chemin d'accès en aval qui ne sont pas mappées  
  
**Supprimer les colonnes d'entrée non mappées**  
 Activez Supprimer les colonnes d'entrée non mappées pour ignorer les colonnes non mappées au niveau de la destination du chemin d'accès aux données. Le bouton Aperçu des modifications affiche la liste des modifications qui se produiront lorsque vous appuierez sur le bouton OK.  
  
  

