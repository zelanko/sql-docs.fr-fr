---
title: Trier des lignes (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sorting rows [SQL Server]
- sorting query results [SQL Server]
ms.assetid: 780ef467-f96e-4373-8235-6dacbedb05a2
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bd8b55519f4edeceb0823c43fe2c25157feed646
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043056"
---
# <a name="sort-rows-visual-database-tools"></a>Trier des lignes (Visual Database Tools)
  Il est possible de choisir l'ordre des lignes qui apparaîtront dans le résultat d'une requête. C'est-à-dire que vous pouvez indiquer dans quelle colonne, ou dans quel ensemble de colonnes, les valeurs seront triées pour déterminer l'ordre d'affichage des lignes dans le jeu de résultats.  
  
> [!NOTE]  
>  L'ordre de tri est déterminé en partie par la séquence de classement de la colonne. Vous pouvez modifier cette séquence dans la [boîte de dialogue Classement](visual-database-tools.md).  
  
 Vous disposez de plusieurs méthodes pour trier les résultats d'une requête :  
  
-   **Vous pouvez demander à trier les lignes par ordre croissant ou décroissant** Par défaut, SQL se réfère aux colonnes de la clause ORDER BY pour trier les lignes selon un ordre croissant. Par exemple, pour trier les titres des livres par ordre croissant de prix, il suffit de trier les lignes selon la colonne du prix. L'instruction SQL obtenue peut se présenter de la manière suivante :  
  
    ```  
    SELECT *  
    FROM titles  
    ORDER BY price  
  
    ```  
  
     Cependant, si vous souhaitez faire apparaître les livres les plus chers en premier, vous pouvez demander un tri décroissant selon le prix. Dans ce cas, vous devez indiquer que les lignes obtenues dans l'ensemble des résultats devront être triées selon la colonne du prix et en ordre décroissant. L'instruction SQL obtenue peut se présenter de la manière suivante :  
  
    ```  
    SELECT *  
    FROM titles  
    ORDER BY price DESC  
  
    ```  
  
-   **Vous pouvez demander un tri sur plusieurs colonnes** Par exemple, il est possible de demander un ensemble de résultats affichant une ligne par auteur et trié selon l'état, puis la ville. L'instruction SQL obtenue peut se présenter de la manière suivante :  
  
    ```  
    SELECT *  
    FROM authors   
    ORDER BY state, city  
  
    ```  
  
-   **Vous pouvez demander un tri en fonction de colonnes qui n'apparaîtront pas dans l'ensemble des résultats** Par exemple, l'ensemble des résultats présentera les livres les plus chers en premier, mais sans faire apparaître les prix. L'instruction SQL obtenue peut se présenter de la manière suivante :  
  
    ```  
    SELECT title_id, title  
    FROM titles  
    ORDER BY price DESC  
  
    ```  
  
-   **Vous pouvez trier en fonction des colonnes dérivées** Par exemple, dans l'ensemble des résultats, chaque ligne contiendra le titre d'un livre, les livres les plus rentables à l'unité étant présentés en premier. L'instruction SQL obtenue peut se présenter de la manière suivante :  
  
    ```  
    SELECT title, price * royalty / 100 as royalty_per_unit  
    FROM titles  
    ORDER BY royalty_per_unit DESC  
  
    ```  
  
     (La formule calculant la rentabilité à l'unité de chaque livre est en gras.)  
  
     Pour calculer une colonne dérivée, vous pouvez utiliser une syntaxe SQL (comme dans l'exemple précédent) ou une fonction définie par l'utilisateur qui retourne une valeur scalaire. Pour plus d'informations sur les fonctions définies par l'utilisateur, consultez la documentation SQL Server.  
  
-   **Vous pouvez trier des lignes groupées** Par exemple, dans l'ensemble des résultats, chaque ligne contiendra une ville et le nombre d'auteurs qui y résident — les villes comprenant le plus grand nombre d'auteurs apparaîtront en premier. L'instruction SQL obtenue peut se présenter de la manière suivante :  
  
    ```  
    SELECT city, state, COUNT(*)  
    FROM authors  
    GROUP BY city, state  
    ORDER BY COUNT(*) DESC, state  
  
    ```  
  
     Remarquez que la requête utilise `state` comme colonne secondaire du tri. De cette manière, si deux états ont le même nombre d'auteurs, vous pouvez les faire apparaître par ordre alphabétique.  
  
-   **Vous pouvez demander un tri en fonction de données internationales** C'est-à-dire que vous pouvez trier une colonne selon des conventions de classement qui diffèrent des conventions utilisées par défaut pour cette colonne. Par exemple, une requête pourrait demander à extraire tous les titres signés par Jaime Patiño. Pour afficher les titres par ordre alphabétique, vous demanderez à appliquer à la colonne des titres une table de classement espagnole. L'instruction SQL obtenue peut se présenter de la manière suivante :  
  
    ```  
    SELECT title  
    FROM   
        authors   
        INNER JOIN   
            titleauthor   
            ON authors.au_id   
            =  titleauthor.au_id   
            INNER JOIN  
                titles   
                ON titleauthor.title_id   
                =  titles.title_id   
    WHERE   
         au_fname = 'Jaime' AND   
         au_lname = 'Patiño'  
    ORDER BY   
         title COLLATE SQL_Spanish_Pref_CP1_CI_AS  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Trier et grouper les résultats de requête &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Rubriques de procédures relatives à la conception de requêtes et de vues &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  