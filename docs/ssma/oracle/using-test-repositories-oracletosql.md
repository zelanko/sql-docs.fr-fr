---
title: À l’aide de référentiels de Test (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Test Cases Repository
- Test Results Repository
ms.assetid: f941cce4-d3e3-4aeb-a88a-4f101a97a9f4
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 04e58ec9c40f62932c4a711c1e96c0bd4e8162e2
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51666168"
---
# <a name="using-test-repositories-oracletosql"></a>Utilisation de référentiels de tests (OracleToSQL)
Les magasins de référentiel de Test de SSMA SSMA testeur de cas de test et les résultats des tests pour une utilisation ultérieure. Les données de référentiel sont enregistrées dans les tables SQL Server **TestCaseRepository** et **RunTestCaseResultRepository** dans le schéma **ssma_oracle_utilities** de **ssmatesterdb** base de données.  
  
Les boutons suivants sont disponibles dans la boîte de dialogue de référentiel de cas de Test :  
  
-   Cliquez sur le **Actualiser** bouton pour actualiser la liste de cas de Test ou les résultats des tests.  
  
-   Cliquez sur le **fermer** bouton pour fermer la boîte de dialogue de référentiel de cas de Test.  
  
## <a name="test-cases-repository"></a>Référentiel de cas de test  
Vous pouvez afficher le référentiel de cas de Test en cliquant sur **cas de Test...** à partir de la **testeur** menu. SSMA affiche ensuite le **référentiel de cas de Test** boîte de dialogue avec une liste de cas de test enregistrés sur le **cas de Test** page.  
  
La grille affiche les informations suivantes sur chaque cas de test :  
  
-   Nom : Nom de cas de test.  
  
-   Créé : La cas de test date de création.  
  
-   Modifié : Le cas de test date de dernière modification.  
  
-   Description : Les cas de test descriptions.  
  
Les boutons suivants sont disponibles sur la page de cas de Test :  
  
-   Cliquez sur le **ajouter** bouton pour exécuter l’Assistant de cas de Test et créer un nouveau test.  
  
-   Cliquez sur le **supprimer** bouton pour supprimer le test sélectionné à partir du référentiel. Lorsqu’un cas de Test est supprimé, tous les résultats des tests associés sont également supprimés.  
  
-   Cliquez sur le **modifier** bouton pour exécuter l’Assistant de cas de Test et de modifier le test sélectionné.  
  
-   Cliquez sur le **exécuter** bouton pour ouvrir la [en cours d’exécution de cas de Test (OracleToSQL)](https://msdn.microsoft.com/fc208cdb-7373-4f6b-8f6c-cdff9d3dcd02) boîte de dialogue et exécuter le test sélectionné.  
  
## <a name="test-results-repository"></a>Référentiel des résultats des tests  
Vous pouvez afficher le référentiel des résultats des tests sur le **résultats des tests** page de la **référentiel de cas de Test** fenêtre. Ouvrez-le en cliquant sur **résultats des tests...** à partir de la **testeur** menu.  
  
Vous pouvez utiliser deux filtres sur **résultats des tests** page :  
  
-   Le filtre de nom de cas de Test : permet de choisir les résultats des tests par nom de cas de test. De ce filtre **tous les cas de Test** valeur permet d’afficher les résultats des tests pour tous les cas de test.  
  
-   Le filtre de Date de l’exécution de cas de Test : filtres de résultats des tests selon la date de l’enregistrement. De ce filtre **période tous les** valeur autorise l’affichage des résultats des tests pour n’importe quelle date de l’enregistrement.  
  
Les informations suivantes sur les résultats des tests s’affiche dans la grille.  
  
-   Nom : nom de cas de Test.  
  
-   Enregistré : Date de cas de l’enregistrement du Test.  
  
-   Résultats : Un bref résumé de l’exécution du test (info-bulle de cette cellule affiche un résumé complet de l’exécution de tests).  
  
Les boutons suivants sont disponibles sur la page des résultats de Test :  
  
-   Cliquez sur le **vue** bouton pour ouvrir [affichage de rapports de cas de Test &#40;OracleToSQL&#41; ](../../ssma/oracle/viewing-test-case-reports-oracletosql.md) de résultat de cas de Test actuel.  
  
-   Cliquez sur le **supprimer** bouton pour supprimer le résultat du Test sélectionné  
  
## <a name="see-also"></a>Voir aussi  
[Cas de Test en cours d’exécution &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Test des objets de base de données migrés &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
