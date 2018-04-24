---
title: Objets pris en charge par l’Assistant Génération de scripts | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-scripting
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 304fd6220cef71d2c246171353e6fabb6117e8f3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>Objets pris en charge par l'Assistant Génération de scripts
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  L'Assistant Générer et publier des scripts prend en charge un sous-ensemble des objets pris en charge par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="supported-objects"></a>Objets pris en charge  
 Le tableau suivant répertorie les objets qui peuvent être publiés et pris en charge par l'Assistant Générer et publier des scripts.  
  
||||||  
|-|-|-|-|-|  
|Rôle d'application|Rôle de base de données|schéma|Agrégat défini par l'utilisateur|Affichage*|  
|Assembly|Contrainte DEFAULT|Procédure stockée*|Type de données défini par l'utilisateur|Collection de schémas XML|  
|Contrainte CHECK|Catalogue de texte intégral|Synonyme|Fonction définie par l'utilisateur||  
|Procédure stockée CLR (Common Language Runtime)|Index|Table de charge de travail|Table définie par l'utilisateur||  
|Fonction CLR définie par l'utilisateur|Règle|Utilisateur**|Type défini par l'utilisateur||  
  
 *Publié sans chiffrement.  
  
 **Tous les utilisateurs non-système qui existent dans la base de données sont publiés en tant que rôles.  
  
  
