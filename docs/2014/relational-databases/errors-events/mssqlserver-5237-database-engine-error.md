---
title: MSSQLSERVER_5237 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5237 (Database Engine error)
ms.assetid: 9ff28935-d1eb-47ee-99b3-1a65cb948ce7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: eabe36c423b1df3702b594137aca371a6075e327
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48208729"
---
# <a name="mssqlserver5237"></a>MSSQLSERVER_5237
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|5237|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE|  
|Texte du message|Échec de la vérification entre ensembles de lignes DBCC pour l'objet 'NAME' (ID d'objet O_ID) en raison d'une erreur de requête interne.|  
  
## <a name="explanation"></a>Explication  
 Suite à une erreur interne, DBCC n'est pas en mesure d'exécuter la requête pour vérifier des vues indexées.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Exécutez de nouveau la commande DBCC.  
  
  
