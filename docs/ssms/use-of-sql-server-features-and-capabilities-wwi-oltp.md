---
title: Arguments pour outils externes
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- arguments [SQL Server Management Studio]
- external tools [SQL Server Management Studio]
ms.assetid: 3991c13a-f23f-450b-a2ba-19391c399735
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 23c2680b2043ff35e882e801a684f8aeb9503b21
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86010814"
---
# <a name="arguments-for-external-tools"></a>Arguments pour outils externes
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Les arguments sont des variables pour lesquelles l'environnement Studio fournit des valeurs lorsque vous lancez un outil externe à partir du menu **Outils** . Des outils externes, tels que le Bloc-notes, peuvent être ajoutés au menu **Outils** via la boîte de dialogue **Outils externes** .  
  
Le tableau ci-dessous répertorie les arguments pour les outils externes.  
  
|Name|Argument|Description|  
|--------|------------|---------------|  
|**Chemin d'accès de l'élément**|$(ItemPath)|Nom complet du fichier source en cours (sous la forme lecteur + chemin d'accès + nom du fichier) ; vide si la fenêtre active n'est pas une fenêtre source.|  
|**Répertoire de l'élément**|$(ItemDir)|Répertoire de la source en cours (sous la forme lecteur + chemin d'accès) ; vide si la fenêtre active n'est pas une fenêtre source.|  
|**Nom de fichier de l'élément**|$(ItemFilename)|Nom de fichier de la source en cours (sous la forme nom de fichier) ; vide si la fenêtre active n'est pas une fenêtre source.|  
|**Extension de l'élément**|$(ItemExt)|Extension du nom de fichier de la source en cours.|  
|**Ligne active***|$(CurLine)|Position de ligne active du curseur de l'éditeur.|  
|**Colonne active***|$(CurCol)|Position de colonne active du curseur de l'éditeur.|  
|**Texte actif***|$(CurText)|Texte actif (mot se trouvant à la position actuelle du curseur, ou sélection d'une seule ligne, s'il y en a une).|  
|**Chemin d'accès de la cible**|$(TargetPath)|Nom de fichier complet de la cible (sous la forme lecteur + chemin d'accès + nom du fichier).|  
|**Répertoire cible**|$(TargetDir)|Répertoire de la cible.|  
|**Nom de la cible**|$(TargetName)|Nom de fichier de la cible.|  
|**Extension de la cible**|$(TargetExt)|Extension du nom de fichier de la cible.|  
|**Répertoire du projet**|$(ProjDir)|Répertoire du projet en cours (sous la forme lecteur + chemin d'accès).|  
|**Nom du fichier projet**|$(ProjFileName)|Nom de fichier du projet en cours (sous la forme lecteur + chemin d'accès + nom du fichier).|  
|**Répertoire de la solution**|$(SolutionDir)|Répertoire de la solution en cours (sous la forme lecteur + chemin d'accès).|  
|**Nom du fichier solution**|$(SolutionFileName)|Nom de fichier de la solution en cours (sous la forme lecteur + chemin d'accès + nom du fichier).|  
  
*La ligne active, la colonne active ou le texte actif est basé sur la position du curseur dans l’éditeur de texte, comme indiqué dans la barre d’état.  
  
## <a name="see-also"></a>Voir aussi  
[Boîte de dialogue Outils externes](../ssms/external-tools-dialog-box.md)  
[Éléments généraux de l’interface utilisateur](../ssms/general-user-interface-elements.md)  
  
