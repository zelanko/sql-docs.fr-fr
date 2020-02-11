---
title: max full-text crawl range (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- crawls [full-text search]
- max full-text crawl range option
ms.assetid: a49de86b-0891-4dcd-89c0-ead30aab00e0
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a05811b363303e6d68e13faf62d9aca1825b767d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62781694"
---
# <a name="max-full-text-crawl-range-server-configuration-option"></a>max full-text crawl range (option de configuration de serveur)
  Utilisez l’option **max full-text crawl range** pour optimiser l’utilisation du processeur, ce qui permet d’améliorer les performances de l’analyse durant une analyse complète. À l’aide de cette option, vous pouvez spécifier le nombre de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] partitions à utiliser lors d’une analyse complète de l’index. Par exemple, s'il existe plusieurs processeurs et si leur utilisation n'est pas optimale, vous pouvez augmenter la valeur maximale de cette option. En plus de cette option, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise d'autres facteurs, tels que le nombre de lignes d'une table et le nombre de processeurs, pour déterminer le nombre réel de partitions utilisées.  
  
 La valeur par défaut de cette option est 4, la valeur minimale est 1 et la valeur maximale est 256. Les modifications apportées à cette option affectent uniquement les analyses ultérieures. Les analyses en cours d'exécution ne seront pas affectées par une modification de cette option.  
  
 L’option **max full-text crawl range** est une option avancée. Si vous utilisez la procédure stockée système **sp_configure** pour modifier sa valeur, vous ne pouvez modifier l’option **max full-text crawl range** que si l’option **show advanced options** a la valeur 1. Le paramètre prend effet immédiatement (sans redémarrage du serveur).  
  
## <a name="see-also"></a>Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
