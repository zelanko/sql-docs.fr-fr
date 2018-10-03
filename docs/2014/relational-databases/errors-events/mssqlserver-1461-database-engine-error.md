---
title: MSSQLSERVER_1461 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1461 (Database Engine error)
ms.assetid: fce10907-4753-441b-b624-f28e00ed7520
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0af23b53c60ffeafcbaa99a7a499fe0a71cd551b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48121629"
---
# <a name="mssqlserver1461"></a>MSSQLSERVER_1461
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|1461|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBM_SAFETY_MISMATCH|  
|Texte du message|Plusieurs niveaux de sécurité de mise en miroir de bases de données ont été détectés pour la base de données « %.*ls ». Le niveau de sécurité FULL sera utilisé.|  
  
## <a name="explanation"></a>Explication  
 Les connexions de mise en miroir ont été interrompues lorsque le niveau de sécurité des transactions a été modifié car les paramètres de sécurité des transactions étaient incohérents entre la base de données principale et la base de données miroir. Le paramètre de sécurité par défaut, à savoir la sécurité totale des transactions, sera utilisé. La session sera exécutée en mode haute sécurité.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour désactiver la sécurité des transactions, réexécutez l’instruction ALTER DATABASE *nom_base_de_données* SET PARTNER SAFETY OFF sur la base de données principale.  
  
  
