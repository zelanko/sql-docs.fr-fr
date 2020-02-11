---
title: Propriétés de la mémoire partagée | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bea56ada3ef490225fd08892128abb482b9342a8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62999539"
---
# <a name="shared-memory-properties"></a>Propriétés de Mémoire partagée
  La page **Protocole**de la boîte de dialogue **Propriétés de Mémoire partagée** permet d’activer ou de désactiver le protocole de mémoire partagée. Il s'agit du protocole le plus simple à utiliser et pour lequel aucun paramètre ne doit être configuré. Étant donné que les clients qui utilisent le protocole de mémoire partagée [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent se connecter uniquement à une instance exécutée sur le même ordinateur, il n’est pas utile pour la plupart des activités de base de données. Utilisez le protocole de mémoire partagée pour débloquer une situation dans laquelle vous suspectez que les autres protocoles ne sont pas configurés correctement.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être redémarré pour activer ou désactiver le protocole.  
  
## <a name="options"></a>Options  
 **Activé**  
 Les valeurs possibles sont **Yes** et **No**. Le protocole de mémoire partagée est activé par défaut.  
  
## <a name="see-also"></a>Voir aussi  
 [Choix d'un protocole réseau](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Création d'une chaîne de connexion valide à l'aide du protocole de mémoire partagée](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  
