---
title: Guide pratique pour gérer une instance CDC | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5d9e677f-b872-497d-9cde-472184a214ab
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fd64fe5cad5f85c41830d25dce279ba09915626b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62771167"
---
# <a name="how-to-manage-a-cdc-instance"></a>How to Manage a CDC Instance
  Cette procédure décrit comment utiliser la console du concepteur CDC pour gérer les opérations d'instance de capture de données modifiées au moment de l'exécution.  
  
### <a name="to-manage-cdc-instance-operations"></a>Pour gérer les opérations d'instance de capture de données modifiées  
  
1.  Dans le menu **Démarrer** , sélectionnez **Console du concepteur de capture de données modifiées**.  
  
2.  Dans le volet gauche, développez **Capture de données modifiées** , puis le service qui contient l'instance que vous souhaitez afficher.  
  
3.  Sélectionnez le nom de l'instance à utiliser.  
  
4.  Dans le volet **Actions** à droite de la console du concepteur CDC, cliquez sur l'opération à effectuer.  
  
     Vous pouvez également cliquer avec le bouton droit sur le nom de l'instance dans le volet gauche et sélectionner l'opération à effectuer.  
  
     Vous pouvez effectuer les tâches suivantes :  
  
    -   **Démarrer** : pour lancer la capture des modifications.  
  
    -   **Arrêter** : pour arrêter la capture des modifications.  
  
    -   **Réinitialiser** : Cliquez sur **Réinitialiser** pour rétablir l’état (vide) initial de l’instance de capture de données modifiées. Cette option est disponible lorsque l'instance de capture de données modifiées est arrêtée. Toutes les modifications des tables de modifications et de l'état interne de l'instance de capture de données modifiées sont supprimées. Lorsque l'instance de capture de données modifiées est démarrée ultérieurement, la capture de modifications démarre à partir de ce point et inclut uniquement les transactions qui ont démarré après que l'instance de capture de données modifiées a démarré.  
  
    -   **Supprimer** : pour supprimer l’instance CDC.  
  
    -   **Script de journalisation Oracle** : pour afficher la boîte de dialogue du **script de journalisation Oracle** contenant le script de journalisation supplémentaire Oracle. Pour plus d'informations sur les opérations réalisables dans cette boîte de dialogue, consultez [Oracle Supplemental Logging Script](oracle-supplemental-logging-script.md).  
  
         **Remarque**: Lorsque vous exécutez des scripts de journalisation supplémentaires, la boîte de dialogue des informations d'identification Oracle pour l'exécution de script s'ouvre et vous permet de spécifier un nom d'utilisateur et un mot de passe Oracle valides. Pour plus d'informations sur la façon de fournir les informations d'identification Oracle appropriées, consultez [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md).  
  
    -   **Déploiement d’instance CDC** : pour générer un script de déploiement de l’instance CDC. Pour plus d'informations sur cette boîte de dialogue, consultez [CDC Instance Deployment Script](cdc-instance-deployment-script.md).  
  
     Pour plus d'informations sur ces tâches, consultez [Manage a CDC Instance](manage-a-cdc-instance.md).  
  
 Vous pouvez également sélectionner **Propriétés** pour modifier les propriétés de configuration de l'instance de capture de données modifiées. Pour plus d'informations sur la modification des propriétés d'une instance de capture de données modifiées, consultez [Edit Instance Properties](edit-instance-properties.md).  
  
  
