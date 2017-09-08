---
title: "Avancé de sélection d’un objet (SybaseToSQL) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.prod: sql-non-specified
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: d2baa90f-1b77-47ce-988d-1910c7c74103
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 511e907f3f73d3a000d35c2ba0771af0b940056d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="advanced-object-selection-sybasetosql"></a>Sélection d’objet avancé (SybaseToSQL)
Le **Section avancé de l’objet** boîte de dialogue vous permet de filtrer les objets de base de données à l’aide de chaînes et les sous-chaînes dans le nom d’objet, puis sélectionnez ou désélectionnez ces objets. SSMA effectue des opérations de conversion et la migration sur les objets sélectionnés.  
  
Pour accéder à cette boîte de dialogue, avec le bouton droit dans l’Explorateur de métadonnées, puis **sélection avancée de l’objet**.  
  
Lorsque vous ouvrez la boîte de dialogue, cliquez sur **afficher les éléments de sous-catégories** pour afficher tous les objets qui ont des métadonnées chargées dans le projet. Vous pouvez entrer ensuite des chaînes pour filtrer les éléments. Par exemple, entrez la chaîne « company » pour afficher tous les éléments avec des noms qui incluent cette chaîne.  
  
Avant d’utiliser cette boîte de dialogue, vous souhaiterez forcer SSMA pour charger toutes les métadonnées par conversion de schémas ou de l’enregistrement du projet.  
  
## <a name="options"></a>Options  
**Vérifiez tous les éléments**  
Ajoute une case à cocher en regard de tous les éléments. Ces éléments sont immédiatement sélectionnés dans l’Explorateur de métadonnées.  
  
**Désactivez tous les éléments**  
Supprime la case à cocher en regard de tous les éléments. Ces éléments seront effacées immédiatement dans l’Explorateur de métadonnées.  
  
**Mode liste**  
Affiche les éléments dans une liste filtrés.  
  
**Mode d’affichage de tableau**  
Affiche les éléments dans une table filtrés.  
  
**Affiche les éléments chargés uniquement**  
Active/désactive l’affichage des catégories ou des éléments. Lorsque cette option est sélectionnée, SSMA montre tous les éléments qui correspondent aux critères de filtre et ceux qui ont été précédemment chargée. Lorsque ce bouton n’est pas sélectionné, SSMA montre les dossiers de catégorie.  
  
**Filtre**  
Entrez la chaîne que vous souhaitez utiliser pour filtrer les éléments. Par exemple, pour rechercher tous les éléments qui contiennent la chaîne « ID » dans le nom de l’élément, entrez la chaîne « ID » dans le **filtre** boîte.  
  
Si les éléments correspondent aux critères de filtre, les catégories ou éléments seront affiche lorsque vous tapez la chaîne. Pour afficher les éléments correspondants, nous vous recommandons de cliquer sur le **affiche uniquement les éléments chargés** bouton.  
  
**Effacer le filtre**  
Efface le **filtre** boîte.  
  

