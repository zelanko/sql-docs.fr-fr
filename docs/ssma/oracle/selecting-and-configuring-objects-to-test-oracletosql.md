---
title: Sélection et la configuration des objets à tester (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Selection of Objects to Test,Parameter Comparison Settings
ms.assetid: 29fb6542-5c1f-4b14-a822-87700beb7623
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: d568d1749cd54796072a108e438e448bf2a74578
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62626204"
---
# <a name="selecting-and-configuring-objects-to-test-oracletosql"></a>Sélection et configuration des objets à tester (OracleToSQL)
À ce stade, sélectionner les objets à tester, puis configurez les paramètres pour la comparaison des procédures et fonctions paramètres de sortie, ainsi que les valeurs de retour des fonctions.  
  
## <a name="selection-of-objects-to-test"></a>Sélection d’objets à tester  
Dans l’arborescence des objets Oracle situé sur le côté gauche de la fenêtre, sélectionnez les objets que vous souhaitez appeler pendant le processus de test. Consultez la liste complète des objets testables dans le [test des objets de base de données migrées &#40;OracleToSQL&#41; ](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md) rubrique.  
  
Si le testeur de SSMA ne prennent pas en charge les objets sélectionnés pour le test, vous verrez le lien intitulé **certains des objets sélectionnés contiennent des erreurs** sous l’arborescence d’objets. Cliquez sur ce lien pour afficher les raisons pourquoi ces objets ne peuvent pas être testées et pour effacer la sélection d’objets incorrectes.  
  
Sur le côté droit, vous pouvez afficher plusieurs pages le **SQL** page affiche la définition de l’objet en cours. Le **paramètres** page répertorie les paramètres si l’objet est une procédure stockée ou une fonction. Le **propriétés** page montre d’autres caractéristiques de l’objet. Consultez la description de **paramètre comparaisons** et **valeurs appeler** pages ci-dessous.  
  
## <a name="parameter-comparison-settings"></a>Paramètres de comparaison  
Établir les règles de comparaison des paramètres de sortie et retourner des valeurs dans le **paramètre comparaisons** page. Vous pouvez rendre les paramètres suivants.  
  
### <a name="use-during-test-comparisons"></a>Utilisation pendant les comparaisons de tests  
Activer à l’aide du paramètre sélectionné dans la comparaison des résultats de test.  
  
-   Si vous choisissez **True**, SSMA compare la valeur de sortie de ce paramètre après l’exécution de la procédure sur Oracle avec la valeur correspondante sur SQL Server.
  
-   Si vous choisissez**False**, le paramètre sera exclu de la vérification des résultats.  
  
### <a name="use-custom-scale"></a>Utiliser la mise à l’échelle personnalisée  
Pour les paramètres de type de données numérique, vous pouvez définir une échelle personnalisée pour la comparaison.  
  
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
Vous pouvez spécifier des valeurs de paramètre d’entrée sur le **valeurs appeler** page. Le **ajouter un appel** bouton ajoute un nouvel appel avec les valeurs de paramètres vide. Le **supprimer les appels** bouton supprime l’appel en cours.  
  
## <a name="next-step"></a>Étape suivante  
[Sélectionner et configurer les objets affectés &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Test des objets de base de données migrés &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
