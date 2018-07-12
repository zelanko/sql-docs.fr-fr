---
title: MSSQLSERVER_1401 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 1401 (Database Engine error)
ms.assetid: 02928770-aa63-4509-8713-406c73e4cedc
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 41472f979c926f9009070be63112494fa6352be4
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37429678"
---
# <a name="mssqlserver1401"></a>MSSQLSERVER_1401
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|1401|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBM_MASTERSTARTUP|  
|Texte du message|Le démarrage de la routine du thread principal pour le processus de mise en miroir de la base de données a échoué pour la raison suivante : %ls. Corrigez la cause de cette erreur et redémarrez le service SQL Server.|  
  
## <a name="explanation"></a>Explication  
 Le démarrage du thread de contrôle de la mise en miroir a échoué.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], recherchez l'erreur associée qui a précédé ce message. Corrigez la cause de cette erreur, puis redémarrez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER).  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer, arrêter, suspendre, reprendre, redémarrer le moteur de base de données, SQL Server Agent ou le service SQL Server Browser](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
