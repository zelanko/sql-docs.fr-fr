---
title: Terminer la préparation du cas de Test (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 32f38713-7ae4-48d3-980d-74cadc8545a0
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: cd91a80d322fb8048489ffead0bcbbeaf7e00c08
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38984211"
---
# <a name="finishing-test-case-preparation-oracletosql"></a>Terminer la préparation du cas de Test (OracleToSQL)
Dernière page de l’Assistant affiche la description du cas de Test et des informations sur les objets impliqués dans le test. En outre, sur cette page vous pouvez définir le test des options d’exécution.  
  
Le **les informations de cas de Test** section indique le nom de cas de Test et la description.  
  
Le **objets sélectionnés pour être testé** section contient la liste nommée des objets testés regroupés par type d’objet.  
  
Le **objets affectés par Test que vous analyserez** section affiche la liste nommée d’objets, les modifications de données doivent être comparées après l’exécution d’objets testé.  
  
## <a name="test-case-settings"></a>Paramètres de cas de test  
Dans le **les paramètres de cas de Test** section, vous pouvez définir l’exécution suivante des options de test :  
  
### <a name="stop-test-execution-after-first-failure"></a>Arrêter l’exécution des tests après la première défaillance  
Spécifie pour interrompre le test si une erreur se produit pendant l’exécution du test.  
  
-   Si vous choisissez **Oui**, tester l’exécution s’arrête si une erreur se produit.  
  
-   Si vous choisissez **non**, l’exécution de tests se poursuit après une erreur.  
  
### <a name="perform-data-rollback"></a>Effectuer la restauration de données  
Permet la restauration automatique des données après l’exécution de tests.  
  
-   Si vous choisissez **Oui**, les modifications de données seront perdues après l’exécution de tests.  
  
-   Si vous choisissez **non**, toutes les modifications de données seront enregistrées de l’exécution de test.  
  
### <a name="auxiliary-tables-saving-mode"></a>Mode d’économie de tables auxiliaires  
Définit le mode d’enregistrement pour les tables auxiliaires créé pendant l’exécution du test. Consultez la description de tables auxiliaires dans le [en cours d’exécution de cas de Test &#40;OracleToSQL&#41; ](../../ssma/oracle/running-test-cases-oracletosql.md) rubrique.  
  
-   Si vous sélectionnez **toujours enregistrer**, table auxiliaire données doivent toujours être stockées pour une utilisation ultérieure.  
  
-   Si vous sélectionnez **enregistrer en cas d’échec de la comparaison des tables**, les données de table auxiliaire seront stockées uniquement si une erreur se produit.  
  
-   Si vous sélectionnez **toujours supprimer**, tables auxiliaires toujours être supprimées après l’exécution de tests.  
  
-   Si vous sélectionnez **utilisateur poser en cas d’échec de la comparaison des tables**, l’utilisateur peut sélectionner l’action nécessaire si une erreur se produit.  
  
Cliquez sur le **Terminer** bouton pour enregistrer le cas de Test préparée dans [à l’aide de référentiels de Test (OracleToSQL)](http://msdn.microsoft.com/f941cce4-d3e3-4aeb-a88a-4f101a97a9f4).  
  
## <a name="see-also"></a>Voir aussi  
[À l’aide de référentiels de Test &#40;OracleToSQL&#41;](../../ssma/oracle/using-test-repositories-oracletosql.md)  
[Cas de Test en cours d’exécution &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Test des objets de base de données migrés &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
