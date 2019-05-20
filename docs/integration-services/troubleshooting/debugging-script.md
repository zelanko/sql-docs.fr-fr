---
title: Script de débogage | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Script task [Integration Services], debugging
- debugging [Integration Services], scripts
- scripts [Integration Services], debugging
ms.assetid: fddf57d8-8607-4f88-85a0-1b683087b491
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b0b038e81c70e3368e9f66c6dfefc925e282b27d
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65713741"
---
# <a name="debugging-script"></a>Script de débogage

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Vous écrivez les scripts utilisés par la tâche de script et le composant de script dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).  
  
 Vous définissez et écrivez les points d'arrêt dans VSTA. Vous pouvez gérer les points d’arrêt dans VSTA, mais également avec la boîte de dialogue **Définir des points d’arrêt** fournie par le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Pour plus d’informations, consultez [Débogage du flux de contrôle](../../integration-services/troubleshooting/debugging-control-flow.md).  
  
 La boîte de dialogue **Définir des points d’arrêt** inclut les points d’arrêt du script. Ces points d'arrêt apparaissent au bas de la liste des points d'arrêt et mentionnent le numéro de ligne et le nom de la fonction dans laquelle le point d'arrêt apparaît. Vous pouvez supprimer un point d’arrêt de script à partir de la boîte de dialogue **Définir des points d’arrêt** .  
  
 Au moment de l'exécution, les points d'arrêt définis sur des lignes de code dans le script sont intégrés à ceux définis sur le package ou sur les tâches et conteneurs du package. Le débogueur peut s'exécuter à partir d'un point d'arrêt dans le script jusqu'à un point d'arrêt défini sur le package, la tâche ou le conteneur, et inversement. Par exemple, un package peut contenir des points d’arrêt définis sur les conditions d’arrêt qui se produisent quand le package reçoit les événements **OnPreExecute** et **OnPostExecute** , et peut aussi contenir une tâche de script qui contient des points d’arrêt sur des lignes de son script. Dans ce scénario, l’exécution du package peut être suspendue selon la condition d’arrêt associée à l’événement **OnPreExecute** , se poursuivre jusqu’aux points d’arrêt du script, puis continuer jusqu’à la condition d’arrêt associée à l’événement **OnPostExecute** .  
  
 Pour plus d’informations sur le débogage de la tâche de Script et du composant Script, consultez [Codage et débogage de la tâche de script](../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md) et [Codage et débogage du composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="to-set-a-breakpoint-in-visual-studio-for-applications"></a>Pour définir un point d'arrêt dans Visual Studio for Applications  
  
-   [Déboguer un script en définissant des points d'arrêt dans une tâche de script et un composant de script](../../integration-services/extending-packages-scripting/debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Outils de dépannage pour le développement des packages](../../integration-services/troubleshooting/troubleshooting-tools-for-package-development.md)  
  
  
