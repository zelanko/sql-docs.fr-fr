---
title: Propriétés de SQL Server Browser (onglet Avancé) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- configmgr-client
ms.topic: conceptual
ms.assetid: ba79137a-cb72-4bf3-a650-e11d02cfce10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 84ef8dc398ce8c2e41fa28794efec5a790994f81
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48192179"
---
# <a name="sql-server-browser-properties-advanced-tab"></a>Propriétés de SQL Server Browser (onglet Avancé)
  Le programme [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser s'exécute sur le serveur en tant que service. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser est à l'écoute des demandes entrantes pour les ressources [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et fournit des informations sur les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées sur l'ordinateur.  
  
## <a name="options"></a>Options  
 **Cluster**  
 Indique si ce service est installé en tant que ressource d'un serveur cluster.  
  
 **Commentaires client**  
 Indique si le contrôle SQM (Service Quality Monitoring) a été activé sur ce service. Pour plus d'informations sur Commentaires client, recherchez dans la documentation en ligne la rubrique « Paramètres des rapports d'erreurs et d'utilisation ».  
  
 **Répertoire de vidage**  
 Emplacement où sont placés les vidages de mémoire en cas d'erreur.  
  
 **Rapport d'erreurs**  
 Quand cette option a pour valeur **Oui**, le programme Dr. Watson transfère les informations à [!INCLUDE[msCoName](../../includes/msconame-md.md)] ou au serveur d'erreur en cas de problème sérieux. Pour plus d'informations sur les rapports d'erreurs, recherchez dans la documentation en ligne la rubrique « Paramètres des rapports d'erreurs et d'utilisation ».  
  
 **ID d'instance**  
 Indique l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui a utilisé cette instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. L’instance par défaut est **MSSQL10_50.MSSQLSERVER**.  
  
## <a name="see-also"></a>Voir aussi  
 [Service SQL Server Browser](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
