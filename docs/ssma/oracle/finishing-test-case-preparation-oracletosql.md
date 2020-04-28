---
title: Fin de la préparation du cas de test (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 32f38713-7ae4-48d3-980d-74cadc8545a0
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: bc5693c71ac6061f12ee90386b3c135a45a14e09
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68266074"
---
# <a name="finishing-test-case-preparation-oracletosql"></a>Terminer la préparation des cas de test (OracleToSQL)
La dernière page de l’Assistant affiche la description du cas de test et les informations relatives aux objets impliqués dans le test. En outre, sur cette page, vous pouvez définir les options d’exécution des tests.  
  
La section **informations sur les cas de test** affiche le nom et la description du cas de test.  
  
La section **objets sélectionnés pour être testés** contient la liste nommée d’objets testés regroupés par type d’objet.  
  
La section **objets affectés par le test qui sera analysé** affiche la liste nommée des objets dont les modifications de données doivent être comparées après l’exécution des objets testés.  
  
## <a name="test-case-settings"></a>Paramètres de cas de test  
Dans la section **paramètres de cas de test** , vous pouvez définir les options de test d’exécution suivantes :  
  
### <a name="stop-test-execution-after-first-failure"></a>Arrêter l’exécution des tests après le premier échec  
Spécifie de rompre le test si une erreur se produit pendant l’exécution du test.  
  
-   Si vous choisissez **Oui**, l’exécution des tests s’arrête si une erreur se produit.  
  
-   Si vous choisissez **non**, l’exécution des tests se poursuit après une erreur.  
  
### <a name="perform-data-rollback"></a>Effectuer une restauration des données  
Active la restauration automatique des données après l’exécution des tests.  
  
-   Si vous choisissez **Oui**, les modifications apportées aux données seront perdues après l’exécution du test.  
  
-   Si vous choisissez **non**, toutes les modifications apportées aux données d’exécution des tests seront enregistrées.  
  
### <a name="auxiliary-tables-saving-mode"></a>Mode d’enregistrement des tables auxiliaires  
Définit le mode d’enregistrement pour les tables auxiliaires créées pendant l’exécution du test. Consultez la description des tables auxiliaires dans la rubrique [exécution des cas de Test &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md) .  
  
-   Si vous sélectionnez **toujours enregistrer**, les données de la table auxiliaire sont toujours stockées pour une utilisation ultérieure.  
  
-   Si vous sélectionnez **enregistrer en cas d’échec**de la comparaison de tables, les données de la table auxiliaire sont stockées uniquement si une erreur se produit.  
  
-   Si vous sélectionnez **toujours supprimer**, les tables auxiliaires sont toujours supprimées après l’exécution du test.  
  
-   Si vous sélectionnez **demander**à l’utilisateur en cas d’échec de la comparaison de tables, l’utilisateur peut sélectionner l’action nécessaire si une erreur se produit.  
  
Cliquez sur le bouton **Terminer** pour enregistrer le cas de test préparé dans [à l’aide des référentiels de test (OracleToSQL)](https://msdn.microsoft.com/f941cce4-d3e3-4aeb-a88a-4f101a97a9f4).  
  
## <a name="see-also"></a>Voir aussi  
[Utilisation de référentiels de test &#40;OracleToSQL&#41;](../../ssma/oracle/using-test-repositories-oracletosql.md)  
[Exécution de cas de test &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Test des objets de base de données migrés &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
