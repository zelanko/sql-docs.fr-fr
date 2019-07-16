---
title: Sélection et la configuration des objets à tester (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Parameter Comparision Setting
- Tester Component,Selecting Objects
ms.assetid: 89c23aad-bfee-4917-bc16-175288390ac0
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 2951d4c3bf1eae73ffd066d796b0e3dda4d28cf6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020966"
---
# <a name="selecting-and-configuring-objects-to-test-sybasetosql"></a>Sélection et configuration des objets à tester (SybaseToSQL)
À ce stade, sélectionner les objets à tester, puis configurez les paramètres pour la comparaison des procédures et fonctions paramètres de sortie, ainsi que les valeurs de retour des fonctions.  
  
## <a name="selection-of-objects-to-test"></a>Sélection d’objets à tester  
Dans l’arborescence d’objets Sybase situé sur le côté gauche de la fenêtre, sélectionnez les objets que vous souhaitez appeler pendant le processus de test. Consultez la liste complète des objets testables dans le [test des objets de base de données migrées &#40;SybaseToSQL&#41; ](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md) rubrique.  
  
Si le testeur de SSMA ne prennent pas en charge les objets sélectionnés pour le test, vous verrez le lien intitulé **certains des objets sélectionnés contiennent des erreurs** sous l’arborescence d’objets. Cliquez sur ce lien pour afficher les raisons pourquoi ces objets ne peuvent pas être testées et pour effacer la sélection d’objets incorrectes.  
  
Sur le côté droit, vous pouvez afficher plusieurs pages le **SQL** page affiche la définition de l’objet en cours. Dans le **Pre SQL** et **Post SQL** pages peuvent spécifier des scripts qui s’exécutent avant et après l’appel du test objet démarre. Il s’agit peut être utile lors de l’objet requiert des objets supplémentaires ces tables temporaires ou les curseurs. Le **paramètres** page répertorie les paramètres si l’objet est une procédure stockée ou une fonction. Le **propriétés** page montre d’autres caractéristiques de l’objet. Consultez la description de **paramètres Comparsions** et **valeurs appeler** pages ci-dessous.  
  
## <a name="parameter-comparison-settings"></a>Paramètres de comparaison  
Établir les règles de comparaison des paramètres de sortie et retourner des valeurs dans le **comparaison des paramètres** page. Vous pouvez rendre les paramètres suivants.  
  
### <a name="use-during-comparisons"></a>Utilisez comparaisons  
Activer à l’aide du paramètre sélectionné dans la comparaison des résultats de test.  
  
-   Si vous choisissez **True**, SSMA compare la valeur de sortie de ce paramètre après l’exécution de la procédure sur Sybase avec la valeur correspondante sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Si vous choisissez**False**, le paramètre sera exclu de la vérification des résultats.  
  
### <a name="use-custom-scale"></a>Utiliser la mise à l’échelle personnalisée  
Pour les paramètres de type de données numérique approximatif et fixe de longueur, vous pouvez définir une échelle personnalisée pour la comparaison.  
  
-   Si vous choisissez **True**, valeurs numériques seront arrondies conformément à la **mise à l’échelle comparaison** valeur avant d’être comparées.  
  
-   Si vous choisissez**False**, la comparaison numérique seront exacte.  
  
### <a name="comparing-scale"></a>Comparaison de mise à l’échelle  
Disponible uniquement si le **Use Custom Scale** option est définie sur **True**. Il s’agit de la précision d’une comparaison numérique.  
  
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
  
-   Si vous choisissez **False**, la comparaison sera respecte la casse.  
  
### <a name="ignore-trailing-spaces"></a>Ignorez les espaces de fin  
Contrôle la façon dont les espaces à droite sont traités au cours de la comparaison.  
  
-   Si vous choisissez **True**, les chaînes comparées seront tronqués à droite avant la comparaison.  
  
-   Si vous choisissez **False**, les chaînes comparées permet de conserver les espaces de fin.  
  
## <a name="specify-input-values-for-procedures-and-functions-call-values"></a>Spécifiez les valeurs d’entrée pour les procédures et fonctions (valeurs appeler)  
Vous pouvez spécifier des valeurs de paramètre d’entrée sur le **valeurs appeler** page. Le **ajouter un appel** bouton ajoute un nouvel appel avec les valeurs de paramètres vide. Le **supprimer appeler** bouton supprime l’appel en cours.  
  
## <a name="next-step"></a>Étape suivante  
[Sélectionner et configurer les objets affectés &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Test des objets de base de données migrés &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
