---
title: "Comment gérer une Instance de capture de données modifiées | Documents Microsoft"
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
ms.assetid: 5d9e677f-b872-497d-9cde-472184a214ab
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d368fcacfb8e548647785c8b5f6ef5b73b4ef10b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="how-to-manage-a-cdc-instance"></a>Procédure : gérer une instance de capture de données modifiées
  Cette procédure décrit comment utiliser la console du concepteur CDC pour gérer les opérations d'instance de capture de données modifiées au moment de l'exécution.  
  
### <a name="to-manage-cdc-instance-operations"></a>Pour gérer les opérations d'instance de capture de données modifiées  
  
1.  Dans le menu **Démarrer** , sélectionnez **Console du concepteur de capture de données modifiées**.  
  
2.  Dans le volet gauche, développez **Capture de données modifiées** , puis le service qui contient l'instance que vous souhaitez afficher.  
  
3.  Sélectionnez le nom de l'instance à utiliser.  
  
4.  Dans le volet **Actions** à droite de la console du concepteur CDC, cliquez sur l'opération à effectuer.  
  
     Vous pouvez également cliquer avec le bouton droit sur le nom de l'instance dans le volet gauche et sélectionner l'opération à effectuer.  
  
     Vous pouvez effectuer les tâches suivantes :  
  
    -   **Démarrer**: pour démarrer la capture des modifications.  
  
    -   **Arrêter**: pour cesser de capturer des modifications.  
  
    -   **Réinitialiser**: cliquez sur **Réinitialiser** pour rétablir l’état (vide) initial de l’instance de capture de données modifiées. Cette option est disponible lorsque l'instance de capture de données modifiées est arrêtée. Toutes les modifications des tables de modifications et de l'état interne de l'instance de capture de données modifiées sont supprimées. Lorsque l'instance de capture de données modifiées est démarrée ultérieurement, la capture de modifications démarre à partir de ce point et inclut uniquement les transactions qui ont démarré après que l'instance de capture de données modifiées a démarré.  
  
    -   **Supprimer**: pour supprimer l'instance de capture de données modifiées.  
  
    -   **Script de journalisation Oracle**: cliquez sur **Script de journalisation Oracle** pour afficher la boîte de dialogue de script de journalisation Oracle avec le script de journalisation supplémentaire Oracle. Pour plus d'informations sur les opérations réalisables dans cette boîte de dialogue, consultez [Oracle Supplemental Logging Script](../../integration-services/change-data-capture/oracle-supplemental-logging-script.md).  
  
         **Remarque**: lorsque vous exécutez des scripts de journalisation supplémentaires, la boîte de dialogue des informations d'identification Oracle pour l'exécution de script s'ouvre et vous permet de spécifier un nom d'utilisateur et un mot de passe Oracle valides. Pour plus d'informations sur la façon de fournir les informations d'identification Oracle appropriées, consultez [Oracle Credentials for Running Script](../../integration-services/change-data-capture/oracle-credentials-for-running-script.md).  
  
    -   **Déploiement d'instance CDC**: pour générer un script de déploiement de l'instance de capture de données modifiées. Pour plus d'informations sur cette boîte de dialogue, consultez [CDC Instance Deployment Script](../../integration-services/change-data-capture/cdc-instance-deployment-script.md).  
  
     Pour plus d'informations sur ces tâches, consultez [Manage a CDC Instance](../../integration-services/change-data-capture/manage-a-cdc-instance.md).  
  
 Vous pouvez également sélectionner **Propriétés** pour modifier les propriétés de configuration de l'instance de capture de données modifiées. Pour plus d'informations sur la modification des propriétés d'une instance de capture de données modifiées, consultez [Edit Instance Properties](../../integration-services/change-data-capture/edit-instance-properties.md).  
  
  

