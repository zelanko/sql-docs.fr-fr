---
title: MSSQLSERVER_7915 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 7915 (Database Engine error)
ms.assetid: 63338587-7dd3-40e6-b70e-d8ae18fff47b
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f2b74890fc0a878ae21e14e08b9586ac32f6389a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051286"
---
# <a name="mssqlserver7915"></a>MSSQLSERVER_7915
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|7915|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC2_REPAIR_IAM_CHAIN_REBUILT|  
|Texte du message|Réparation : la chaîne IAM pour l'ID d'objet O_ID, ID d'index I_ID, ID de partition PN_ID, ID d'unité d'allocation A_ID (type TYPE), a été tronquée avant la page P_ID et sera reconstruite.|  
  
## <a name="explanation"></a>Explication  
 Ceci est un message d'information envoyé par REPAIR, qui indique que la chaîne IAM (Index Allocation Map) spécifiée a été corrigée afin de pouvoir être reconstruite. Cette correction peut avoir requis l'allocation d'une nouvelle tête de la chaîne IAM ou la suppression de pages incorrectes de la chaîne.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 None  
  
  