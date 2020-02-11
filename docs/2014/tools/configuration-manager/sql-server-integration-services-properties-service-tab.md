---
title: Propriétés de SQL Server Integration Services (onglet Service) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 37f0acd9-c96f-48fd-9b53-2ca0097af242
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d4cb1b821604d125bc81148a06fb613c8547a449
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68186721"
---
# <a name="sql-server-integration-services-properties-service-tab"></a>Propriétés de SQL Server Integration Services (onglet Service)
  L’onglet **Service**de la boîte de dialogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **Properties** dialog box to view or specify the following options.  
  
## <a name="options"></a>Options  
 **Chemin d’accès binaire**  
 Affiche l'emplacement des fichiers programme utilisés par ce service.  
  
 **Contrôle d’erreur**  
 1 indique `SERVICE_ERROR_NORMAL`. Si le lancement du service échoue pendant le démarrage de l'ordinateur, le programme de démarrage consigne l'erreur et affiche une boîte de message, mais poursuit l'opération de démarrage. Cette valeur ne peut pas être modifiée.  
  
 **Code de sortie**  
 Code d’erreur [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows définissant tout problème rencontré au démarrage ou à l’arrêt du service. Cette propriété a pour valeur **ERROR_SERVICE_SPECIFIC_ERROR** (1066) quand l’erreur est unique pour le service représenté par cette classe, et les informations sur l’erreur sont disponibles dans la propriété **ServiceSpecificExitCode** . Le service définit cette valeur à NO_ERROR (0) lors du fonctionnement, et à nouveau lors d'une fin normale.  
  
 **Nom d’hôte**  
 Affiche le nom de l'ordinateur ou du cluster exécutant le service [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 **Nom**  
 Indique le nom d'affichage du service.  
  
 **ID du processus**  
 Affiche l'ID de processus Windows.  
  
 **Type de service SQL**  
 Affiche le type de service fourni aux processus appelants. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installe plusieurs services.  
  
 **Mode de démarrage**  
 Les options disponibles pour ce service sont les suivantes :  
  
-   Manuel : ce service n'est pas automatiquement lancé au démarrage de l'ordinateur. Vous devez démarrer le service à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou d'un autre outil.  
  
-   Automatique : ce service essaie de se lancer au démarrage de cet ordinateur.  
  
-   Désactivé : ce service ne peut pas être démarré.  
  
 **State**  
 Indique si ce service est en cours d'exécution, arrêté ou désactivé. « **…** » indique qu’un changement d’état est en attente.  
  
  
