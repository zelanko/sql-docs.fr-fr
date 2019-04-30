---
title: Paramètres globaux (testeur) (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 6f0b9cea-5a24-4e42-8bbf-c4516b00da23
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 5d9bf2a94146739a743fc4c310ece1d9c4642d11
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63126352"
---
# <a name="global-settings-tester-sybasetosql"></a>Paramètres globaux (Testeur) (SybaseToSQL)
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
[Terminer la préparation du cas de Test &#40;SybaseToSQL&#41;](../../ssma/sybase/finishing-test-case-preparation-sybasetosql.md)  
  
