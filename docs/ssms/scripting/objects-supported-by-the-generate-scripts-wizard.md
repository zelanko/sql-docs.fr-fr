---
title: Objets pris en charge par l’Assistant Génération de scripts | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9161815d886594c21a69739aee88c1893bda7007
ms.sourcegitcommit: c29150492383f48ef484fa02a483cde1cbc68aca
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65821342"
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
|Procédure stockée CLR (Common Language Runtime)*|Index|Table de charge de travail|Table définie par l'utilisateur||  
|Fonction CLR définie par l'utilisateur|Règle|Utilisateur**|Type défini par l'utilisateur||  
  
 *Publié sans chiffrement.  
  
 **Tous les utilisateurs non-système qui existent dans la base de données sont publiés en tant que rôles.  
  
  
