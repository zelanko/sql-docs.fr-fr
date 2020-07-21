---
title: MSSQLSERVER_1458 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1458 (Database Engine error)
ms.assetid: adc78c59-a6f2-432b-9a07-fdd1dc2b9026
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fd4f3499dcf24435c594d3f01adce97f979f817d
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553854"
---
# <a name="mssqlserver_1458"></a>MSSQLSERVER_1458
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|1458|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBM_FAILREDO_ON_PRIMARY|  
|Texte du message|La copie principale de la base de données '%.*ls' a rencontré l'erreur %d, état %d, gravité %d. La mise en miroir de bases de données a été interrompue. Essayez de résoudre l'erreur et reprenez la mise en miroir.|  
  
## <a name="explanation"></a>Explication  
 Ce message indique que la base de données principale a rencontré une erreur qui a provoqué la suspension de la mise en miroir de bases de données.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Dans la plupart des cas, cette erreur se corrige toute seule. Si le problème persiste, le redémarrage de la base de données ou de l'instance du serveur corrige généralement le problème. Pour plus d'informations, consultez le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur chaque serveur partenaire pour rechercher l'erreur associée qui a précédé ce message.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance de la mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
