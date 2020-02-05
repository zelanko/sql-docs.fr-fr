---
title: MSSQLSERVER_1458 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1458 (Database Engine error)
ms.assetid: adc78c59-a6f2-432b-9a07-fdd1dc2b9026
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 546d3e40d8b925d88344f6074d577b1b14c31092
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68033429"
---
# <a name="mssqlserver_1458"></a>MSSQLSERVER_1458
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
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
[Surveillance de la mise en miroir de bases de données &#40;SQL Server&#41;](~/database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)  
  
