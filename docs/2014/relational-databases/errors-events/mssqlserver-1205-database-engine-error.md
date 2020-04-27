---
title: MSSQLSERVER_1205 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1205 (Database Engine error)
ms.assetid: 9fe3f67c-df3c-4642-a3a4-ccc0e138b632
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ef8a59c98bc6669a13b5a4ffeb516b4063db23c7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62915893"
---
# <a name="mssqlserver_1205"></a>MSSQLSERVER_1205
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|1205|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LK_VICTIM|  
|Texte du message|La transaction (ID de processus %d) a été bloquée sur les ressources %.*ls par un autre processus et a été choisie comme victime. Relancez la transaction.|  
  
## <a name="explanation"></a>Explication  
 Des ressources sont accessibles dans un ordre conflictuel sur des transactions distinctes, ce qui provoque un blocage. Par exemple :  
  
-   Transaction1 met à jour **Table1.Row1**, tandis que Transaction2 met à jour **Table2.Row2**.  
  
-   Transaction1 essaie de mettre à jour **Table2.Row2** mais est bloquée car Transaction2 n’est pas encore validée.  
  
-   Transaction2 essaie alors de mettre à jour **Table1.Row1** mais est bloquée car Transaction1 n’est pas encore validée.  
  
-   Un blocage survient car Transaction1 attend que Transaction2 se termine, alors que Transaction2 attend que Transaction1 se termine.  
  
 Dans ce cas, le système détecte le blocage et choisit une des transactions impliquées en tant que « victime », pour émettre ce message tout en annulant la transaction de la victime.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Exécutez de nouveau la transaction. Vous pouvez également réviser l'application pour éviter les blocages. La transaction qui a été choisie comme victime peut être retentée et réussira probablement, en fonction des opérations qui sont exécutées simultanément.  
  
 Pour empêcher ou éviter l’apparition de blocages, faites en sorte que toutes les transactions accèdent aux lignes dans le même ordre (**Table1**, puis **Table2**) ; de cette manière, bien qu’un blocage puisse survenir, aucun interblocage ne se produira.  
  
  
