---
title: Sélectionner et configurer les objets (SybaseToSQL) affectés | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Affected Objects
ms.assetid: a219df74-543a-4aec-aeeb-79f90ac3e2ee
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 48d5305854d214e61036e00ca23a94b85313138a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62667506"
---
# <a name="selecting-and-configuring-affected-objects-sybasetosql"></a>Sélection et configuration des objets affectés (SybaseToSQL)
À cette page, vous pouvez sélectionner les tables et les clés étrangères, les modifications dans lequel doivent être comparées quand SSMA vérifie les résultats de l’exécution pour les objets choisi à l’étape précédente. En outre, vous pouvez personnaliser les paramètres de vérification.  
  
## <a name="selection-of-affected-objects"></a>Sélection des objets affectés  
Dans l’arborescence d’objets Sybase situé sur le côté gauche de la fenêtre, cochez les tables et les clés étrangères, les modifications dans lequel doivent être comparées pour étant identiques.  
  
Si le testeur de SSMA ne peut pas vérifier la valeur d’un de ces objets, vous verrez le lien intitulé **certains des objets sélectionnés contiennent des erreurs** sous l’arborescence d’objets. Cliquez sur ce lien pour afficher les raisons pourquoi ces objets ne peuvent pas être comparées et pour effacer la sélection d’objets incorrectes.  
  
## <a name="table"></a>Table de charge de travail  
L’onglet de la Table contient la vue de grille de la table sélectionnée. La grille contient les informations suivantes sur la table sélectionnée :  
  
-   Nom de la colonne  
  
-   Type de données  
  
-   Précision  
  
-   Échelle  
  
-   Règle  
  
-   Par défaut  
  
-   Identité  
  
-   Nullable  
  
## <a name="sql"></a>SQL  
Onglet SQL contient la table « créer » SQL de la table sélectionnée.  
  
## <a name="data"></a>Données  
Onglet données affiche les données présentes dans la table sélectionnée.  
  
## <a name="properties"></a>Properties  
Onglet Propriétés affiche les propriétés de la table sélectionnée. Les champs suivants sont présents sous l’onglet Propriétés :  
  
-   Création ou dernière modification  
  
-   Nom de l’objet  
  
## <a name="table-comparison-settings"></a>Paramètres de comparaison de table  
Établir des règles de comparaison pour la table sur **Table comparaisons** page. Vous pouvez rendre les paramètres suivants.  
  
### <a name="comparison-mode"></a>Mode de comparaison  
Définit le contenu de la table sur laquelle sera effectuée la comparaison.  
  
-   Si vous sélectionnez **modifications uniquement**, comparaison complète des lignes de la table sera effectuée.  
  
-   Si vous sélectionnez **complète**, sera effectuée la comparaison uniquement pour les lignes qui ont été modifiés.  
  
## <a name="column-comparison-settings"></a>Paramètres de comparaison de colonne  
Établir des règles de comparaison pour les colonnes de table sur **colonne comparaisons** page. Vous pouvez rendre les paramètres suivants.  
  
### <a name="use-during-test-comparisons"></a>Utilisation pendant les comparaisons de tests  
Déterminer si cette colonne fera partie de vérification des résultats de test.  
  
-   Si vous choisissez **True**, SSMA compare le contenu de cette colonne après l’exécution du test sur Sybase avec le contenu de la colonne dans SQL Server.
  
-   Si vous choisissez **False**, la colonne doivent être exclue de vérification des résultats.  
  
### <a name="use-custom-scale"></a>Utiliser la mise à l’échelle personnalisée  
Pour les colonnes de type de données numérique, vous pouvez définir une échelle personnalisée pour la comparaison.  
  
-   Si vous choisissez **True**, valeurs numériques seront arrondies conformément à la **mise à l’échelle comparaison** valeur avant d’être comparées.  
  
-   Si vous choisissez **False**, la comparaison numérique seront exacte.  
  
### <a name="comparing-scale"></a>Comparaison de mise à l’échelle  
  
-   Disponible uniquement si le **Use Custom Scale** option est définie sur **True**. Il s’agit de la précision d’une comparaison numérique.  
  
### <a name="date-time-comparing"></a>Comparaison de date heure  
Définit la date/heure valeurs sont comparées.  
  
-   Si vous sélectionnez **comparer la Date entière**, comparaison complète des valeurs à partir de ces deux plateformes sera effectuée.  
  
-   Si vous sélectionnez **comparer une Date uniquement**, l’heure partie sera ignorée.  
  
-   Si vous sélectionnez **comparer l’heure uniquement**, la date partie sera ignorée.  
  
-   Si vous sélectionnez **millisecondes ignorer**, les résultats seront comparées jusqu'à secondes.  
  
-   Si vous sélectionnez **ignorer la Date et les millisecondes**, le résultat sera uniquement par rapport à la partie heure et il ignore les parties fractionnaires d’une seconde.  
  
### <a name="ignore-strings-case"></a>Ignorer la casse des chaînes  
Contrôle de la casse de la comparaison.  
  
-   Si vous choisissez **True**, la comparaison sera respectent pas la casse.  
  
-   Si vous choisissez **False**, la comparaison en compte de la casse des lettres.  
  
## <a name="comparing-sql"></a>Comparaison de SQL  
Vous pouvez afficher les instructions SELECT, générées par le testeur de SSMA sur le **SQL comparer** page. Le testeur comparera les jeux de résultats de ces instructions sur la ligne par ligne. Chaque ligne d’un jeu de résultats Sybase suivante doit être égale à la ligne suivante du jeu de résultats produit dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Vous pouvez modifier ces instructions SELECT pour effectuer une vérification personnalisée. Pour enregistrer les modifications dans Sybase et dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instructions, utilisez le **appliquer** boutons sous la source et la cible SQL, en conséquence.  
  
## <a name="next-step"></a>Étape suivante  
[Personnalisation de l’ordre des appels &#40;SybaseToSQL&#41;](../../ssma/sybase/customizing-calls-order-sybasetosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Cas de Test en cours d’exécution &#40;SybaseToSQL&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Test des objets de base de données migrés &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
