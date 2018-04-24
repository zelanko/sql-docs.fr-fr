---
title: MSSQLSERVER_17130 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c3395687ca0808cacd2e7b8e975e9503d49fde72
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver17130"></a>MSSQLSERVER_17130
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|17130|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|INIT_NOLOCKSPACE|  
|Texte du message|Mémoire insuffisante pour le nombre de verrous configuré. Tentative de démarrage avec une table de hachage de verrou moins importante en cours, ce qui risque d'influer sur les performances. Contactez l'administrateur de base de données pour configurer une quantité de mémoire plus importante pour cette instance du moteur de base de données.|  
  
## <a name="explanation"></a>Explication  
Mémoire insuffisante pour la taille souhaitée de la table de hachage du gestionnaire de verrous.  Une tentative d'allocation d'une table de hachage plus petite va être effectuée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Vérifiez les paramètres de configuration de la mémoire du serveur (min server memory et max server memory), ainsi que la sollicitation de la mémoire : Allouez davantage de mémoire à SQL Server.  
  
