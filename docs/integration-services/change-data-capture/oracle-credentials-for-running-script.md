---
title: "Informations d’identification Oracle pour l’exécution d’un script | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a301cb0-2f5b-41ba-81bf-46b41d07f137
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: de0535b4b8bf400037726996a86a890374138335
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="oracle-credentials-for-running-script"></a>Informations d'identification Oracle pour l'exécution d'un script
  Pour exécuter le script de journalisation supplémentaire Oracle à partir de la console du concepteur de capture de données modifiées Oracle, le programme vous invite à entrer les informations d'identification de l'utilisateur Oracle qui exécute le script. Pour exécuter ce script, l'utilisateur Oracle doit disposer de l'autorisation ALTER TABLE pour que toutes les tables soient capturées et de l'autorisation SELECT sur la vue DBA_LOG_GROUPS.  
  
## <a name="task-list"></a>Liste des tâches  
 Entrez les informations suivantes dans cette boîte de dialogue :  
  
 **Authentification**  
  
 Sélectionnez l'une des options suivantes :  
  
-   **Authentification Windows**: sélectionnez cette option pour utiliser les informations d'identification actuelles de domaine Windows. Vous ne pouvez utiliser cette option que si la base de données Oracle est configurée pour utiliser l'authentification Windows.  
  
-   **Authentification Oracle**: si vous sélectionnez cette option, vous devez taper le **Nom d'utilisateur** et le **Mot de passe** de l'utilisateur dans la base de données Oracle source à laquelle vous êtes connecté.  
  
## <a name="see-also"></a> Voir aussi  
 [Procédure : gérer une instance de capture de données modifiées](../../integration-services/change-data-capture/how-to-manage-a-cdc-instance.md)   
 [Examiner et générer des scripts de journalisation supplémentaires](../../integration-services/change-data-capture/review-and-generate-supplemental-logging-scripts.md)  
  
  
