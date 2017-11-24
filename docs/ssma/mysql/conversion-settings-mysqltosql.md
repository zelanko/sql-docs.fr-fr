---
title: "Les paramètres de conversion (MySQLToSQL) | Documents Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: f551cf6e-1575-4206-9cca-975b5b43a6b8
caps.latest.revision: "10"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 29e0343f6f4e254a8171cb1d44084201af34d7d9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="conversion-settings-mysqltosql"></a>Paramètres de conversion (MySQLToSQL)
Le **'Paramètres'** onglet permet à l’utilisateur définir les paramètres de niveau de nœud. L’onglet est seront disponible sur les nœuds de la métabase suivants :  
  
-   Nœud de base de données  
  
-   Catégorie de fonctions  
  
-   Nœud de fonction  
  
-   Tables catégorie  
  
-   Nœud de la table  
  
## <a name="specifications"></a>Spécifications :  
Le **paramètres** onglet possède deux paramètres de l’utilisateur au dixième. :  
  
1.  Conversion de la fonction  
  
2.  Conversion de la table  
  
Ces paramètres seront disponibles en fonction du type de nœud de la métabase. Par exemple, Conversion de la fonction liées définition ne sera pas disponible au niveau du nœud de Table  
  
> [!NOTE]  
> -   Les modifications apportées par l’utilisateur seront enregistrées dans l’espace de travail du projet sous forme de fichier distinct de préférence.  
> -   L’extension de ce fichier sera **ccprefs**.  
  
1.  **Paramètre de Conversion de fonction :**  
  
    1.  Cet onglet contient **'Force la conversion de la fonction'** option. L’option peut avoir une des quatre valeurs suivantes :  
  
        -   Convertir en fonction des paramètres de projet [héritées]  
  
        -   Toujours convertir une fonction  
  
        -   Toujours convertir une procédure  
  
        -   Convertir en fonction des paramètres de projet  
  
    2.  Selon les paramètres, la fonction sera convertie à une fonction ou à une procédure stockée.  
  
    3.  Les paramètres définis par l’utilisateur sont enregistrés dans le fichier de préférences en cascade en cliquant sur **appliquer** bouton.  
  
2.  **Paramètre de Conversion de table :**  
  
    1.  Cet onglet contient **'Génération de colonne auxiliaire ROWID de supprimer'** option. L’option peut avoir une des quatre valeurs suivantes :  
  
        -   Convertir en fonction des paramètres de projet [héritées]  
  
        -   Oui  
  
        -   Non  
  
        -   Convertir en fonction des paramètres de projet  
  
    2.  Si **'Yes'**, ce paramètre empêche la création de la création de colonne auxiliaire ROWID sur les tables cibles.  
  
    3.  Les paramètres définis par l’utilisateur sont enregistrés dans le fichier de préférences en cascade en cliquant sur **appliquer** bouton.  
  
## <a name="see-also"></a>Voir aussi  
[Paramètres du projet (Conversion) (MySQL vers SQL)](http://msdn.microsoft.com/en-us/7ad5fe44-6445-4ba8-a457-5af792631f11)  
  
