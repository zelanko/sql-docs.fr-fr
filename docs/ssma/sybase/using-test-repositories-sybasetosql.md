---
title: À l’aide de référentiels de Test (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Test Repositories
ms.assetid: c359c25c-db2a-4a20-afa9-62d87a62df72
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 939342a85ed657faa645c593018cbf39042031c2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62625826"
---
# <a name="using-test-repositories-sybasetosql"></a>Utilisation de référentiels de tests (SybaseToSQL)
Les magasins de référentiel de Test de SSMA SSMA testeur de cas de test et les résultats des tests pour une utilisation ultérieure. Les données de référentiel sont enregistrées dans les tables SQL Server **TestCaseRepository** et **RunTestCaseResultRepository** dans le schéma **ssma_sybase_utilities** de **ssmatesterdb_syb** base de données.  
  
Les boutons suivants sont disponibles dans la boîte de dialogue de référentiel de cas de Test :  
  
-   Cliquez sur le **Actualiser** bouton pour actualiser la liste de cas de Test ou les résultats des tests.  
  
-   Cliquez sur le **fermer** bouton pour fermer la boîte de dialogue de référentiel de cas de Test.  
  
## <a name="test-cases-repository"></a>Référentiel de cas de test  
Vous pouvez afficher le référentiel de cas de Test en cliquant sur **cas de Test...**  à partir de la **testeur** menu. SSMA affiche ensuite le **référentiel de cas de Test** boîte de dialogue avec une liste de cas de test enregistrés sur le **cas de Test** page.  
  
La grille affiche les informations suivantes sur chaque cas de test :  
  
-   Nom : Le nom de cas de test.  
  
-   Créé : La date de création de cas de test.  
  
-   Modification : La date de dernière modification du cas de test.  
  
-   Description : Les descriptions de cas de test.  
  
Les boutons suivants sont disponibles sur la page de cas de Test :  
  
-   Cliquez sur le **ajouter** bouton pour exécuter l’Assistant de cas de Test et créer un nouveau test.  
  
-   Cliquez sur le **supprimer** bouton pour supprimer le test sélectionné à partir du référentiel. Lorsqu’un cas de Test est supprimé, tous les résultats des tests associés sont également supprimés.  
  
-   Cliquez sur le **modifier** bouton pour exécuter l’Assistant de cas de Test et de modifier le test sélectionné.  
  
-   Cliquez sur le **exécuter** bouton pour ouvrir la [en cours d’exécution de cas de Test &#40;SybaseToSQL&#41; ](../../ssma/sybase/running-test-cases-sybasetosql.md) boîte de dialogue et exécuter le test sélectionné.  
  
## <a name="test-results-repository"></a>Référentiel des résultats des tests  
Vous pouvez afficher le référentiel des résultats des tests sur le **résultats des tests** page de la **référentiel de cas de Test** fenêtre. Ouvrez-le en cliquant sur **résultats des tests...**  à partir de la **testeur** menu.  
  
Vous pouvez utiliser deux filtres sur **résultats des tests** page :  
  
-   Le filtre de nom de cas de Test : Permet de choisir les résultats des tests par nom de cas de test. De ce filtre **tous les cas de Test** valeur permet d’afficher les résultats des tests pour tous les cas de test.  
  
-   Le filtre de Date de l’exécution de cas de Test : Filtres de résultats des tests selon la date de l’enregistrement. De ce filtre **période tous les** valeur autorise l’affichage des résultats des tests pour n’importe quelle date de l’enregistrement.  
  
Les informations suivantes sur les résultats des tests s’affiche dans la grille.  
  
-   Nom : Nom du cas de test.  
  
-   En route : Date du cas de test en cours d’exécution.  
  
-   Résultat : Un bref résumé de l’exécution du test (info-bulle de cette cellule affiche un résumé complet de l’exécution de tests).  
  
Les boutons suivants sont disponibles sur la page des résultats de Test :  
  
-   Cliquez sur le **vue** bouton pour ouvrir [affichage de rapports de cas de Test &#40;SybaseToSQL&#41; ](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md) de résultat de cas de Test actuel.  
  
-   Cliquez sur le **supprimer** bouton pour supprimer le résultat du Test sélectionné  
  
## <a name="see-also"></a>Voir aussi  
[Cas de Test en cours d’exécution &#40;SybaseToSQL&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Test des objets de base de données migrés &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
