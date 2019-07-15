---
title: Propriétés de SQL Server Browser (onglet Avancé) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ba79137a-cb72-4bf3-a650-e11d02cfce10
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: bf0f8a27de07eb61e288fb290041a433a06b3481
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733242"
---
# <a name="sql-server-browser-properties-advanced-tab"></a>Propriétés de SQL Server Browser (onglet Avancé)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
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
 [Service SQL Server Browser](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  
