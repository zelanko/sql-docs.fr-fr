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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103125"
---
# <a name="conversion-settings-mysqltosql"></a>Paramètres de conversion (MySQLToSQL)
L’onglet **« paramètres »** permet à l’utilisateur de définir des paramètres au niveau du nœud. L’onglet sera disponible dans les nœuds de la métabase suivants :  
  
-   Nœud de base de données  
  
-   Catégorie des fonctions  
  
-   Nœud de fonction  
  
-   Catégorie de tables  
  
-   Nœud de table  
  
## <a name="specifications"></a>Spécifications  
L’onglet **paramètres** comporte deux paramètres utilisateur, à savoir :  
  
1.  Conversion de fonction  
  
2.  Conversion de table  
  
Ces paramètres sont disponibles en fonction du type de nœud de la métabase. Par exemple, le paramètre relatif à la conversion des fonctions n’est pas disponible sur le nœud de la table  
  
> [!NOTE]  
> -   Les modifications apportées par l’utilisateur sont enregistrées dans l’espace de travail du projet sous la forme d’un fichier de préférences distinct.  
> -   L’extension de ce fichier sera **ccprefs**.  
  
1.  **Paramètre de conversion de fonction :**  
  
    1.  Cet onglet contient l’option **« conversion forcée des fonctions »** . L’option peut avoir l’une des quatre valeurs suivantes :  
  
        -   Convertir en fonction des paramètres du projet [hérité]  
  
        -   Toujours convertir en fonction  
  
        -   Toujours convertir en procédure  
  
        -   Convertir en fonction des paramètres du projet  
  
    2.  Selon les paramètres, la fonction est convertie en fonction ou en procédure stockée.  
  
    3.  Les paramètres définis par l’utilisateur sont enregistrés dans le fichier de préférences en cascade en cliquant sur le bouton **appliquer** .  
  
2.  **Paramètre de conversion de table :**  
  
    1.  Cet onglet contient l’option **« Supprimer la génération de colonne auxiliaire ROWID »** . L’option peut avoir l’une des quatre valeurs suivantes :  
  
        -   Convertir en fonction des paramètres du projet [hérité]  
  
        -   Oui  
  
        -   Non  
  
        -   Convertir en fonction des paramètres du projet  
  
    2.  Si **'Yes'**, ce paramètre interdit la création de la création de colonne auxiliaire ROWID sur les tables cibles.  
  
    3.  Les paramètres définis par l’utilisateur sont enregistrés dans le fichier de préférences en cascade en cliquant sur le bouton **appliquer** .  
  
## <a name="see-also"></a>Voir aussi  
[Paramètres du projet (conversion) (MySQL vers SQL)](https://msdn.microsoft.com/7ad5fe44-6445-4ba8-a457-5af792631f11)  
  
