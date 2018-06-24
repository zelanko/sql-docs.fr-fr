---
title: Objets pris en charge par l’Assistant Génération de scripts | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
caps.latest.revision: 5
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f102fa4366106581c5f3ec4ff141d537531dbaa4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040598"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>Objets pris en charge par l'Assistant Génération de scripts
  L'Assistant Générer et publier des scripts prend en charge un sous-ensemble des objets pris en charge par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="supported-objects"></a>Objets pris en charge  
 Le tableau suivant répertorie les objets qui peuvent être publiés et pris en charge par l'Assistant Générer et publier des scripts.  
  
||||||  
|-|-|-|-|-|  
|Rôle d'application|Rôle de base de données|schéma|Agrégat défini par l'utilisateur|Vue<sup>1</sup>|  
|Assembly|Contrainte DEFAULT|Procédure stockée<sup>1</sup>|Type de données défini par l'utilisateur|Collection de schémas XML|  
|Contrainte CHECK|Catalogue de texte intégral|Synonyme|Fonction définie par l'utilisateur||  
|Procédure stockée CLR (common language runtime)<sup>1</sup>|Index|Table de charge de travail|Table définie par l'utilisateur||  
|Fonction CLR définie par l'utilisateur|Règle|Utilisateur<sup>2</sup>|Type défini par l'utilisateur||  
  
 <sup>1</sup> publié sans chiffrement.  
  
 <sup>2</sup> tous les utilisateurs non-système qui existent dans la base de données sont publiés en tant que rôles.  
  
  