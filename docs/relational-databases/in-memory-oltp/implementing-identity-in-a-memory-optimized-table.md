---
title: "Implémentation d’IDENTITY dans une table optimisée en mémoire | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 21133ec5172c13b5d010c9aef1f461282acd35b5
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="implementing-identity-in-a-memory-optimized-table"></a>Implémentation d'IDENTITY dans une table optimisée en mémoire
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

IDENTITY est pris en charge par une table optimisée en mémoire, tant que la valeur initiale et l’incrément ont tous les deux une valeur de 1 (qui est la valeur par défaut). Les colonnes d’identité avec une définition IDENTITY(x, y) où x != 1 ou y != 1 ne sont pas prises en charge dans les tables optimisées en mémoire.   
    
Pour augmenter la valeur initiale d’IDENTITY, insérez une nouvelle ligne avec une valeur explicite pour la colonne d’identité, à l’aide de l’option de session `SET IDENTITY_INSERT table_name ON`. Lors de l’insertion de la ligne, la valeur initiale d’IDENTITY est remplacée par la valeur insérée de manière explicite, plus 1. Par exemple, pour augmenter la valeur initiale à 1 000, insérez une ligne avec la valeur 999 dans la colonne d’identité. Les valeurs d’identité générées commenceront alors à 1 000.     
  
## <a name="see-also"></a>Voir aussi  
 [Migration vers OLTP en mémoire](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
