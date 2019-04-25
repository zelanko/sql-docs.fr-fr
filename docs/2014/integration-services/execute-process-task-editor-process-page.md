---
title: Exécuter l’éditeur de tâche de processus (Page processus) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executeprocesstask.process.f1
helpviewer_keywords:
- Execute Process Task Editor
ms.assetid: 0fc22406-e79b-47a4-a7e4-108d4ce6202f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 543ab9724f44e5db1f4532eeadcce79b36de52b5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62769585"
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
 Tapez le chemin du dossier qui contient l’exécutable ou cliquez sur le bouton Parcourir **(...)**, puis recherchez le dossier.  
  
 **StandardInputVariable**  
 Sélectionnez une variable pour fournir l’entrée au processus ou cliquez sur \<**Nouvelle variable...**> pour en créer une :  
  
 **Rubriques connexes :**  [Ajouter une variable](../../2014/integration-services/add-variable.md)  
  
 **StandardOutputVariable**  
 Sélectionnez une variable pour capturer la sortie du processus ou cliquez sur \<**Nouvelle variable...**> pour en créer une.  
  
 **StandardErrorVariable**  
 Sélectionnez une variable pour capturer la sortie d’erreur du processus ou cliquez sur \<**Nouvelle variable...**> pour en créer une.  
  
 **FailTaskIfReturnCodeIsNotSuccessValue**  
 Indiquez si la tâche échoue quand le code de sortie du processus est différent de la valeur spécifiée dans **SuccessValue**.  
  
 **SuccessValue**  
 Spécifiez la valeur retournée par l'exécutable pour indiquer le succès de l'opération. Cette valeur est définie par défaut sur **0**.  
  
 **TimeOut**  
 Spécifiez la durée en secondes de l'exécution du processus. Une valeur **0** indique qu’aucun délai d’attente n’est utilisé et que l’exécution du processus dure tant que ce dernier n’est pas terminé ou tant qu’aucune erreur ne se produit.  
  
 **TerminateProcessAfterTimeOut**  
 Indiquez si le processus doit se terminer après le délai d’attente spécifié par l’option **TimeOut** . Cette option est uniquement disponible si la valeur de l'option **TimeOut** n'est pas **0**.  
  
 **WindowStyle**  
 Spécifiez le style de la fenêtre dans lequel le processus est exécuté.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Page Expressions](expressions/expressions-page.md)  
  
  
