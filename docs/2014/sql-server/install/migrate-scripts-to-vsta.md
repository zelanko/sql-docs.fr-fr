---
title: Migrer des scripts vers VSTA | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SSIS Script task, converting scripts
- Script component [Integration Services], converting scripts
- Script task [Integration Services], converting scripts
- SSIS Script component, converting scripts
ms.assetid: d685098b-86a1-46bf-939a-63d56951e009
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: cb44a7b635e24c0c2e3266c1cca98a9c4f6a347c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66093984"
---
# <a name="migrate-scripts-to-vsta"></a>Migrer des scripts vers VSTA
  Lorsque vous mettez [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] à niveau [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]des [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages vers, migre les scripts dans des tâches de script [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ou des composants script vers Tools for Applications (VSTA). VSTA est l'environnement de script que [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilise. Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], l’environnement de script pour [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] for Applications (VSA).  
  
 Si les scripts des tâches de script ou des composants Script font référence à des interfaces, il se peut que vous deviez modifier ces références avant de mettre le package à niveau. Si vous ne le faites pas, la mise à niveau du package ou la validation des scripts échoue, selon la méthode de mise à niveau choisie. Pour modifier ces références, remplacez les références aux interfaces IDTS*xxx*90 par des références aux interfaces IDTS*xxx*100 correspondantes.  
  
 Pour plus d’informations sur la migration des scripts et des packages de mise à niveau, consultez [mettre à niveau des packages Integration Services](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
## <a name="understanding-migration-failures"></a>Présentation des échecs de migration  
 Lorsque vous migrez les scripts, la migration peut échouer pour l'une des raisons suivantes :  
  
-   Le point d'entrée du script VSA a été renommé.  
  
     Le point d'entrée spécifie dans la classe `ScriptMain` du projet VSTA la méthode que le runtime [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise comme point d'entrée du code de tâche de script. La classe `ScriptMain` est celle que génèrent par défaut les modèles de script.  
  
-   Le script VSA ne contient aucun point d'entrée ou en contient plusieurs.  
  
-   Des références d'assemblys n'ont pas pu être ajoutées.  
  
-   La classe `ScriptMain` a été modifiée pour hériter d'autres classes en plus de la classe de `ScriptObjectModelSSIS`. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ne prend pas en charge l’héritage multiple.  
  
 Vous ne pouvez pas convertir un script VSA [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] qui utilise dans un script VSTA [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]qui utilise. Toutefois, vous pouvez créer un nouveau script VSTA qui utilise [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]. Pour plus d’informations, consultez [Codage et débogage de la tâche de script](../../integration-services/control-flow/script-task.md) et [Codage et débogage du composant Script](../../integration-services/data-flow/transformations/script-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de packages avec des scripts](../../relational-databases/server-management-objects-smo/tasks/scripting.md)  
  
  
