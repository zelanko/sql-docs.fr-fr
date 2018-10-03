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
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d98e80da1f311292daf3fa275c87e4db5f9cc2e9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48100625"
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
 Tapez le chemin du dossier qui contient l’exécutable ou cliquez sur le bouton Parcourir **(...)** , puis recherchez le dossier.  
  
 **StandardInputVariable**  
 Sélectionnez une variable pour fournir l’entrée au processus ou cliquez sur \<**Nouvelle variable...**> pour en créer une :  
  
 **Rubriques connexes :**[ajouter une Variable  ](../../2014/integration-services/add-variable.md)  
  
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
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Page Expressions](expressions/expressions-page.md)  
  
  
