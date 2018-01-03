---
title: Infos express (IntelliSense) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Quick Info option [IntelliSense]
- declarations [IntelliSense]
- IntelliSense [SQL Server], Quick Info
- identifier declarations [IntelliSense]
ms.assetid: 3c8b59f4-1922-4bde-844f-5f2306514d96
caps.latest.revision: "33"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: adcf4b2e0e108a886a3ea24e9b5a225b691dcbcb
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="quick-info-intellisense"></a>Infos express (IntelliSense)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] L’option **Info express** de [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense affiche la déclaration complète de tout identificateur présent dans votre code. Lorsque vous déplacez le pointeur de la souris sur un identificateur, sa déclaration apparaît dans une fenêtre indépendante jaune. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], **Info express** est disponible dans les éditeurs de requête XML et du moteur de base de données.  
  
## <a name="transact-sql-quick-info"></a>Info express (Transact-SQL)  
 **Info express** affiche deux types d’informations dans l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Quand l’option **Info express** n’est pas en mode débogage, elle affiche la déclaration de l’expression. En revanche, en mode débogage, **Info express** affiche le nom de l’expression et sa valeur actuelle.  
  
 Dans l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] , **Info express** n’est disponible que pour les parties de la syntaxe [!INCLUDE[tsql](../../includes/tsql-md.md)] prises en charge par IntelliSense. Par exemple, si vous déplacez le pointeur de la souris sur l’identificateur d’un objet dont le type de données n’est pas pris en charge par IntelliSense, la fenêtre indépendante **Info express** contient un message indiquant que le type de données n’est pas pris en charge.  
  
## <a name="see-also"></a> Voir aussi  
 [Syntaxe Transact-SQL prise en charge par IntelliSense](../../relational-databases/scripting/transact-sql-syntax-supported-by-intellisense.md)  
  
  
