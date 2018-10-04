---
title: Propriétés du serveur (onglet Service) de rapports | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- configmgr-client
ms.topic: conceptual
ms.assetid: 2a2e1dbf-02b9-4893-aaf0-c0e4a2c9b4f9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 478278f6cc0c097fd8ced85ae42990d31b2578c7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48159019"
---
# <a name="report-server-properties-service-tab"></a>Propriétés de Report Server (onglet Service)
  Ce service est le service [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Report Server. Les valeurs des propriétés en gris clair ne peuvent pas être modifiées à l'aide de cette application.  
  
## <a name="options"></a>Options  
 **Chemin d’accès binaire**  
 Affiche l'emplacement des fichiers programme utilisés par ce service.  
  
 **Contrôle d'erreurs**  
 1 indique « SERVICE_ERROR_NORMAL ». Si le lancement du service échoue pendant le démarrage de l'ordinateur, le programme de démarrage consigne l'erreur et affiche une boîte de message, mais poursuit l'opération de démarrage. Cette valeur ne peut pas être modifiée.  
  
 **Code de sortie**  
 Lorsqu'une erreur se produit, le numéro d'erreur apparaît dans cette zone. Pour dépanner des incidents, recherchez ce numéro dans la Base de connaissances [!INCLUDE[msCoName](../../includes/msconame-md.md)] ou communiquez-le au personnel en charge du support technique.  
  
 **Host Name**  
 Affiche le nom de l'ordinateur ou du cluster exécutant la recherche en texte intégral.  
  
 **Nom**  
 Indique le nom d'affichage du service.  
  
 **ID de processus**  
 Affiche l'ID de processus [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Type de service SQL**  
 Type de service fourni aux processus appelants. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installe plusieurs services.  
  
 **Mode de démarrage**  
 Les options disponibles pour ce service sont les suivantes :  
  
-   Manuel : ce service n'est pas automatiquement lancé au démarrage de l'ordinateur. Vous devez démarrer le service à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou d'un autre outil.  
  
-   Automatique : ce service essaie de se lancer au démarrage de cet ordinateur.  
  
-   Désactivé : ce service ne peut pas être démarré.  
  
 **État**  
 Indique si ce service est en cours d'exécution, arrêté ou désactivé.  
  
## <a name="see-also"></a>Voir aussi  
 [Services SQL Server](../../../2014/tools/configuration-manager/sql-server-services.md)  
  
  
