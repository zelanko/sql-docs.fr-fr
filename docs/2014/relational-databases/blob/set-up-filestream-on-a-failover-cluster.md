---
title: Configurer FILESTREAM sur un cluster de basculement | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], setting up on a failover cluster
ms.assetid: 6721f780-20b7-4109-8ddb-ac327310699e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9357a345593cd81c420b702a38a02c60da5aebcc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66009921"
---
# <a name="set-up-filestream-on-a-failover-cluster"></a>Configurer FILESTREAM sur un cluster de basculement
  Cette rubrique décrit comment activer FILESTREAM sur un cluster de basculement. Avant d’essayer d’appliquer cette procédure, vous devez comprendre la notion de [clustering de basculement](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md) et activer FILESTREAM. Pour plus d’informations sur l’activation de FILESTREAM, consultez [Activer et configurer FILESTREAM](enable-and-configure-filestream.md).  
  
### <a name="to-set-up-filestream-on-a-failover-cluster"></a>Pour configurer FILESTREAM sur un cluster de basculement  
  
1.  Installez le nœud principal pour le cluster de basculement.  
  
     Une fois l’installation terminée, activez FILESTREAM sur le nœud principal à l’aide du **Gestionnaire de configuration SQL Server**. Cela active les paramètres qui requièrent les privilèges d'administrateur Windows. Si l’accès distant est requis, sélectionnez **Autoriser les clients distants à avoir un accès en continu aux données FILESTREAM**. Cela crée une ressource de cluster de fichiers partagés.  
  
2.  Installez un nœud passif.  
  
     Une fois l’installation terminée, activez FILESTREAM sur le nœud passif à l’aide du **Gestionnaire de configuration SQL Server**. Le nom que vous spécifiez pour **Nom de partage Windows** doit être identique sur tous les nœuds du cluster.  
  
3.  Pour ajouter davantage de nœuds passifs, répétez l'étape 2.  
  
4.  Après avoir ajouté tous les nœuds, terminez le processus en exécutant la procédure stockée sp_configure sur chaque instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  Pour ajouter et activer des nœuds supplémentaires au cluster à tout moment, vous pouvez répéter les étapes 2, 3 et 4.  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Créer un cluster de basculement SQL Server &#40;programme d’installation&#41;](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)   
 [Supprimer une instance de cluster de basculement SQL Server &#40;programme d’installation&#41;](../../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md)   
 [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
  
