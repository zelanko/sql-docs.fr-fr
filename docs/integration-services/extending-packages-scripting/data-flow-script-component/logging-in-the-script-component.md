---
title: Journalisation dans le composant Script | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], logging
ms.assetid: 17c19787-379e-43fe-9107-e36e17ecda53
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 008e4a98491dad64565b486a565f849e83281036
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58271373"
---
# <a name="logging-in-the-script-component"></a>Journalisation dans le composant Script
  La journalisation dans des packages [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] vous permet d'enregistrer des informations détaillées sur l'avancement, les résultats et les problèmes d'exécution en enregistrant des événements prédéfinis ou des messages définis par l'utilisateur en vue d'une analyse ultérieure. Le composant Script peut utiliser la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> de la classe **ScriptMain** pour enregistrer des données définies par l’utilisateur. Si la journalisation est activée et que l’événement **ScriptComponentLogEntry** est sélectionné pour la journalisation sous l’onglet **Détails** de la boîte de dialogue **Configurer les journaux SSIS**, un seul appel à la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> stocke les informations sur l’événement dans tous les modules fournisseurs d’informations configurés pour la tâche de flux de données.  
  
 Voici un exemple simple de journalisation :  
  
 `Dim bt(0) As Byte`  
  
 `Me.Log("Test Log Event", _`  
  
 `0, _`  
  
 `bt)`  
  
> [!NOTE]  
>  Bien qu'il soit possible d'exécuter la journalisation directement à partir du composant Script, il peut être préférable d'implémenter des événements plutôt que la journalisation. L'utilisation d'événements vous permet non seulement d'activer la journalisation des messages d'événements, mais également de répondre à un événement à l'aide de gestionnaires d'événements par défaut ou définis par l'utilisateur.  
  
 Pour plus d’informations sur la journalisation, consultez [Journalisation Integration Services &#40;SSIS&#41;](../../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Journalisation Integration Services &#40;SSIS&#41;](../../../integration-services/performance/integration-services-ssis-logging.md)  
  
  
