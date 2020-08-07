---
title: Paramètres globaux (testeur) (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 6f0b9cea-5a24-4e42-8bbf-c4516b00da23
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: f1ebf6d1122db6b28b13c33320dabef520a40f5a
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87931286"
---
# <a name="global-settings-tester-sybasetosql"></a>Paramètres globaux (Testeur) (SybaseToSQL)
Utilisez la page testeur de la boîte de dialogue **paramètres globaux** pour spécifier les paramètres du testeur SSMA.  
  
Pour accéder aux paramètres du testeur, dans le menu **Outils** , sélectionnez **paramètres globaux**, puis cliquez sur **testeur** en bas du volet gauche.  
  
## <a name="options"></a>Options  
**Analyse des objets testable**  
Ce paramètre spécifie s’il faut exécuter l’analyse des objets testable. Sélectionnez **Oui** si vous souhaitez que SSMA tester analyse et vérifie automatiquement les objets dépendants. L’option par défaut est **Oui**.  
  
Les options suivantes sont disponibles pour ce paramètre :  
  
1.  Oui  
  
2.  Non  
  
**Mode d’enregistrement des tables auxiliaires**  
Ce paramètre spécifie comment enregistrer les tables auxiliaires internes créées au cours de l’exécution du cas de test. Les options suivantes peuvent être définies pour ce paramètre particulier :  
  
1.  Toujours supprimer  
  
2.  Toujours enregistrer  
  
3.  Échec de l’enregistrement de la comparaison des tables  
  
4.  Demander à l’utilisateur si la comparaison de table a échoué  
  
Le groupe d’options par défaut est : **toujours supprimer**.  
  
**Effectuer une restauration des données**  
Ce paramètre spécifie s’il faut effectuer une opération de restauration après l’exécution de chaque cas de test. Le groupe d’options par défaut est **non**.  
  
Les options suivantes sont disponibles pour ce paramètre :  
  
1.  Oui  
  
2.  Non  
  
**Arrêter l’exécution des tests après le premier échec**  
Ce paramètre spécifie s’il faut arrêter le cas de test en cours d’exécution, si une erreur s’est produite lors de l’exécution. L’option par défaut est **Oui**.  
  
Les options suivantes sont disponibles pour ce paramètre :  
  
1.  Oui  
  
2.  Non  
  
## <a name="see-also"></a>Voir aussi  
[Fin de la préparation du cas de test &#40;SybaseToSQL&#41;](../../ssma/sybase/finishing-test-case-preparation-sybasetosql.md)  
  
