---
title: Fenêtre Résultats spatiaux | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 5a98d82babedc2f60804a1948cd510d59e78b9fe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154355"
---
# <a name="spatial-results-window"></a>Fenêtre Résultats spatiaux
  La fenêtre **Résultats spatiaux** propose des outils de mappage visuel permettant d'afficher des données spatiales. Pour afficher des résultats spatiaux, vos résultats de requête doivent inclure une colonne spatiale avec des données géométriques ou géographiques.  
  
> [!NOTE]  
>  La fenêtre **Résultats spatiaux** est uniquement disponible si vos résultats sont retournés dans une grille dans la fenêtre **Résultats** . Si vous spécifiez que les résultats doivent être retournés sous forme de texte, cette fenêtre n'est pas disponible.  
  
## <a name="options"></a>Options  
 **Sélectionner la colonne spatiale**  
 À partir des colonnes spatiales figurant dans les résultats de requête, spécifiez la colonne spatiale à afficher. Vous ne pouvez sélectionner qu'une seule colonne à la fois.  
  
 **Sélectionner la colonne d'étiquette**  
 À partir des colonnes retournées dans les résultats de requête, spécifiez la colonne non spatiale qui servira à étiqueter les données spatiales. Vous ne pouvez sélectionner qu'une seule colonne à la fois.  
  
 Cette option n'est pas disponible lorsque des instances de point seulement sont retournées dans une requête.  
  
 **Sélectionner la projection**  
 Affichez les données géographiques selon l'une des quatre projections proposées : équirectangulaire, de Mercator, de Robinson ou de Bonne.  
  
 Cette option n'est pas disponible pour les données géométriques.  
  
 **Zoom**  
 Ajustez l'affichage du mappage sur une échelle exponentielle.  
  
 **Afficher le quadrillage**  
 Activez/désactivez le quadrillage des coordonnées.  
  
 Pour les formes polygonales, l'étiquette est affichée uniquement lorsque la forme est suffisamment grande pour contenir le texte d'étiquette. Pour afficher les étiquettes des petites formes, ajustez le zoom.  
  
> [!NOTE]  
>  Il est impossible d'étiqueter les instances de point.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher des données spatiales dans l'Explorateur d'objets](view-spatial-data-in-object-explorer.md)   
 [Données spatiales &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)   
 [Éditeur de requête du moteur de base de données &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md)   
 [Éditeurs de texte et de requête &#40;SQL Server Management Studio&#41;](query-and-text-editors-sql-server-management-studio.md)  
  
  