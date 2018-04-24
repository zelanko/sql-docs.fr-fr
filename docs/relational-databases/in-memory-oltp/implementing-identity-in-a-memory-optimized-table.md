---
title: Implémentation d’IDENTITY dans une table optimisée en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 97695b8edb0ea13e2bd16a9dce754f32a0dd4742
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a>Implémentation d'IDENTITY dans une table optimisée en mémoire
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

IDENTITY est pris en charge par une table optimisée en mémoire, tant que la valeur initiale et l’incrément ont tous les deux une valeur de 1 (qui est la valeur par défaut). Les colonnes d’identité avec une définition IDENTITY(x, y) où x != 1 ou y != 1 ne sont pas prises en charge dans les tables optimisées en mémoire.   
    
Pour augmenter la valeur initiale d’IDENTITY, insérez une nouvelle ligne avec une valeur explicite pour la colonne d’identité, à l’aide de l’option de session `SET IDENTITY_INSERT table_name ON`. Lors de l’insertion de la ligne, la valeur initiale d’IDENTITY est remplacée par la valeur insérée de manière explicite, plus 1. Par exemple, pour augmenter la valeur initiale à 1 000, insérez une ligne avec la valeur 999 dans la colonne d’identité. Les valeurs d’identité générées commenceront alors à 1 000.     
  
## <a name="see-also"></a> Voir aussi  
 [Migration vers OLTP en mémoire](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
