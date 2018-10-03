---
title: Application SQLAGENT90 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- starting SQL Server Agent
- sqlagent90 application
- SQL Server Agent, starting
- command prompt utilities [SQL Server], sqlagent90
ms.assetid: e8b80e8d-d0c9-4500-a868-0ce08233da08
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9df8a9a63697f6fdc2cdf75b468dcb8e39b4eb4a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678447"
---
# <a name="sqlagent90-application"></a>application sqlagent90
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L’application **sqlagent90** démarre [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent à partir de l’invite de commandes. En règle générale, l'Agent [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] doit être exécuté à partir de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou en utilisant des méthodes SQL-SMO dans une application. N’exécutez **sqlagent90** à partir de l’invite de commandes que si vous effectuez un diagnostic de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent, ou lorsque vous y êtes invité par votre fournisseur de support principal.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sqlagent90  
-c [-v] [-i instance_name]  
```  
  
## <a name="arguments"></a>Arguments  
 **-c**  
 Indique que l'Agent [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] s'exécute depuis l'invite de commandes et est indépendant du Gestionnaire de contrôle du service Windows. Lorsque **-c** est utilisé, l’Agent [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne peut pas être commandé depuis l’application Services dans les Outils d’administration ni depuis le Gestionnaire de configuration de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Cet argument est obligatoire.  
  
 **-v**  
 Indique que l'Agent [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] s'exécute en mode documenté et inscrit les informations de diagnostic dans la fenêtre de l'invite de commandes. Les informations de diagnostic sont semblables à celles inscrites dans le journal des erreurs de l'Agent [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 **-i** *instance_name*  
 Indique que l’Agent [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] se connecte à l’instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nommée qui est spécifiée par l’argument *instance_name*.  
  
## <a name="remarks"></a>Notes   
 Après avoir affiché un message de copyright, **sqlagent90** ne présente une sortie dans la fenêtre d’invite de commandes que si le commutateur **-v** a été spécifié. Pour arrêter **sqlagent90**, appuyez sur CTRL+C à l’invite de commandes. Ne fermez pas la fenêtre d’invite de commandes avant d’arrêter **sqlagent90**.  
  
## <a name="see-also"></a> Voir aussi  
 [Tâches d’administration automatisée &#40;SQL Server Agent&#41;](http://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)  
  
  
