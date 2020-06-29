---
title: Éditeur de tâche d’exécution de processus (page traiter) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executeprocesstask.process.f1
helpviewer_keywords:
- Execute Process Task Editor
ms.assetid: 0fc22406-e79b-47a4-a7e4-108d4ce6202f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 51b06136ce1380f04f64bc079f5db41f3d851c8a
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85429176"
---
# <a name="execute-process-task-editor-process-page"></a>Execute Process Task Editor (Process Page)
  Utilisez la page **Traiter** de la boîte de dialogue **Éditeur de tâche d'exécution de processus** pour configurer les options qui exécutent le processus. Ces options comprennent l'exécutable à lancer, son emplacement, les arguments de l'invite de commandes et les variables qui fournissent l'entrée et la sortie de capture.  
  
 Pour en savoir plus sur cette tâche, consultez [Execute Process Task](control-flow/execute-process-task.md).  
  
## <a name="options"></a>Options  
 **RequireFullFileName**  
 Indiquez si la tâche doit échouer si l'exécutable est introuvable à l'emplacement spécifié.  
  
 **Exécutable**  
 Tapez le nom de l'exécutable à lancer.  
  
 **Arguments**  
 Fournissez les arguments de l'invite de commandes.  
  
 **WorkingDirectory**  
 Tapez le chemin d’accès du dossier qui contient l’exécutable ou cliquez sur le bouton Parcourir **(...)** et recherchez le dossier.  
  
 **StandardInputVariable**  
 Sélectionnez une variable pour fournir l’entrée au processus ou cliquez sur \<**New variable...**> pour créer une variable :  
  
 **Rubriques connexes :**  [Ajouter une variable](../../2014/integration-services/add-variable.md)  
  
 **StandardOutputVariable**  
 Sélectionnez une variable pour capturer la sortie du processus ou cliquez sur \<**New variable...**> pour créer une variable.  
  
 **StandardErrorVariable**  
 Sélectionnez une variable pour capturer la sortie d’erreur du processeur ou cliquez sur \<**New variable...**> pour créer une variable.  
  
 **FailTaskIfReturnCodeIsNotSuccessValue**  
 Indiquez si la tâche échoue quand le code de sortie du processus est différent de la valeur spécifiée dans **SuccessValue**.  
  
 **SuccessValue**  
 Spécifiez la valeur retournée par l'exécutable pour indiquer le succès de l'opération. Cette valeur est définie par défaut sur **0**.  
  
 **Expiré**  
 Spécifiez la durée en secondes de l'exécution du processus. Une valeur **0** indique qu’aucun délai d’attente n’est utilisé et que l’exécution du processus dure tant que ce dernier n’est pas terminé ou tant qu’aucune erreur ne se produit.  
  
 **TerminateProcessAfterTimeOut**  
 Indiquez si le processus doit se terminer après le délai d’attente spécifié par l’option **TimeOut** . Cette option est uniquement disponible si la valeur de l'option **TimeOut** n'est pas **0**.  
  
 **WindowStyle**  
 Spécifiez le style de la fenêtre dans lequel le processus est exécuté.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services de référence des erreurs et des messages](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Page Expressions](expressions/expressions-page.md)  
  
  
