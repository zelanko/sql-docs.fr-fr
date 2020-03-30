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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 52f4c841d2022216480051576bb0b6da7bdb5d34
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "71286461"
---
# <a name="logging-in-the-script-component"></a>Journalisation dans le composant Script

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  La journalisation dans des packages [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] vous permet d'enregistrer des informations détaillées sur l'avancement, les résultats et les problèmes d'exécution en enregistrant des événements prédéfinis ou des messages définis par l'utilisateur en vue d'une analyse ultérieure. Le composant Script peut utiliser la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> de la classe **ScriptMain** pour enregistrer des données définies par l’utilisateur. Si la journalisation est activée et que l’événement **ScriptComponentLogEntry** est sélectionné pour la journalisation sous l’onglet **Détails** de la boîte de dialogue **Configurer les journaux SSIS**, un seul appel à la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> stocke les informations sur l’événement dans tous les modules fournisseurs d’informations configurés pour la tâche de flux de données.  
  
 Voici un exemple simple de journalisation :  
  
 `Dim bt(0) As Byte`  
  
 `Me.Log("Test Log Event", _`  
  
 `0, _`  
  
 `bt)`  
  
> [!NOTE]  
>  Bien qu'il soit possible d'exécuter la journalisation directement à partir du composant Script, il peut être préférable d'implémenter des événements plutôt que la journalisation. L'utilisation d'événements vous permet non seulement d'activer la journalisation des messages d'événements, mais également de répondre à un événement à l'aide de gestionnaires d'événements par défaut ou définis par l'utilisateur.  
  
 Pour plus d’informations sur la journalisation, consultez [Journalisation Integration Services &#40;SSIS&#41;](../../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Journalisation Integration Services &#40;SSIS&#41;](../../../integration-services/performance/integration-services-ssis-logging.md)  
  
  
