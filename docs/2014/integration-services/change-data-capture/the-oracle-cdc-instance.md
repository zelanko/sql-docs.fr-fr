---
title: Instance Oracle CDC | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ed71e8c4-e013-4bf2-8b6c-1e833ff2a41d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 03ccf5f5bae37238e59a0e96b4d53314b0e4906f
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52769091"
---
# <a name="the-oracle-cdc-instance"></a>Instance Oracle CDC
  L'instance Oracle CDC est un processus créé par le service de capture de données modifiées Oracle pour traiter les modifications capturées d'une seule base de données source Oracle. L’instance Oracle CDC récupère sa configuration à partir de la table **cdc.xdbcdc_config** et conserve son état dans la table **cdc.xdbcdc_state** . Ces tables font partie de la base de données CDC, qui définit l'instance Oracle CDC. Pour plus d'informations sur la base de données xdbcdc et les tables, consultez [The CDC Databases](the-oracle-cdc-service.md).  
  
 La section suivante décrit les tâches effectuées par l'instance Oracle CDC :  
  
-   **Vérification du démarrage du service de gestion des**: Au démarrage, l’instance de capture de données modifiées charge sa configuration à partir de la **xdbcdc_config** table et exécute une série de vérifications d’état qui garantissent que l’instance de capture de données modifiées, l’état persistant est cohérent et qu’il peut commencer à traiter modifications.  
  
-   **Préparation pour la capture des modifications**: Lorsque la vérification réussit, l’Instance Oracle CDC analyse toutes les instances de capture actuellement définies et prépare les requêtes Oracle LogMiner et autres structures de prise en charge nécessaires pour la capture des modifications. En outre, l'instance Oracle charge de nouveau l'état interne de capture qui a été enregistré lors de la dernière exécution de l'instance Oracle CDC.  
  
-   **Capture des modifications à partir d’Oracle**: L’Instance Oracle CDC modifications à partir d’Oracle au moyen de la fonctionnalité Oracle logminer, les trie en fonction de la validation de transaction, puis modifie l’heure dans une transaction et les écrit dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] modifier des tables dans la base de données de capture de données modifiées.  
  
-   **Gestion de l’arrêt du service**: Le cycle de vie de l’Instance Oracle CDC est géré par le Service de capture de données modifiées Oracle. Lorsque l'instance Oracle CDC doit s'arrêter, elle effectue les tâches suivantes :  
  
    -   elle cesse de lire dans le journal des transactions Oracle ;  
  
    -   elle cesse d'écrire les transactions Oracle terminées dans la base de données CDC ;  
  
    -   elle attend 30 secondes (si nécessaire) jusqu'à ce que l'écriture de la transaction actuelle soit terminée dans la base de données CDC. Si plus de 30 secondes s'écoulent, l'écriture est annulée et la transaction est restaurée (pour une nouvelle tentative lors du redémarrage de l'instance de capture de données modifiées) ;  
  
    -   dans un thread distinct, elle écrit autant d’enregistrements mis en mémoire cache que possible dans la table de transactions intermédiaires pendant au plus 30 secondes (de la transaction la plus ancienne à la plus récente), puis elle met à jour la table **xdbcdc_state** et valide les modifications.  
  
-   **Gestion des modifications de configuration**: L’Instance Oracle CDC est avertie des modifications de configuration à partir du Service de capture de données modifiées ou la détection d’une nouvelle version dans le **cdc.xdbcdc_config** table. La plupart des modifications ne requièrent pas le redémarrage de l'instance Oracle CDC (par exemple, ajout ou suppression des instances de capture). Toutefois, certaines modifications, telles que la modification de la chaîne de connexion Oracle ou des informations d'identification d'accès requièrent le redémarrage de l'instance de capture de données modifiées.  
  
-   **Gestion de la récupération**: Lorsqu’une Instance Oracle CDC démarre son état interne est restauré à partir de la **xdbcdc_state** et **xdbcdc_staged_transactions** tables. Une fois l'état restauré, l'instance de capture de données modifiées s'exécute de manière habituelle.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs](error-handling.md)  
  
  
