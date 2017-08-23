---
title: Journalisation dans le composant de Script | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Script component [Integration Services], logging
ms.assetid: 17c19787-379e-43fe-9107-e36e17ecda53
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 410a2472399574753d67a44b93437b1698c8b086
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="logging-in-the-script-component"></a>Journalisation dans le composant Script
  La journalisation dans des packages [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] vous permet d'enregistrer des informations détaillées sur l'avancement, les résultats et les problèmes d'exécution en enregistrant des événements prédéfinis ou des messages définis par l'utilisateur en vue d'une analyse ultérieure. Le composant Script peut utiliser le <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> méthode de la **ScriptMain** classe pour enregistrer les données définies par l’utilisateur. Si la journalisation est activée et le **ScriptComponentLogEntry** événement est sélectionné pour la journalisation le **détails** onglet de la **configurer les journaux SSIS** boîte de dialogue, un seul appel à la <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> méthode stocke les informations sur les événements de tous les modules fournisseurs d’informations qui ont été configurés pour la tâche de flux de données.  
  
 Voici un exemple simple de journalisation :  
  
 `Dim bt(0) As Byte`  
  
 `Me.Log("Test Log Event", _`  
  
 `0, _`  
  
 `bt)`  
  
> [!NOTE]  
>  Bien qu'il soit possible d'exécuter la journalisation directement à partir du composant Script, il peut être préférable d'implémenter des événements plutôt que la journalisation. L'utilisation d'événements vous permet non seulement d'activer la journalisation des messages d'événements, mais également de répondre à un événement à l'aide de gestionnaires d'événements par défaut ou définis par l'utilisateur.  
  
 Pour plus d’informations sur la journalisation, consultez [Integration Services &#40; SSIS &#41; Journalisation](../../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services &#40; SSIS &#41; Journalisation](../../../integration-services/performance/integration-services-ssis-logging.md)  
  
  
