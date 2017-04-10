---
title: "Execute Process Task Editor (Process Page) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.executeprocesstask.process.f1"
helpviewer_keywords: 
  - "Execute Process Task Editor"
ms.assetid: 0fc22406-e79b-47a4-a7e4-108d4ce6202f
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 31
---
# Execute Process Task Editor (Process Page)
  Utilisez la page **Traiter** de la boîte de dialogue **Éditeur de tâche d'exécution de processus** pour configurer les options qui exécutent le processus. Ces options comprennent l'exécutable à lancer, son emplacement, les arguments de l'invite de commandes et les variables qui fournissent l'entrée et la sortie de capture.  
  
 Pour en savoir plus sur cette tâche, consultez [Execute Process Task](../../integration-services/control-flow/execute-process-task.md).  
  
## Options  
 **RequireFullFileName**  
 Indiquez si la tâche doit échouer si l'exécutable est introuvable à l'emplacement spécifié.  
  
 **Exécutable**  
 Tapez le nom de l'exécutable à lancer.  
  
 **Arguments**  
 Fournissez les arguments de l'invite de commandes.  
  
 **WorkingDirectory**  
 Tapez le chemin du dossier qui contient l’exécutable ou cliquez sur le bouton Parcourir **(...)**, puis recherchez le dossier.  
  
 **StandardInputVariable**  
 Sélectionnez une variable pour fournir l’entrée au processus ou cliquez sur \<**Nouvelle variable...**> pour créer une variable :  
  
 **Rubriques connexes :**[Ajouter une variable](../Topic/Add%20Variable.md)  
  
 **StandardOutputVariable**  
 Sélectionnez une variable pour capturer la sortie du processus ou cliquez sur \<**Nouvelle variable...**> pour créer une variable.  
  
 **StandardErrorVariable**  
 Sélectionnez une variable pour capturer la sortie d’erreur du processus ou cliquez sur \<**Nouvelle variable...**> pour créer une variable.  
  
 **FailTaskIfReturnCodeIsNotSuccessValue**  
 Indiquez si la tâche échoue quand le code de sortie du processus est différent de la valeur spécifiée dans **SuccessValue**.  
  
 **SuccessValue**  
 Spécifiez la valeur retournée par l'exécutable pour indiquer le succès de l'opération. Cette valeur est définie par défaut sur **0**.  
  
 **TimeOut**  
 Spécifiez la durée en secondes de l'exécution du processus. Une valeur **0** indique qu’aucun délai d’attente n’est utilisé et que l’exécution du processus dure tant que ce dernier n’est pas terminé ou tant qu’aucune erreur ne se produit.  
  
 **TerminateProcessAfterTimeOut**  
 Indiquez si le processus doit se terminer après le délai d’attente spécifié par l’option **TimeOut**. Cette option est uniquement disponible si la valeur de l'option **TimeOut** n'est pas **0**.  
  
 **WindowStyle**  
 Spécifiez le style de la fenêtre dans lequel le processus est exécuté.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)  
  
  