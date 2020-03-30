---
title: MSSQLSERVER_9790 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 67aa62efb3f77c82aec4b1f5d654532cfadd74fb
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67903821"
---
# <a name="mssqlserver_9790"></a>MSSQLSERVER_9790
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|9790|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER|  
|Texte du message|Impossible d'acheminer le message entrant. La base de données MSDB système contenant les informations d'acheminement est en mode SINGLE USER.|  
  
## <a name="explanation"></a>Explication  
Une erreur s'est produite lors de la tentative de classement d'un message reçu sur le réseau : la base de données MSDB était en mode SINGLE USER.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Passez MSDB en mode MULTI USER à l'aide de la commande ALTER DATABASE.  
  
