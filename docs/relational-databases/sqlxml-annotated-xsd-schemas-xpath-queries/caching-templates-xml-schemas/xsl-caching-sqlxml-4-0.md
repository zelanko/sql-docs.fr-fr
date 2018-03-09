---
title: Mise en cache XSL (SQLXML 4.0) | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- XSL caching [SQLXML]
ms.assetid: 91994142-32f0-4d8d-a8cf-eb0d8b1f1999
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2b43e029278c8cab6cd842d5d2bafdad9a31ad63
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2018
---
# <a name="xsl-caching-sqlxml-40"></a>Mise en cache XSL (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
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
 [La mise en cache de modèle &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/template-caching-sqlxml-4-0.md)   
 [La mise en cache de schéma &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)  
  
  
