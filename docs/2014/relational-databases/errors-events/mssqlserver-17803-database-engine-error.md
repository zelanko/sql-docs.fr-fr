---
title: MSSQLSERVER_17803 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17803 (Database Engine error)
ms.assetid: 28591a19-258d-4891-b78a-4686789bb2d7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 683806941947a6da888264e4d0e4e3807200ef13
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869544"
---
# <a name="mssqlserver17803"></a>MSSQLSERVER_17803
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|17803|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SRV_NOMEMORY|  
|Texte du message|Une erreur d'allocation de mémoire s'est produite au cours de l'établissement de la connexion. Réduisez la charge de mémoire qui n'est pas essentielle ou augmentez la quantité de mémoire système. La connexion a été fermée.%.*ls|  
  
## <a name="explanation"></a>Explication  
Le serveur manque de mémoire.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Déterminez la cause de la mémoire insuffisante au niveau du serveur. Les étapes de résolution des problèmes de mémoire génériques peuvent être utiles  
  
