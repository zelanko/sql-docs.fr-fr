---
title: Schéma de mise en cache (SQLXML 4.0) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- schemas [SQLXML]
ms.assetid: 7e5fda21-b435-41fd-b637-8b616560a93f
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6ddf2b95f9b72a0def960f6159cd8646a6b4439c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045324"
---
# <a name="schema-caching-sqlxml-40"></a>Mise en cache des schémas (SQLXML 4.0)
  Avec une installation côte à côte de XML pour Microsoft SQL Server 2000 Web Release 1, Microsoft SQLXML 2.0 et SQLXML 3.0, vous pouvez contrôler explicitement le schéma de mise en cache dans toutes les versions à l’aide de clés de Registre suivantes :  
  
 Web Release 1 :  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXMLX\SchemaCacheSize  
```  
  
 SQLXML 2.0 :  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML2\SchemaCacheSize  
```  
  
 SQLXML 3.0 :  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML3\SchemaCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 Pour plus d’informations sur l’installation de côte à côte, consultez [Nouveautés de SQLXML 4.0 SP1](../../sqlxml/what-s-new-in-sqlxml-4-0-sp1.md).  
  
 La mise en cache des schémas améliore considérablement les performances d'une requête XPath. Quand une requête XPath est exécutée sur un schéma de mappage, le schéma est stocké en mémoire et les structures de données nécessaires sont construites en mémoire. Si la mise en cache des schémas est définie, le schéma demeure en mémoire, en améliorant de cette façon les requêtes XPath suivantes.  
  
 Vous pouvez définir la taille du cache des schémas en ajoutant la clé précitée au Registre.  
  
 La taille du schéma est fonction de la mémoire disponible et du nombre de schémas que vous utilisez. La valeur par défaut **SchemaCacheSize** est 31. Si vous définissez **SchemaCacheSize** plus élevée, plus de mémoire est utilisée. Par conséquent, vous pouvez augmenter la taille du cache en cas d'accès lent au schéma ou diminuer la taille du cache si la mémoire est insuffisante.  
  
 Pour des raisons de performances, il est recommandé de définir **SchemaCacheSize** supérieure au nombre de schémas de mappage que vous utilisez généralement. Comme le nombre de schémas augmente, si **SchemaCacheSize** est inférieur au nombre de schémas que vous avez, les performances se dégradent.  
  
> [!NOTE]  
>  Pendant le développement, il est recommandé de ne pas mettre en cache les schémas, car les modifications apportées aux schémas ne sont pas répercutées dans le cache pendant deux minutes environ.  
  
## <a name="see-also"></a>Voir aussi  
 [La mise en cache de modèle &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md)   
 [Mise en cache XSL &#40;SQLXML 4.0&#41;](xsl-caching-sqlxml-4-0.md)  
  
  