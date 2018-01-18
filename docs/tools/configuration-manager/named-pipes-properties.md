---
title: "Propriétés de canaux nommés | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [SQL Server]
- listening [SQL Server], pipes
- pipes [SQL Server], listening on pipes
- Named Pipes [SQL Server], listening on pipes
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
caps.latest.revision: "32"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 72fecdede46024eae399d9a762b0f8cdf7bb3a6b
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="named-pipes-properties"></a>Propriétés de Canaux nommés
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Utilisez le **protocole**page sur le **propriétés de canaux nommés** boîte de dialogue pour afficher ou modifier le canal sur lequel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écoute, lors de l’utilisation du protocole canaux nommés.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]doit être redémarré pour activer ou désactiver le protocole ou modifier le canal nommé.  
  
## <a name="options"></a>Options  
 **Activé**  
 Les valeurs possibles sont **Yes** et **No**.  
  
 **Nom du canal**  
 Spécifie le canal nommé sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écoute. Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est à l'écoute sur `\\.\pipe\sql\query` pour l'instance par défaut et sur `\\.\pipe\MSSQL$<instancename>\sql\query` pour une instance nommée. Ce champ est limité à 2 047 caractères.  
  
## <a name="creating-an-alternate-named-pipe"></a>Création d'un autre canal nommé  
 Pour modifier le canal nommé, tapez le nom du nouveau canal dans la zone **Nom du canal** puis arrêtez et redémarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Étant donné que **sql\query** est connu comme étant le canal nommé utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le fait de modifier ce canal peut permettre de réduire les risques d’attaques par des programmes malveillants.  
  
### <a name="example"></a>Exemple  
 Tapez **\\\\.\pipe\unit\app** pour écouter sur le canal **unit\app** .  
  
 Tapez **\\\\.\pipe\acct** pour écouter sur le canal **acct** .  
  
## <a name="see-also"></a>Voir aussi  
 [Activer ou désactiver un protocole réseau serveur](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [Choix d’un protocole réseau](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [Création d’une chaîne de connexion valide à l’aide de canaux nommés](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)  
  
  
