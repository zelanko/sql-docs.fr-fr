---
title: MSSQLSERVER_17132 | Microsoft Docs
description: L'ordinateur SQL Server n'a pas pu traiter le paquet d’ouverture de session du client. Consultez une explication de l’erreur et les solutions possibles.
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17132 (Database Engine error)
ms.assetid: d1d198bd-6730-4394-bd5f-28f320c01a38
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4767ba217eab0d8cdbc6a9dc80f751868322f21f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780842"
---
# <a name="mssqlserver_17132"></a>MSSQLSERVER_17132
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|17132|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|INIT_NODESSPACE|  
|Texte du message|Échec du démarrage du serveur en raison d'une quantité de mémoire insuffisante pour le descripteur. Réduisez les utilisations non vitales de la mémoire ou augmentez la mémoire système.|  
  
## <a name="explanation"></a>Explication  
Échec de l'allocation d'une quantité de mémoire suffisante pour stocker le descripteur interne du serveur.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Ajoutez plus de mémoire à l'ordinateur. Les étapes de résolution des problèmes de mémoire génériques peuvent être utiles.  
  
