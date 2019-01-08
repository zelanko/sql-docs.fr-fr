---
title: Équilibrage de charge de packages sur des serveurs distants à l’aide de SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- load-balancing [Integration Services]
- parent packages [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 9281c5f8-8da3-4ae8-8142-53c5919a4cfe
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 77394dc55b6f8146e9c98ffd55a21bfb41785ec9
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52756451"
---
# <a name="load-balancing-packages-on-remote-servers-by-using-sql-server-agent"></a>Équilibrage de charge de packages sur des serveurs distants à l'aide de l'Agent SQL Server
  Lorsque plusieurs packages doivent être exécutés, il convient d'utiliser d'autres serveurs disponibles. Cette méthode qui consiste à utiliser d'autres serveurs pour exécuter des packages lorsque les packages sont tous sous le contrôle d'un package parent est qualifiée d'équilibrage de charge. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], l'équilibrage de charge est une procédure manuelle qui doit être mise en œuvre par les propriétaires des packages. L'équilibrage de charge n'est pas exécuté automatiquement par les serveurs. En outre, les packages qui sont exécutés sur des serveurs distants doivent être des packages complets, et non des tâches individuelles contenues dans d'autres packages.  
  
 L'équilibrage de charge peut être utile dans les scénarios suivants :  
  
-   Des packages peuvent être exécutés simultanément.  
  
-   Des packages sont volumineux et, s'ils sont exécutés en séquence, peuvent s'exécuter plus longtemps que la période impartie au traitement.  
  
 Les administrateurs et les architectes peuvent déterminer si l'utilisation de serveurs supplémentaires pour le traitement sera avantageuse pour leurs processus.  
  
## <a name="illustration-of-load-balancing"></a>Illustration de l'équilibrage de charge  
 Le schéma ci-dessous représente un package parent sur un serveur. Le package parent contient plusieurs tâches Exécuter le travail de l'Agent SQL Server. Chaque tâche dans le package parent appelle un Agent SQL Server sur un serveur distant. Ces serveurs distants contiennent des travaux de l'Agent SQL Server qui incluent une étape appelant un package sur ce serveur.  
  
 ![Aperçu de l’architecture de l’équilibrage de charge SSIS](../media/loadbalancingoverview.gif "Aperçu de l’architecture de l’équilibrage de charge SSIS")  
  
 Les étapes requises pour l'équilibrage de charge dans cette architecture ne sont pas de nouveaux concepts. L'équilibrage de charge est plutôt obtenu en utilisant autrement des concepts existants et des objets SSIS communs.  
  
## <a name="execution-of-packages-on-a-remote-instance-by-using-sql-server-agent"></a>Exécution de packages sur une instance distante à l'aide de l'Agent SQL Server  
 Dans l'architecture de base pour l'exécution de packages distants, un package central réside sur l'instance de SQL Server qui contrôle les autres packages distants. Le schéma montre ce package central, nommé le SSIS parent. L'instance où réside ce package parent contrôle l'exécution des travaux de l'Agent SQL Server qui s'exécutent sur les packages enfants. Les packages enfants ne sont pas exécutés selon une planification fixe contrôlée par l'Agent SQL Server sur le serveur distant. Les packages enfants sont plutôt démarrés par l'Agent SQL Server lorsqu'ils sont appelés par le package parent et ils s'exécutent sur l'instance de SQL Server sur laquelle réside l'Agent SQL Server.  
  
 Avant que vous puissiez exécuter un package distant à l'aide de l'Agent SQL Server, vous devez configurer les packages parents et enfants et configurer les travaux de l'Agent SQL Server qui contrôlent les packages enfants. Les sections suivantes fournissent d'autres informations sur la création, la configuration, l'exécution et la maintenance de packages exécutés sur des serveurs distants. Ce processus comporte plusieurs étapes :  
  
-   Création des packages enfants et installation de ceux-ci sur des serveurs distants.  
  
-   Création des travaux de l'Agent SQL Server sur les instances distantes qui exécuteront les packages.  
  
-   Création du package parent.  
  
-   Déterminez le scénario de journalisation pour les packages enfants.  
  
 Le tableau suivant fournit des liens vers des rubriques qui vous guideront dans l'ensemble du processus.  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Implémentation de packages enfants](../implementation-of-child-packages.md)|Décrit l'installation de packages, puis la création de travaux de l'Agent SQL Server qui exécutent les packages.|  
|[Implémentation du package parent](../implementation-of-the-parent-package.md)|Décrit la création d'un package parent qui contient plusieurs tâches Exécuter le travail de l'Agent SQL Server. Chaque tâche exécute un des packages enfants.|  
|[Journalisation des packages à charge équilibrée sur les serveurs distants](../logging-for-load-balanced-packages-on-remote-servers.md)|Décrit le scénario de journalisation pour les packages distants.|  
  
## <a name="related-tasks"></a>Tâches associées  
 [Planifier un package à l'aide de SQL Server Agent](../schedule-a-package-by-using-sql-server-agent.md)  
  
  
