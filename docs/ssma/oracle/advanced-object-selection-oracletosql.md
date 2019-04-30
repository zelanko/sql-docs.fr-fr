---
title: Sélection d’objet (OracleToSQL) avancée | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: c978fba4-c953-4ed0-a21d-1b38e7225552
author: Shamikg
ms.author: Shamikg
manager: v-pelars
ms.openlocfilehash: 8bc452dff465ca872f094fa7aaaba98612beb135
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63287199"
---
# <a name="advanced-object-selection--oracletosql"></a>Sélection d’objet avancée (OracleToSQL)
Le **Section avancé de l’objet** boîte de dialogue vous permet de filtrer les objets de base de données à l’aide de chaînes et des sous-chaînes dans le nom d’objet, puis sélectionnez ou désélectionnez ces objets. SSMA effectue des opérations de conversion et la migration sur les objets sélectionnés.  
  
Pour accéder à cette boîte de dialogue, avec le bouton droit dans l’Explorateur de métadonnées, puis sélectionnez **sélection avancée de l’objet**.  
  
Lorsque vous ouvrez la boîte de dialogue, cliquez sur **afficher les éléments de sous-catégories** pour afficher tous les objets qui ont des métadonnées chargées dans le projet. Vous pouvez ensuite entrer des chaînes pour filtrer les éléments. Par exemple, entrez la chaîne « company » pour afficher tous les éléments avec des noms qui incluent cette chaîne.  
  
Avant d’utiliser cette boîte de dialogue, vous souhaiterez forcer SSMA pour charger toutes les métadonnées par la conversion de schémas ou de l’enregistrement du projet.  
  
## <a name="options"></a>Options  
**Activer tous les éléments**  
Ajoute une case à cocher en regard de tous les éléments. Ces éléments sont immédiatement sélectionnés dans l’Explorateur de métadonnées.  
  
**Désactiver tous les éléments**  
Supprime la case à cocher en regard de tous les éléments. Ces éléments seront effacés immédiatement dans l’Explorateur de métadonnées.  
  
**Mode d’affichage de liste**  
Affiche les éléments dans une liste filtrés.  
  
**Mode d’affichage de table**  
Affiche les éléments dans une table filtrés.  
  
**Affiche les éléments chargés uniquement**  
Active ou désactive l’affichage des catégories ou des éléments. Lorsque cette case est activée, SSMA montre tous les éléments qui correspondent aux critères de filtre et ceux qui ont été précédemment chargée. Lorsque cette case n’est pas activée, SSMA montre les dossiers de catégorie.  
  
**Filter**  
Entrez la chaîne que vous souhaitez utiliser pour filtrer les éléments. Par exemple, pour rechercher des éléments disponibles qui contiennent la chaîne « ID » dans le nom d’élément, entrez la chaîne « ID » dans le **filtre** boîte.  
  
Si les éléments correspondent au critère de filtre, les catégories ou les éléments apparaîtront à mesure que vous tapez la chaîne. Pour afficher les éléments correspondants, nous recommandons que vous cliquez sur le **affiche uniquement les éléments chargés** bouton.  
  
**Effacer le filtre**  
Efface le **filtre** boîte.  
  
