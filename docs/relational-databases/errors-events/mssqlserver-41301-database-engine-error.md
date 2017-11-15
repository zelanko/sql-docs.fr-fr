---
title: MSSQLSERVER_41301 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 41301 (Database Engine error)
ms.assetid: c6127e1e-2846-4ee9-bc42-2d896ea9730e
caps.latest.revision: "10"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 7a44ac20040a2a3d6c5c772cf1dfa0008734e06a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver41301"></a>MSSQLSERVER_41301
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|41301|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|COMMIT_DEPENDENCY_FAILURE|  
|Texte du message|Une transaction précédente à la transaction actuelle a pris une dépendance ou a été abandonnée, et la transaction en cours ne peut plus être validée.|  
  
## <a name="explanation"></a>Explication  
La transaction a rencontré une erreur de dépendance, et est maintenant vouée à l'échec.  
  
Cette erreur peut également être causée par un nombre de transactions dépendantes trop important. Les transactions d'écriture ne peuvent avoir qu'un nombre limité de transactions dépendantes. Par exemple, cette erreur peut se produire si trop de transactions de lecture essaient de prendre une dépendance sur la transaction de mise à jour.  
  
## <a name="user-action"></a>Action de l'utilisateur  
N'effectuez aucune tâche dans la transaction. Appelez ROLLBACK TRAN pour restaurer la transaction. Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Voir aussi  
[Activer et désactiver les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](~/database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
