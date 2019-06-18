---
title: Paramètres globaux (testeur) (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4acc0f2a-85ba-4c99-856a-89030f5c418e
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 0cbe66e8298053ef1682e25e97024fa0a96e9abb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62864900"
---
# <a name="global-settings-tester-oracletosql"></a>Paramètres globaux (Testeur) (OracleToSQL)
Utilisez la page de testeur de la **paramètres globaux** boîte de dialogue pour spécifier les paramètres pour un testeur de SSMA.  
  
Accéder aux paramètres testeur, sur le **outils** menu, sélectionnez **paramètres globaux**, puis cliquez sur **testeur** en bas du volet gauche.  
  
## <a name="options"></a>Options  
**Analyse de l’objet testable**  
Ce paramètre spécifie s’il faut exécuter l’analyse des objets Testable. Sélectionnez **Oui** si vous souhaitez que le testeur de SSMA pour analyser et rechercher automatiquement les objets dépendants. Groupe d’options par défaut est **Oui**.  
  
Les options suivantes sont disponibles pour ce paramètre :  
  
1.  Oui  
  
2.  Non  
  
**Mode d’économie de tables auxiliaires**  
Ce paramètre spécifie comment enregistrer les tables auxiliaires internes créées pendant l’exécution de cas de test. Options suivantes peuvent être définies pour ce paramètre particulier :  
  
1.  Toujours supprimer  
  
2.  Toujours enregistrer  
  
3.  Enregistrer en cas d’échec de la comparaison des tables  
  
4.  Demandez à utilisateur si la comparaison de la Table a échoué  
  
Le groupe d’options par défaut est : **Toujours supprimer**.  
  
**Effectuer la restauration de données**  
Ce paramètre spécifie s’il faut exécuter une opération de restauration après l’exécution de chaque cas de test. Groupe d’options par défaut est **non**.  
  
Les options suivantes sont disponibles pour ce paramètre :  
  
1.  Oui  
  
2.  Non  
  
**Arrêter l’exécution des tests après la première défaillance**  
Ce paramètre spécifie s’il faut arrêter le cas de test en cours d’exécution en cours, si une erreur s’est produite lors de l’exécution. Groupe d’options par défaut est **Oui**.  
  
Les options suivantes sont disponibles pour ce paramètre :  
  
1.  Oui  
  
2.  Non  
  
## <a name="see-also"></a>Voir aussi  
[Terminer la préparation du cas de Test &#40;OracleToSQL&#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
  
