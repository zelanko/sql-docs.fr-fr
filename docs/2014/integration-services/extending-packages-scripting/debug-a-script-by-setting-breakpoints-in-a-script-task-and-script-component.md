---
title: Déboguer un script en définissant des points d’arrêt dans une tâche de script et un composant de script| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- breakpoints [Integration Services]
- scripts [Integration Services], breakpoints
ms.assetid: 6c03464f-3f7d-4882-b7f8-8e396f8e2944
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 3a05344f1fc20e575566d0a0fa527ac64b32363f
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968399"
---
# <a name="debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component"></a>Déboguer un script en définissant des points d'arrêt dans une tâche de script et un composant de script
  Cette section décrit la procédure de définition des points d'arrêt dans les scripts utilisés dans la tâche de script et le composant de script.  
  
 Une fois que vous avez défini des points d’arrêt dans le script, la boîte de dialogue **définir les points d’arrêt- \<object name> ** répertorie les points d’arrêt, ainsi que les points d’arrêt intégrés.  
  
> [!IMPORTANT]  
>  Dans certains cas, les points d'arrêt de la tâche de script et le composant de script sont ignorés. Pour plus d’informations, consultez la section **débogage de la tâche de script** dans [codage et débogage de la tâche de script](../control-flow/script-task.md) et la section **débogage du composant script** dans [codage et débogage du composant Script] (.. /extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md.  
  
### <a name="to-set-a-breakpoint-in-script"></a>Pour définir un point d'arrêt dans un script  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Double-cliquez sur le package qui contient le script dans lequel vous souhaitez définir des points d'arrêt.  
  
3.  Pour ouvrir la tâche de script, cliquez sur l’onglet **Flux de contrôle**, puis double-cliquez sur la tâche de script.  
  
4.  Pour ouvrir le composant de script, cliquez sur l’onglet **Flux de données**, puis double-cliquez sur le composant de script.  
  
5.  Cliquez sur **Script**, puis sur **Modifier le script**.  
  
6.  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA), recherchez la ligne de script sur laquelle vous voulez définir un point d’arrêt, cliquez dessus avec le bouton droit, pointez sur **Point d’arrêt**, puis sélectionnez **Insérer un point d’arrêt**.  
  
     L'icône du point d'arrêt apparaît sur la ligne de code.  
  
7.  Dans le menu **Fichier** , cliquez sur **Quitter**.  
  
8.  Cliquez sur **OK**.  
  
9. Pour enregistrer le package, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
  
