---
title: Éditeur de restauration de références de colonnes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.resolvereferences.mapper.F1
- sql12.dts.designer.resolvereferences.preview.F1
ms.assetid: bb3ee33c-79c4-4c76-a82f-71581b4a60f1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8b56e089feba35c3fe83e0a4e593309f8d1ac782
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85431376"
---
# <a name="resolve-column-reference-editor"></a>Éditeur de restauration de références de colonnes
  Lorsqu'un chemin d'accès d'entrée est déconnecté ou s'il existe des colonnes non mappées dans le chemin d'accès, une icône d'erreur s'affiche en regard du chemin d'accès aux données correspondant. Pour simplifier la résolution des erreurs de référence de colonne, le nouvel éditeur de résolution des références vous permet de lier des colonnes de sortie non mappées avec des colonnes d'entrée non mappées pour tous les chemins d'accès de l'arborescence d'exécution. L'éditeur de résolution des références met également en surbrillance les chemins d'accès pour indiquer ceux qui sont résolus.  
  
> [!NOTE]  
>  Il est maintenant possible de modifier un composant même lorsque son chemin d'accès d'entrée est déconnecté.  
  
 Une fois toutes les références de colonnes résolues, s'il n'y a pas d'autres erreurs de chemin d'accès aux données, aucune icône d'erreur ne s'affiche en regard des chemins d'accès aux données.  
  
## <a name="options"></a>Options  
 Colonnes de sortie non mappées (source) :  
 Colonnes du chemin d'accès en amont qui ne sont pas mappées  
  
 Colonnes mappées (source) :  
 Colonnes du chemin d'accès en amont qui sont mappées à des colonnes du chemin d'accès en aval  
  
 Colonnes mappées (destination) :  
 Colonnes du chemin d'accès en amont qui sont mappées à des colonnes du chemin d'accès en aval  
  
 Colonnes d'entrée non mappées (destination) :  
 Colonnes du chemin d'accès en aval qui ne sont pas mappées  
  
 Supprimer les colonnes d'entrée non mappées  
 Activez Supprimer les colonnes d'entrée non mappées pour ignorer les colonnes non mappées au niveau de la destination du chemin d'accès aux données. Le bouton Aperçu des modifications affiche la liste des modifications qui se produiront lorsque vous appuierez sur le bouton OK.  
  
  
