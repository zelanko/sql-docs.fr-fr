---
title: Paramètres de filtre (Explorateur d'objets et Explorateur de l'utilitaire)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.common.filtersettings.f1
- sql13.ag.job.filtersettings.f1
ms.assetid: 4aab04bc-e1ab-4d4b-ab74-b287fc805bc2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 66ae081ad6fcfb5b5d361201430ea9fb4d8dcd6c
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86001966"
---
# <a name="filter-settings-object-explorer-and-utility-explorer"></a>Paramètres de filtre (Explorateur d'objets et Explorateur de l'utilitaire)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Cette boîte de dialogue vous permet de spécifier un filtre. Un filtre vous permet de configurer l'Explorateur d'objets et l'Explorateur de l'utilitaire pour qu'ils affichent uniquement les éléments qui correspondent à des critères spécifiques. Par exemple, vous pouvez utiliser un filtre pour afficher uniquement les travaux dont le nom contient le mot « Maintenance ». L’en-tête de la boîte de dialogue **Paramètres du filtre** contient le nom du serveur et peut contenir le nom de la base de données.  
  
## <a name="ui-element-list"></a>Liste d’éléments d’interface utilisateur  
**Propriété**  
Indique la propriété sur laquelle filtrer.  
  
**Opérateur**  
Permet de sélectionner la manière dont le filtre applique la valeur à la propriété. Les options suivantes sont possibles :  
  
-   **Égal à**  
  
    Le filtre affiche les éléments pour lesquels la propriété et la valeur correspondent exactement.  
  
-   **Contains**  
  
    Le filtre affiche les éléments pour lesquels la propriété contient la valeur. La propriété peut contenir du texte supplémentaire.  
  
-   **Ne contient pas**  
  
    Le filtre affiche les éléments pour lesquels la propriété ne contient pas la valeur.  
  
-   **Inférieur à**  
  
    Disponible pour les dates, ce filtre affiche les éléments dont la date est antérieure à la valeur fournie.  
  
-   **Inférieur ou égal à**  
  
    Disponible pour les dates, ce filtre affiche les éléments dont la date est antérieure à la valeur fournie ou contient cette valeur.  
  
-   **Supérieur à**  
  
    Disponible pour les dates, ce filtre affiche les éléments dont la date est postérieure à la valeur fournie.  
  
-   **Supérieur ou égal à**  
  
    Disponible pour les dates, ce filtre affiche les éléments dont la date est postérieure à la valeur fournie ou contient cette valeur.  
  
-   **Entre**  
  
    Disponible pour les dates, ce filtre affiche les éléments dont la date est comprise entre deux dates fournies. Sélectionnez **Entre** et appuyez sur Tab pour ajouter une autre ligne afin d’entrer la seconde date.  
  
-   **Non compris entre**  
  
    Disponible pour les dates, ce filtre affiche les éléments dont la date est antérieure ou postérieure aux deux dates fournies. Sélectionnez **Non compris entre** et quittez la colonne **Opérateur** à l’aide des tabulations pour ajouter une ligne afin d’entrer la seconde date.  
  
**Valeur**  
Tapez la valeur à comparer à la propriété. Pour une date, cliquez sur la flèche vers le bas pour afficher un calendrier vous permettant de sélectionner la date.  
  
**Effacer le filtre**  
Supprime tous les paramètres actuels du filtre.  
  
## <a name="see-also"></a>Voir aussi  
[Utiliser SQL Server Management Studio](../../ssms/use-sql-server-management-studio.md)  
[Vue d'ensemble de l'utilitaire SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
