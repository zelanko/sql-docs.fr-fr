---
title: Implémentation du package parent | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- parent packages [Integration Services]
ms.assetid: d8f94830-fa27-4151-88df-cbdc6bf0fc80
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2cec1f30ba728f1cf3b808acb2fb362e21d259a4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66058154"
---
# <a name="implementation-of-the-parent-package"></a>Implémentation du package parent
  Lors d'un équilibrage de charge de packages SSIS entre serveurs, l'étape suivante après la création et le déploiement des packages enfants, puis la création des travaux de SQL Server Agent distants pour les exécuter, consiste à créer le package parent. Le package parent contient de nombreuses tâches Exécuter le travail de SQL Server Agent, chaque tâche étant responsable de l'appel d'un travail de SQL Server Agent qui exécute l'un des packages enfants. Les tâches Exécuter le travail de SQL Server Agent dans le package parent exécutent les différents travaux de SQL Server Agent. Chaque tâche dans le package parent contient des informations précisant notamment comment établir la connexion au serveur distant et quel travail exécuter sur ce serveur. Pour plus d'informations, consultez [Execute SQL Server Agent Job Task](control-flow/execute-sql-server-agent-job-task.md).  
  
 Pour identifier le package parent qui exécute les packages enfants, dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , cliquez avec le bouton droit sur le package dans l’Explorateur de solutions et sélectionnez **Package de point d’entrée**.  
  
## <a name="listing-child-packages"></a>Liste des packages enfants  
 Si vous déployez votre projet qui contient un package parent et des packages enfants sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , vous pouvez afficher une liste des packages enfants qui sont exécutés par le package parent. Lorsque vous exécutez le package parent, un rapport **Vue d'ensemble** sur ce package est généré automatiquement dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Ce rapport répertorie les packages enfants qui ont été exécutés par la tâche Exécuter le package contenue dans le package parent, comme illustré par l'image ci-dessous.  
  
 ![Rapport Vue d’ensemble avec liste des packages enfants](media/overviewreport-childpackagelisting.png "Rapport Vue d’ensemble avec liste des packages enfants")  
  
 Pour plus d'informations sur l'accès au rapport **Vue d'ensemble** , consultez [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md).  
  
## <a name="precedence-constraints-in-the-parent-package"></a>Contraintes de priorité dans le package parent  
 Lorsque vous créez des contraintes de priorité entre les tâches Exécuter le travail de SQL Server Agent dans le package parent, ces contraintes de priorité contrôlent uniquement le moment de démarrage des travaux de SQL Server Agent sur les serveurs distants. Les contraintes de priorité ne peuvent pas recevoir d'informations sur la réussite ou l'échec des packages enfants qui sont exécutés à partir à des étapes des travaux de SQL Server Agent.  
  
 Cela signifie que le succès ou l'échec d'un package enfant ne se propage pas au parent, puisque la seule fonction de la tâche Exécuter le travail de SQL Server Agent dans le package parent consiste à demander au travail de SQL Server Agent d'exécuter le package enfant. Une fois que le travail de SQL Server Agent a été appelé, le package parent reçoit un résultat de <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success>.  
  
 L'échec de ce scénario signifie uniquement que l'appel de la tâche Exécuter le travail de SQL Server Agent a échoué. Cette situation peut notamment se produire lorsque le serveur distant est hors service et que l'agent ne répond pas. Cependant, tant que l'agent se déclenche, le package a exécuté sa tâche avec succès.  
  
> [!NOTE]  
>  Vous pouvez utiliser une tâche d’exécution SQL qui contient une instruction Transact-SQL **sp_start_job N'nom_package'**. Pour plus d’informations, consultez [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).  
  
## <a name="debugging-environment"></a>Environnement de débogage  
 Lors du test du package parent, utilisez l'environnement de débogage du concepteur en l'exécutant à l'aide des commandes Déboguer / Démarrer le débogage (F5). Vous pouvez également utiliser l'utilitaire d'invite de commandes, **dtexec**. Pour plus d'informations, consultez [Utilitaire dtexec](packages/dtexec-utility.md).  
  
  
