---
title: "Enregistrer les métadonnées (AcessToSQL) | Documents Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: fa4ce8ad-9935-4195-90f9-3fdac587a4ee
caps.latest.revision: 3
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5cc772d20da71bc811d88fa4b27bfe4d9b8f6fe0
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="save-metadata-acesstosql"></a>Enregistrer les métadonnées (AcessToSQL)
Le **enregistrer les métadonnées** boîte de dialogue vous invite à charger les métadonnées dans votre projet SSMA avant de l’enregistrer. Ce permet d’avoir un fichier de projet complet que vous pouvez utiliser hors connexion et les envoyer à d’autres personnes, tels que les membres du support technique.  
  
Pour accéder à la **enregistrer les métadonnées** boîte de dialogue, enregistrez le projet. Si les métadonnées sont manquantes, SSMA affichera le **enregistrer les métadonnées** boîte de dialogue.  
  
## <a name="options"></a>Options  
**Nom**  
Le nom de chaque base de données dans le projet.  
  
**État**  
Indique si les métadonnées sont chargées dans le projet SSMA, ou si les métadonnées sont manquantes.  
  
SSMA charge les métadonnées dans le projet en tant que nécessaire. Métadonnées sont chargées automatiquement lorsque vous parcourir les métadonnées et convertissez des schémas.  
  
**Tout sélectionner**  
Sélectionne la listés de toutes les bases de données.  
  
**Désactiver**  
Efface la case à cocher pour toutes les bases de données avec les métadonnées manquantes. Impossible d’effacer la case à cocher si une métadonnée a été chargée.  
  
**Enregistrer**  
Enregistre le projet, le chargement des métadonnées pour les bases de données sélectionnées qui ont des métadonnées manquantes.  
  
**Annuler**  
Annule l’enregistrement opération. Métadonnées manquantes ne sont pas chargée dans le projet.  
  

