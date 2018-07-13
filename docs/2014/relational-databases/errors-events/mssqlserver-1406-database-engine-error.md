---
title: MSSQLSERVER_1406 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 1406 (Database Engine error)
ms.assetid: 915f97de-9b74-41f8-8bd5-b2d061416718
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 84f9ff97dc89092f06a960f86f0a6844a2b30a52
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37424828"
---
# <a name="mssqlserver1406"></a>MSSQLSERVER_1406
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|1406|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBM_BADSTATEFORFORCESERVICE|  
|Texte du message|Impossible de forcer le service en toute sécurité. Supprimez la mise en miroir de bases de données et récupérez la base de données "%.*ls" pour y accéder.|  
  
## <a name="explanation"></a>Explication  
 Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ne peut pas forcer le service car l'état de la mise en miroir ne peut pas garantir le bon fonctionnement du processus impliqué pour forcer le service.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Supprimez la mise en miroir de bases de données. Vous pouvez ensuite récupérer la base de données miroir pour y accéder.  
  
## <a name="see-also"></a>Voir aussi  
 [Forcer le service dans une session de mise en miroir de bases de données &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md)   
 [Suppression d’une mise en miroir des bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
