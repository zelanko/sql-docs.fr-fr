---
title: Terminer la préparation du cas de Test (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Test Case Settings
ms.assetid: 8b2a49b0-4296-4f3f-9e56-323aa6a6fa8e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c3085d17804866015a78e93556dd5373d3a1b8cd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029139"
---
# <a name="finishing-test-case-preparation-sybasetosql"></a>Terminer la préparation du cas de test (SybaseToSQL)
Dernière page de l’Assistant affiche la description du cas de Test et des informations sur les objets impliqués dans le test. En outre, sur cette page vous pouvez définir le test des options d’exécution.  
  
Le **les informations de cas de Test** section indique le nom de cas de Test et la description.  
  
Le **des objets de Test** section contient la liste nommée des objets testés regroupés par type d’objet.  
  
Le **objets affectés à analyser** section affiche la liste nommée d’objets, les modifications de données doivent être comparées après l’exécution d’objets testé.  
  
## <a name="test-case-settings"></a>Paramètres de cas de test  
Dans le **les paramètres de cas de Test** section, vous pouvez définir l’exécution suivante des options de test :  
  
### <a name="stop-test-execution-after-first-failure"></a>Arrêter l’exécution des tests après la première défaillance  
Spécifie pour interrompre le test si une erreur se produit pendant l’exécution du test.  
  
-   Si vous choisissez **Oui**, tester l’exécution s’arrête si une erreur se produit.  
  
-   Si vous choisissez **non**, l’exécution de tests se poursuit après une erreur.  
  
### <a name="perform-data-rollback"></a>Effectuer la restauration de données  
Activer la restauration automatique des données après l’exécution de tests.  
  
-   Si vous choisissez **Oui**, les modifications de données seront perdues après l’exécution de tests.  
  
-   Si vous choisissez **non**, toutes les modifications de données seront enregistrées de l’exécution de test.  
  
### <a name="auxiliary-tables-saving-mode"></a>Mode d’économie de tables auxiliaires  
Définit le mode d’enregistrement pour les tables auxiliaires créé pendant l’exécution du test. Consultez la description de tables auxiliaires dans le [en cours d’exécution de cas de Test &#40;SybaseToSQL&#41; ](../../ssma/sybase/running-test-cases-sybasetosql.md) rubrique.  
  
-   Si vous sélectionnez **toujours enregistrer**, table auxiliaire données doivent toujours être stockées pour une utilisation ultérieure.  
  
-   Si vous sélectionnez **enregistrer en cas d’échec de la comparaison des tables**, les données de table auxiliaire seront stockées uniquement si une erreur se produit.  
  
-   Si vous sélectionnez **toujours supprimer**, tables auxiliaires toujours être supprimées après l’exécution de tests.  
  
-   Si vous sélectionnez **utilisateur poser en cas d’échec de la comparaison des tables**, l’utilisateur peut sélectionner l’action nécessaire si une erreur se produit.  
  
Cliquez sur le **Terminer** bouton pour enregistrer le cas de Test préparée dans [référentiels de Test à l’aide de &#40;SybaseToSQL&#41;](../../ssma/sybase/using-test-repositories-sybasetosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[À l’aide de référentiels de Test &#40;SybaseToSQL&#41;](../../ssma/sybase/using-test-repositories-sybasetosql.md)  
[Cas de Test en cours d’exécution &#40;SybaseToSQL&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Test des objets de base de données migrés &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
