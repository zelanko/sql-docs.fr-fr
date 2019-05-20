---
title: Informations d’identification Oracle pour l’exécution d’un script | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4a301cb0-2f5b-41ba-81bf-46b41d07f137
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ae98170e3c6628afc75934cece345bbbfbc22267
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65728644"
---
# <a name="oracle-credentials-for-running-script"></a>Informations d'identification Oracle pour l'exécution d'un script

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Pour exécuter le script de journalisation supplémentaire Oracle à partir de la console du concepteur de capture de données modifiées Oracle, le programme vous invite à entrer les informations d'identification de l'utilisateur Oracle qui exécute le script. Pour exécuter ce script, l'utilisateur Oracle doit disposer de l'autorisation ALTER TABLE pour que toutes les tables soient capturées et de l'autorisation SELECT sur la vue DBA_LOG_GROUPS.  
  
## <a name="task-list"></a>Liste des tâches  
 Entrez les informations suivantes dans cette boîte de dialogue :  
  
 **Authentification**  
  
 Sélectionnez l'une des options suivantes :  
  
-   **Authentification Windows** : sélectionnez cette option pour utiliser les informations d’identification actuelles de domaine Windows. Vous ne pouvez utiliser cette option que si la base de données Oracle est configurée pour utiliser l'authentification Windows.  
  
-   **Authentification Oracle** : si vous sélectionnez cette option, vous devez taper le **Nom d’utilisateur** et le **Mot de passe** de l’utilisateur dans la base de données Oracle source à laquelle vous vous connectez.  
  
## <a name="see-also"></a> Voir aussi  
 [Procédure : gérer une instance de capture de données modifiées](../../integration-services/change-data-capture/how-to-manage-a-cdc-instance.md)   
 [Examiner et générer des scripts de journalisation supplémentaires](../../integration-services/change-data-capture/review-and-generate-supplemental-logging-scripts.md)  
  
  
