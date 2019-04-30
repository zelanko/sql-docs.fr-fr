---
title: Mappage des caractères SQL Server et MySQL définie (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 20b3f22e-16a2-4a87-b4eb-c277be6bf5c8
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: cebdf2ed28287a59ec9d4f0daaa1d0c200f8fe20
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63312370"
---
# <a name="mapping-mysql-and-sql-server-character-set-mysqltosql"></a>Mappage des jeux de caractères MySQL et SQL Server (MySQLToSQL)
Jeu de caractères (jeu de caractères) peut être spécifié pour les types de données caractères, les expressions et les littéraux de MySQL.  
  
## <a name="charset-mapping"></a>Mappage de jeu de caractères  
Mappage de jeu de caractères est défini pour chaque jeu de caractères MySQL et utilisé pendant la conversion de type de données caractère. Il spécifie comment convertir des types de données de chaînes de caractères d’un jeu de caractères particulier :  
  
-   Types de caractères national SQL Server (NCHAR/NVARCHAR), ou  
  
-   Types de caractère de SQL Server standard (CHAR/VARCHAR)  
  
1.  **national** sont des types de données de caractères de base de données cible :  
  
    1.  **nchar**  
  
    2.  **nvarchar**  
  
2.  **régulière** sont des types de données de caractères de base de données cible :  
  
    1.  **char**  
  
    2.  **varchar**  
  
3.  Mappage de type autorise uniquement le mappage à **national** types de données character. Une fois que le type de données MySQL caractère est converti en fonction de mappage de type, jeu de caractères est appliqué.  
  
> [!NOTE]  
> Mappage de jeu de caractères peuvent être définies sur chaque niveau de nœud de l’Explorateur d’objets de métadonnées et représentent tous les jeux de caractères lire à partir de MySQL.  
  
## <a name="charset-mapping-on-different-node-levels"></a>Mappage de jeu de caractères sur différents niveaux de nœud  
Mappage de jeu de caractères varie à différents niveaux de nœud, à savoir :  
  
1.  Sur le niveau du nœud de métadonnées racine  
  
2.  Sur la base de données, catégorie et par niveau de nœuds d’objet  
  
> [!NOTE]  
> L’onglet sélectionné à modifier le mappage de jeu de caractères, contient trois boutons, quel que soit le mappage sur les différents niveaux de nœud.  
>   
> Celles-ci sont les suivantes :  
>   
> 1.  **S’appliquent :** Applique les modifications apportées par l’utilisateur est activée uniquement lorsque le mappage de jeu de caractères est modifié et pas encore enregistré.  
> 2.  **Annuler :** Annule les modifications apportées par l’utilisateur. Le bouton est activé lorsque le mappage de jeu de caractères est modifiée, mais pas enregistré.  
> 3.  **Réinitialiser les valeurs par défaut :** Réinitialise tous les mappages de valeurs par défaut.  
  
1.  **Sur le niveau de nœud de métadonnées de racine :**  Grille de mappage de jeu de caractères contient la grille de jeu de caractères avec une colonne distincte pour chaque jeu de caractères. Les colonnes de la grille sont :  
  
    1.  La première colonne de la grille nommée **nom Charset** contient le nom du jeu de caractères.  
  
    2.  La deuxième identité nommée **Description du jeu de caractères** contient la description du jeu de caractères.  
  
    3.  La troisième colonne intitulée, **Type de jeu de caractères cible** contient les paramètres de mappage de jeu de caractères particulier. Les valeurs pour cette colonne sont :  
  
        -   CHAR/VARCHAR  
  
        -   NCHAR/NVARCHAR  
  
    > [!IMPORTANT]  
    > Les valeurs par défaut pour un jeu de caractères particulier ont le préfixe « (valeur par défaut) » après CHAR/VARCHAR ou NCHAR/NVARCHAR.  
  
    Le mappage de jeu de caractères entre la base de données MySQL et de la base de données cible sur le niveau du nœud racine métadonnées est donné ci-dessous :  
  
    ||||  
    |-|-|-|  
    |**Nom du jeu de caractères**|**Description du jeu de caractères**|**Type de jeu de caractères cible (par défaut)**|  
    |big5|Chinois traditionnel Big5|NCHAR/NVARCHAR (valeur par défaut)|  
    |dec8|DEC West Europe|CHAR/VARCHAR (valeur par défaut)|  
    |cp850|Europe de l’ouest de déni de service|CHAR/VARCHAR (valeur par défaut)|  
    |hp8|HP West Europe|CHAR/VARCHAR (valeur par défaut)|  
    |koi8r|KOI8-R Relcom russe|CHAR/VARCHAR (valeur par défaut)|  
    |Latin 1|Europe de l’ouest cp1252|CHAR/VARCHAR (valeur par défaut)|  
    |latin2|Europe centrale ISO 8859-2|CHAR/VARCHAR (valeur par défaut)|  
    |swe7|7 bits suédois|CHAR/VARCHAR (valeur par défaut)|  
    |ascii|US ASCII|CHAR/VARCHAR (valeur par défaut)|  
    |ujis|EUC-JP japonais|NCHAR/NVARCHAR (valeur par défaut)|  
    |SJIS|Shift-JIS japonais|NCHAR/NVARCHAR (valeur par défaut)|  
    |Hébreu|ISO 8859-8 hébreu|CHAR/VARCHAR (valeur par défaut)|  
    |tis620|TIS620 Thai|CHAR/VARCHAR (valeur par défaut)|  
    |eucKR|Coréen EUC-KR|NCHAR/NVARCHAR (valeur par défaut)|  
    |koi8u|KOI8-U ukrainien|CHAR/VARCHAR (valeur par défaut)|  
    |gb2312|GB2312 Chinois simplifié|NCHAR/NVARCHAR (valeur par défaut)|  
    |Grec|ISO 8859-7 grec|CHAR/VARCHAR (valeur par défaut)|  
    |CP 1250|Europe centrale de Windows|CHAR/VARCHAR (valeur par défaut)|  
    |gbk|Chinois simplifié de GBK|NCHAR/NVARCHAR (valeur par défaut)|  
    |Latin5|ISO 8859-9 turc|CHAR/VARCHAR (valeur par défaut)|  
    |armscii8|ARMSCII-8 arménien|CHAR/VARCHAR (valeur par défaut)|  
    |utf8|UTF-8 Unicode|NCHAR/NVARCHAR (valeur par défaut)|  
    |ucs2|UCS-2 Unicode|NCHAR/NVARCHAR (valeur par défaut)|  
    |cp866|Russe de déni de service|CHAR/VARCHAR (valeur par défaut)|  
    |keybcs2|DOS Kamenicky tchèque-slovaque|CHAR/VARCHAR (valeur par défaut)|  
    |macce|Europe centrale Mac|CHAR/VARCHAR (valeur par défaut)|  
    |MacRoman|Europe de l’ouest Mac|CHAR/VARCHAR (valeur par défaut)|  
    |cp852|Déni de service Central européenne|CHAR/VARCHAR (valeur par défaut)|  
    |latin7|ISO 8859-13 Baltique|CHAR/VARCHAR (valeur par défaut)|  
    |CP 1251|Windows Cyrillic|CHAR/VARCHAR (valeur par défaut)|  
    |CP 1256|Arabe de Windows|CHAR/VARCHAR (valeur par défaut)|  
    |CP 1257|Windows Baltic|CHAR/VARCHAR (valeur par défaut)|  
    |binary|Jeu de caractères binaires pseudo|CHAR/VARCHAR (valeur par défaut)|  
    |geostd8|GEOSTD8 géorgien|CHAR/VARCHAR (valeur par défaut)|  
    |cp932|SJIS pour le japonais de Windows|NCHAR/NVARCHAR (valeur par défaut)|  
    |eucjpms|UJIS pour le japonais de Windows|NCHAR/NVARCHAR (valeur par défaut)|  
  
2.  **Sur la base de données, de catégorie ou de niveaux de nœuds d’objet :** Sur le niveau de base de données, catégorie ou les nœuds d’objet, grille de mappage de jeu de caractères contient les mêmes lignes que celle de niveau de métadonnées du nœud racine, reportages. :  
  
    1.  La première colonne de la grille intitulée, **définir un nom de caractère** contient le nom du jeu de caractères.  
  
    2.  La deuxième colonne intitulée, **caractère définir la Description** contient la description du jeu de caractères.  
  
    3.  La seule différence porte sur les valeurs dans la troisième colonne de la grille. La troisième colonne intitulée, **Type de données cible** contient les paramètres de mappage de jeu de caractères particulier. Les valeurs pour la colonne sont :  
  
        -   Hérité (CHAR/VARCHAR ou NCHAR/NVARCHAR)  
  
        -   CHAR/VARCHAR  
  
        -   NCHAR/NVARCHAR  
  
> [!IMPORTANT]  
> -   Dans le mappage de jeu de caractères entre la base de données MySQL et base de données cible sur la base de données, catégorie et niveaux de nœuds d’objet, les valeurs par défaut pour un jeu de caractères particulier sur chaque niveau autre que de la racine de la colonne **Type de données cible** doit être ' Héritée '.  
> -   Dans la grille, la valeur **Inherited** est suivi du suffixe soit '(CHAR/VARCHAR)' ou '(NCHAR/NVARCHAR)' selon quelle valeur a été héritée du parent par ce jeu de caractères particulier.  
  
