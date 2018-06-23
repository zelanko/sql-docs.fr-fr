---
title: Migration des Scripts vers VSTA | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSIS Script task, converting scripts
- Script component [Integration Services], converting scripts
- Script task [Integration Services], converting scripts
- SSIS Script component, converting scripts
ms.assetid: d685098b-86a1-46bf-939a-63d56951e009
caps.latest.revision: 44
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 99acbad66d2a614431bc1f08ad88bd12f2a3e6b4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153866"
---
# <a name="migrate-scripts-to-vsta"></a>Migrer des scripts vers VSTA
  Lorsque vous mettez à niveau [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] packages [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] migre les scripts dans toutes les tâches de Script ou des composants de Script à [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA). VSTA est l'environnement de script que [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilise. Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], l’environnement de script pour [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] for Applications (VSA).  
  
 Si les scripts des tâches de script ou des composants Script font référence à des interfaces, il se peut que vous deviez modifier ces références avant de mettre le package à niveau. Si vous ne le faites pas, la mise à niveau du package ou la validation des scripts échoue, selon la méthode de mise à niveau choisie. Pour modifier ces références, remplacez les références à IDTS*xxx*90 interfaces avec des références à la IDTS correspondante*xxx*100 interfaces.  
  
 Pour plus d’informations sur la migration des scripts et packages de mise à niveau, consultez [mise à niveau des Packages Integration Services](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
## <a name="understanding-migration-failures"></a>Présentation des échecs de migration  
 Lorsque vous migrez les scripts, la migration peut échouer pour l'une des raisons suivantes :  
  
-   Le point d'entrée du script VSA a été renommé.  
  
     Le point d'entrée spécifie dans la classe `ScriptMain` du projet VSTA la méthode que le runtime [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise comme point d'entrée du code de tâche de script. La classe `ScriptMain` est celle que génèrent par défaut les modèles de script.  
  
-   Le script VSA ne contient aucun point d'entrée ou en contient plusieurs.  
  
-   Des références d'assemblys n'ont pas pu être ajoutées.  
  
-   La classe `ScriptMain` a été modifiée pour hériter d'autres classes en plus de la classe de `ScriptObjectModelSSIS`. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ne prend pas en charge l’héritage multiple.  
  
 Vous ne pouvez pas convertir un script VSA qui utilise [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] à un script VSTA qui utilise [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]. Toutefois, vous pouvez créer un nouveau script VSTA qui utilise [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]. Pour plus d’informations, consultez [Codage et débogage de la tâche de script](../../integration-services/control-flow/script-task.md) et [Codage et débogage du composant Script](../../integration-services/data-flow/transformations/script-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de packages avec des scripts](../../relational-databases/server-management-objects-smo/tasks/scripting.md)  
  
  