---
title: Protocoles clients - Propriétés de Canaux nommés (onglet Protocole) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: b971f59abd9238c74a3c26d6cc019f7c55908326
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68010252"
---
# <a name="client-protocols---named-pipes-properties-protocol-tab"></a>Protocoles clients - Propriétés de Canaux nommés (onglet Protocole)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Dans le Gestionnaire de configuration [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , utilisez l'onglet **Protocole** de la boîte de dialogue **Propriétés de Canaux nommés** pour visualiser ou modifier la description du canal par défaut. Pour vous connecter à un autre canal, tapez son nom dans la zone **Canal par défaut** . Pour plus d'informations sur les chaînes de connexion, consultez [Creating a Valid Connection String Using Named Pipes](https://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f).  
  
## <a name="options"></a>Options  
 **Canal par défaut**  
 Spécifie le canal par défaut que la Net-Library des canaux nommés essaie d'utiliser pour se connecter à l'instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est à l'écoute sur : `\\.\pipe\sql\query`  
  
 Pour vous connecter au canal par défaut, entrez `sql\query`  
  
 **Activé**  
 Les valeurs possibles sont **Yes** et **No**.  
  
## <a name="see-also"></a>Voir aussi  
 [Choix d'un protocole réseau](https://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
