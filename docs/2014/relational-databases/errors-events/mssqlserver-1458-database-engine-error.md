---
title: MSSQLSERVER_1458 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 1458 (Database Engine error)
ms.assetid: adc78c59-a6f2-432b-9a07-fdd1dc2b9026
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 28d03db450e4a3f0c06e5b8e3474efd2e3173c70
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414458"
---
# <a name="mssqlserver1458"></a>MSSQLSERVER_1458
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|1458|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBM_FAILREDO_ON_PRIMARY|  
|Texte du message|La copie principale de la base de données '%.*ls' a rencontré l'erreur %d, état %d, gravité %d. La mise en miroir de bases de données a été interrompue. Essayez de résoudre l'erreur et reprenez la mise en miroir.|  
  
## <a name="explanation"></a>Explication  
 Ce message indique que la base de données principale a rencontré une erreur qui a provoqué la suspension de la mise en miroir de bases de données.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Dans la plupart des cas, cette erreur se corrige toute seule. Si le problème persiste, le redémarrage de la base de données ou de l'instance du serveur corrige généralement le problème. Pour plus d'informations, consultez le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur chaque serveur partenaire pour rechercher l'erreur associée qui a précédé ce message.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance de la mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
