---
title: MSSQLSERVER_17887 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17887 (Database Engine error)
ms.assetid: ad0806e6-3296-4c32-b103-fccf0f8a8d3d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: caf58e486706913fbaa8016e142f6aefc8bded3b
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68137212"
---
# <a name="mssqlserver_17887"></a>MSSQLSERVER_17887
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|17887|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SRV_IO_COMP_LISTENER_NONYIELDING|  
|Texte du message|L’écoute d’achèvement d’E/S (0x%lx) travail 0x%p semble être improductive sur le nœud %ld. Utilisation approximative de l'UC : noyau %I64d ms, utilisateur %I64d ms, intervalle : %I64d.|  
  
## <a name="explanation"></a>Explication  
Indique qu'il existe un éventuel problème avec l'écouteur du port d'exécution d'E/S sur le nœud spécifié lors de l'exécution de la routine d'exécution d'E/S pour un événement de lecture/écriture sur le réseau. Cette erreur disparaîtra lorsque l'écouteur du port d'exécution d'E/S sortira de la routine d'exécution d'E/S.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Contactez les services d'assistance Microsoft.  
  
