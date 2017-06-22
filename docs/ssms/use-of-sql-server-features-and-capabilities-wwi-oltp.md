---
title: Arguments pour outils externes | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- arguments [SQL Server Management Studio]
- external tools [SQL Server Management Studio]
ms.assetid: 3991c13a-f23f-450b-a2ba-19391c399735
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 514b5f4e9e5df63f745e7f2e6a9465cddd6c4628
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="arguments-for-external-tools"></a>Arguments pour outils externes
Les arguments sont des variables pour lesquelles l'environnement Studio fournit des valeurs lorsque vous lancez un outil externe à partir du menu **Outils** . Des outils externes, tels que le Bloc-notes, peuvent être ajoutés au menu **Outils** via la boîte de dialogue **Outils externes** .  
  
Le tableau ci-dessous répertorie les arguments pour les outils externes.  
  
|Nom|Argument|Description|  
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
[Éléments généraux relatifs à l'interface utilisateur](../ssms/general-user-interface-elements.md)  
  

