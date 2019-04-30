---
title: Propriétés de SQL Server (onglet Service) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: e4ae0c6b-6fd8-4325-b54e-1758fc659958
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f79b52e62a8080c70865ae8ebe33d1a8a87faa04
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63237988"
---
# <a name="sql-server-properties-service-tab"></a>Propriétés de SQL Server (onglet Service)
  L’onglet **Service**de la boîte de dialogue **Propriétés de MSSQLSERVER** permet d’afficher ou de spécifier les options suivantes.  
  
## <a name="options"></a>Options  
 **Chemin d'accès binaire**  
 Répertorie l'emplacement des fichiers programme utilisés par ce service.  
  
 **Contrôle d'erreurs**  
 1 indique `SERVICE_ERROR_NORMAL`. Si le lancement du service échoue pendant le démarrage de l'ordinateur, le programme de démarrage consigne l'erreur et affiche une boîte de message, mais poursuit l'opération de démarrage. Cette valeur ne peut pas être modifiée.  
  
 **Code de sortie**  
 Lorsqu'une erreur se produit, le numéro d'erreur apparaît dans cette zone. Pour dépanner des incidents, recherchez ce numéro dans la Base de connaissances [!INCLUDE[msCoName](../../includes/msconame-md.md)] ou communiquez-le au personnel en charge du support technique.  
  
 **Host Name**  
 Affiche le nom de l’ordinateur ou du cluster exécutant le service [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Nom**  
 Indique le nom d'affichage du service.  
  
 **ID de processus**  
 Affiche l'ID de processus Windows.  
  
 **Type de service**  
 Affiche le type de service fourni aux processus appelants. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installe plusieurs services.  
  
 **Mode de démarrage**  
 Les options disponibles pour ce service sont les suivantes :  
  
-   Manuelle : Ce service ne démarre pas automatiquement lorsque l’ordinateur démarre. Vous devez démarrer le service à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou d'un autre outil.  
  
-   Automatique : Ce service essaie de se lancer au démarrage de cet ordinateur.  
  
-   Désactivé : Ce service ne peut pas être démarré.  
  
 **État**  
 Indique si ce service est en cours d'exécution, arrêté ou désactivé. « **…** » indique qu’un changement d’état est en attente.  
  
  
