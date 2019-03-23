---
title: Informations d’identification Oracle pour l’exécution d’un script | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4a301cb0-2f5b-41ba-81bf-46b41d07f137
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 12de97bf147ccb61cde5f82e2fa31782404071e4
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58388815"
---
# <a name="oracle-credentials-for-running-script"></a>Informations d'identification Oracle pour l'exécution d'un script
  Pour exécuter le script de journalisation supplémentaire Oracle à partir de la console du concepteur de capture de données modifiées Oracle, le programme vous invite à entrer les informations d'identification de l'utilisateur Oracle qui exécute le script. Pour exécuter ce script, l'utilisateur Oracle doit disposer de l'autorisation ALTER TABLE pour que toutes les tables soient capturées et de l'autorisation SELECT sur la vue DBA_LOG_GROUPS.  
  
## <a name="task-list"></a>Liste des tâches  
 Entrez les informations suivantes dans cette boîte de dialogue :  
  
 **Authentification**  
  
 Sélectionnez l'une des options suivantes :  
  
-   **Authentification Windows** : sélectionnez cette option pour utiliser les informations d’identification actuelles de domaine Windows. Vous ne pouvez utiliser cette option que si la base de données Oracle est configurée pour utiliser l'authentification Windows.  
  
-   **Authentification Oracle** : Si vous sélectionnez cette option, vous devez taper le **nom d’utilisateur** et **mot de passe** pour l’utilisateur dans la base de données Oracle Source à laquelle vous vous connectez à.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : gérer une instance de capture de données modifiées](manage-a-cdc-instance.md)   
 [Examiner et générer des scripts de journalisation supplémentaires](review-and-generate-supplemental-logging-scripts.md)  
  
  
