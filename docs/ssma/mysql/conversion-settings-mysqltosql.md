---
title: Paramètres de conversion (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f551cf6e-1575-4206-9cca-975b5b43a6b8
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: debdd549dc010f7be6b9d9b37a4caf649d4e106a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68103125"
---
# <a name="conversion-settings-mysqltosql"></a>Paramètres de conversion (MySQLToSQL)
Le **'Paramètres'** onglet permet à l’utilisateur définir les paramètres au niveau du nœud. L’onglet seront disponible sur les nœuds de la métabase suivants :  
  
-   Nœud de base de données  
  
-   Catégorie de fonctions  
  
-   Nœud de fonction  
  
-   Catégorie de tables  
  
-   Nœud de table  
  
## <a name="specifications"></a>Spécifications :  
Le **paramètres** onglet a deux paramètres d’utilisateur, reportages. :  
  
1.  Conversion de la fonction  
  
2.  Conversion de la table  
  
Ces paramètres seront disponibles sur le type de nœud de la métabase. Par exemple, Conversion de la fonction liés définition ne sera pas disponible au niveau du nœud de Table  
  
> [!NOTE]  
> -   Les modifications apportées par l’utilisateur seront enregistrées dans l’espace de travail du projet comme un fichier de préférences distinct.  
> -   L’extension de ce fichier sera **ccprefs**.  
  
1.  **Paramètre de Conversion de fonction :**  
  
    1.  Cet onglet contient **'Force la conversion de la fonction'** option. L’option peut avoir une des quatre valeurs suivantes :  
  
        -   Convertir en fonction des paramètres de projet [héritées]  
  
        -   Toujours convertir une fonction  
  
        -   Toujours convertir une procédure  
  
        -   Convertir en fonction des paramètres de projet  
  
    2.  En fonction des paramètres, la fonction passera à une fonction ou à une procédure stockée.  
  
    3.  Les paramètres définis par l’utilisateur sont enregistrés dans le fichier de préférences en cascade lorsque vous cliquez sur **appliquer** bouton.  
  
2.  **Paramètre de Conversion de table :**  
  
    1.  Cet onglet contient **« Génération de colonne auxiliaire ROWID supprimer »** option. L’option peut avoir une des quatre valeurs suivantes :  
  
        -   Convertir en fonction des paramètres de projet [héritées]  
  
        -   Oui  
  
        -   Non  
  
        -   Convertir en fonction des paramètres de projet  
  
    2.  Si **'Yes'** , ce paramètre interdit la création de la création de colonne auxiliaire ROWID sur les tables cibles.  
  
    3.  Les paramètres définis par l’utilisateur sont enregistrés dans le fichier de préférences en cascade lorsque vous cliquez sur **appliquer** bouton.  
  
## <a name="see-also"></a>Voir aussi  
[Paramètres du projet (Conversion) (MySQL to SQL)](https://msdn.microsoft.com/7ad5fe44-6445-4ba8-a457-5af792631f11)  
  
