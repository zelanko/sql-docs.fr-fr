---
title: Schéma de la mise en cache (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- schemas [SQLXML]
ms.assetid: 7e5fda21-b435-41fd-b637-8b616560a93f
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: f6b9e9a8a6d9406def9e2adc90e1ef7e9b8545a1
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39559639"
---
# <a name="schema-caching-sqlxml-40"></a>Mise en cache des schémas (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
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
  
 Pour plus d’informations sur l’installation de la côte à côte, consultez [What ' s New in SQLXML 4.0 SP1](../../../relational-databases/sqlxml/what-s-new-in-sqlxml-4-0-sp1.md).  
  
 La mise en cache des schémas améliore considérablement les performances d'une requête XPath. Quand une requête XPath est exécutée sur un schéma de mappage, le schéma est stocké en mémoire et les structures de données nécessaires sont construites en mémoire. Si la mise en cache des schémas est définie, le schéma demeure en mémoire, en améliorant de cette façon les requêtes XPath suivantes.  
  
 Vous pouvez définir la taille du cache des schémas en ajoutant la clé précitée au Registre.  
  
 La taille du schéma est fonction de la mémoire disponible et du nombre de schémas que vous utilisez. La valeur par défaut **SchemaCacheSize** est 31. Si vous définissez **SchemaCacheSize** plus élevé, plus de mémoire est utilisée. Par conséquent, vous pouvez augmenter la taille du cache en cas d'accès lent au schéma ou diminuer la taille du cache si la mémoire est insuffisante.  
  
 Pour des raisons de performances, il est recommandé de définir **SchemaCacheSize** supérieure au nombre de schémas de mappage que vous utilisez habituellement. Comme le nombre de schémas augmente, si **SchemaCacheSize** est inférieur au nombre de schémas que vous avez, les performances se dégradent.  
  
> [!NOTE]  
>  Pendant le développement, il est recommandé de ne pas mettre en cache les schémas, car les modifications apportées aux schémas ne sont pas répercutées dans le cache pendant deux minutes environ.  
  
## <a name="see-also"></a>Voir aussi  
 [La mise en cache de modèle &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/template-caching-sqlxml-4-0.md)   
 [La mise en cache XSL &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
  
  
