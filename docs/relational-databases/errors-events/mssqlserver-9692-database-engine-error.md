---
title: MSSQLSERVER_9692 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9692 (Database Engine error)
ms.assetid: 02399d6e-ab5e-4f30-8a3e-2bb1e8c135b5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b5348d31c1b85d3f83797bef186362d62e36efb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85636177"
---
# <a name="mssqlserver_9692"></a>MSSQLSERVER_9692
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|9692|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SB2_CANT_LISTEN_PORT_IN_USE|  
|Texte du message|Le transport de protocole %S_MSG ne peut pas écouter le port %d, car il est utilisé par un autre processus.|  
  
## <a name="explanation"></a>Explication  
Un autre programme exécuté sur l'ordinateur utilise actuellement le port TCP indiqué.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Exécutez **netstat -aon** pour identifier le programme qui utilise le port. Désactivez cette application ou spécifiez un port différent pour Service Broker.  
  
