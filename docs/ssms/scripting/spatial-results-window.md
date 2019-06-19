---
title: Fenêtre Résultats spatiaux | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3dc51511120b05c8f4a720a911da6c2b6480fb9d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65821941"
---
# <a name="spatial-results-window"></a>Fenêtre Résultats spatiaux
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
 Affichez les données géographiques dans un des quatre projections : Équirectangulaire, de Mercator, de Robinson ou de Bonne.  
  
 Cette option n'est pas disponible pour les données géométriques.  
  
 **Zoom**  
 Ajustez l'affichage du mappage sur une échelle exponentielle.  
  
 **Afficher le quadrillage**  
 Activez/désactivez le quadrillage des coordonnées.  
  
 Pour les formes polygonales, l'étiquette est affichée uniquement lorsque la forme est suffisamment grande pour contenir le texte d'étiquette. Pour afficher les étiquettes des petites formes, ajustez le zoom.  
  
> [!NOTE]  
>  Il est impossible d'étiqueter les instances de point.  
  
## <a name="see-also"></a> Voir aussi  
 [Afficher des données spatiales dans l'Explorateur d'objets](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md)   
 [Données spatiales &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [Éditeur de requête du moteur de base de données &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)   
 [Éditeurs de texte et de requête &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
