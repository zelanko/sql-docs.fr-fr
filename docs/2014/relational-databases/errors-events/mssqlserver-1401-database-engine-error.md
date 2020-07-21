---
title: MSSQLSERVER_1401 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1401 (Database Engine error)
ms.assetid: 02928770-aa63-4509-8713-406c73e4cedc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fde7bbf3e3db95f75606a7b735eef41b7b6abf2b
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552304"
---
# <a name="mssqlserver_1401"></a>MSSQLSERVER_1401
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|1401|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBM_MASTERSTARTUP|  
|Texte du message|Le démarrage de la routine du thread principal pour le processus de mise en miroir de la base de données a échoué pour la raison suivante : %ls. Corrigez la cause de cette erreur et redémarrez le service SQL Server.|  
  
## <a name="explanation"></a>Explication  
 Le démarrage du thread de contrôle de la mise en miroir a échoué.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], recherchez l'erreur associée qui a précédé ce message. Corrigez la cause de cette erreur, puis redémarrez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER).  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer, arrêter, suspendre, reprendre, redémarrer le moteur de base de données, SQL Server Agent ou le service SQL Server Browser](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
