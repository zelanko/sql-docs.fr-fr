---
title: Propriétés de canaux nommés | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server]
- listening [SQL Server], pipes
- pipes [SQL Server], listening on pipes
- Named Pipes [SQL Server], listening on pipes
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 8e45e72c16366b08d76cd2431e1d43d613b57828
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47682247"
---
# <a name="named-pipes-properties"></a>Propriétés de Canaux nommés
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Utilisez la page **Protocole**de la boîte de dialogue **Propriétés des canaux nommés** pour afficher ou modifier le canal nommé sur lequel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écoute, pendant l’utilisation du protocole Canaux nommés.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Pour activer ou désactiver le protocole, ou modifier le canal nommé, doit être redémarré.  
  
## <a name="options"></a>Options  
 **Activé**  
 Les valeurs possibles sont **Yes** et **No**.  
  
 **Nom du canal**  
 Spécifie le canal nommé sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écoute. Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est à l'écoute sur `\\.\pipe\sql\query` pour l'instance par défaut et sur `\\.\pipe\MSSQL$<instancename>\sql\query` pour une instance nommée. Ce champ est limité à 2 047 caractères.  
  
## <a name="creating-an-alternate-named-pipe"></a>Création d'un autre canal nommé  
 Pour modifier le canal nommé, tapez le nom du nouveau canal dans la zone **Nom du canal** puis arrêtez et redémarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Étant donné que **sql\query** est connu comme étant le canal nommé utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le fait de modifier ce canal peut permettre de réduire les risques d’attaques par des programmes malveillants.  
  
### <a name="example"></a> Exemple  
 Tapez **\\\\.\pipe\unit\app** pour écouter sur le canal **unit\app** .  
  
 Tapez **\\\\.\pipe\acct** pour écouter sur le canal **acct** .  
  
## <a name="see-also"></a> Voir aussi  
 [Activer ou désactiver un protocole réseau de serveur](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [Choix d'un protocole réseau](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [Création d’une chaîne de connexion valide avec des canaux nommés](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)  
  
  
