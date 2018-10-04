---
title: Modes SQL (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: d840ee51-b863-4e77-84aa-37d3f094bfed
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 46d91efa1451749d8d1cce2b1a8cf361cc30986a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47737307"
---
# <a name="sql-modes-mysqltosql"></a>Modes SQL (MySQLToSQL)
SSMA pour MySQL peut fonctionner dans différents Modes SQL et applique ces modes différemment pour différents clients.  
  
Modes de définissent la syntaxe SQL que MySQL doit prendre en charge, et le genre de validation de données vérifie qu’il doit effectuer. Cela rend plus facile à utiliser MySQL dans différents environnements et à utiliser MySQL avec SQL Server.  
  
## <a name="sql-modes-grid"></a>Grille de Modes SQL :  
  
-   Grille de Modes SQL au niveau racine contient les colonnes suivantes : **nom du Mode SQL**, **chargé les Modes SQL**, et **efficace Modes SQL**.  
  
-   Grille de Modes SQL sur les bases de données catégorie, base de données, Table catégorie, catégorie d’instructions, catégorie de vues, table, vue, fonctions, procédures, UDF et niveau de l’objet événement contient les colonnes suivantes : **nom du Mode SQL**,  **Héritée de Modes SQL**, et **Modes SQL efficace**.  
  
-   Grille de Modes SQL au niveau de la procédure stockée, fonction stockée et déclencheur contient les colonnes suivantes : **nom du Mode SQL**, **les Modes SQL d’origine**, et **efficace Modes SQL**.  
  
> [!NOTE]  
> Modes de groupe seront affichera en gras, sous la colonne 'Nom de Mode SQL'.  
  
## <a name="loaded-sql-modes"></a>Modes SQL chargé  
Voici les Modes SQL, qui sont définies au niveau de la session ou racine. Les Modes SQL une fois chargés dans la base de données cible ne peut pas être modifiés ou édités.  
  
## <a name="inherited-sql-modes"></a>Modes SQL héritées  
Voici les Modes SQL, qui sont héritées à partir du nœud Parent correspondant.  
  
À l’exception de la catégorie de fonctions, procédures, catégorie, catégorie d’événements et les déclencheurs, ces Modes SQL sont présents à tous les niveaux (objet de base de données, Table catégorie, catégorie d’instructions, vues catégorie, table, vue, fonctions, procédures, UDF et événements).  
  
> [!NOTE]  
> En sélectionnant le **hériter du Parent** case à cocher, héritées des Modes SQL peuvent être héritée à partir du nœud parent. Par défaut, cette case à cocher est sélectionné.  
  
## <a name="original-sql-modes"></a>Modes SQL d’origine  
Voici les Modes SQL présents à uniquement les niveaux de fonction, de procédures et de déclencheur.  
  
> [!NOTE]  
> En sélectionnant le **utiliser l’original** vérifier la zone, les Modes SQL qui ont été utilisés à l’origine dans la fonction correspondante ou de procédure ou un déclencheur peut être utilisé. Par défaut, cette case à cocher est sélectionné.  
  
## <a name="effective-sql-modes"></a>Modes SQL efficace  
Efficace Modes SQL peuvent être définis au différents niveaux de la façon suivante :  
  
-   **Au niveau de la session :**  
  
    1.  Tous les Modes SQL chargé peut être appelées, « Modes efficace de SQL ».  
  
    2.  À ce niveau, les modes SQL effectives peuvent être directement et explicitement modifiées.  
  
    3.  Le Mode de SQL efficace qui est défini explicitement ne sont pas reflété comme Mode de SQL chargé et pour finir, est appliqué à l’objet.  
  
-   **Au niveau de la fonction ou procédure ou du déclencheur :**  
  
    1.  Tous les Modes SQL d’origine peut être appelée, « Modes efficace de SQL ».  
  
    2.  À ce niveau, le mode SQL effectif peut être modifié explicitement uniquement lorsque la **utiliser l’original** case à cocher est désactivée.  
  
    3.  Le Mode SQL efficace qui est défini explicitement ne sont pas reflété en tant que Mode SQL d’origine et pour finir, est appliqué à l’objet.  
  
-   **Sur des nœuds autres que de niveau de la fonction ou procédure ou du déclencheur :**  
  
    1.  Tous les Modes SQL héritée peut être appelées, « Modes efficace de SQL ».  
  
    2.  À ce niveau, le mode SQL effectif peut être modifié explicitement uniquement lorsque la **hériter du Parent** case à cocher est désactivée.  
  
    3.  Le Mode SQL efficace qui est défini explicitement ne sont pas reflété en tant que Mode hérité de SQL et pour finir, est appliqué à l’objet.  
  
