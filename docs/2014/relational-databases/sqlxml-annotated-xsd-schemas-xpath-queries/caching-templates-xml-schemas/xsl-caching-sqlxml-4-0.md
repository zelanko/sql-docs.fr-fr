---
title: Mise en cache XSL (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- XSL caching [SQLXML]
ms.assetid: 91994142-32f0-4d8d-a8cf-eb0d8b1f1999
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9c23a208a0276a2a3eb71f493aa7e5ce7fad0928
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62805823"
---
# <a name="xsl-caching-sqlxml-40"></a>Mise en cache XSL (SQLXML 4.0)
  La mise en cache des feuilles de style XSL améliore les performances. Lors de sa première exécution, une feuille de style XSL reste en mémoire si la mise en cache XSL est définie à ON ; cela permet d'améliorer les performances pour les traitements ultérieurs. Le paramètre par défaut est ON.  
  
 Vous pouvez définir la taille du cache XSL en ajoutant la clé suivante au Registre :  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\XSLCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 La taille du cache XSL doit être définie d'après la mémoire disponible et le nombre de feuilles de style XSL que vous utilisez. La valeur par défaut de **XSLCacheSize** est 31. Vous pouvez augmenter la taille du cache si l'accès XSL semble lent, ou diminuer la taille du cache si la mémoire est insuffisante.  
  
 Pour des performances optimales, il est recommandé de définir **XSLCacheSize** à une valeur plus élevée que le nombre de feuilles de style XSL que vous utilisez généralement. Si la valeur de **XSLCacheSize** est inférieure au nombre de feuilles de style XSL disponibles, les performances se dégradent avec l'augmentation du nombre de feuilles de style XSL. La valeur maximale qui peut être définie pour **XSLCacheSize** est 128.  
  
 Chaque fois que la feuille de style XSL mise en cache est utilisée, l'heure de modification du fichier XSL est vérifiée pour déterminer s'il doit être actualisé. En effet, la copie du disque est plus récente que la copie du cache.  
  
## <a name="see-also"></a>Voir aussi  
 [La mise en cache de modèle &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md)   
 [Schema Caching &#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md)  
  
  
