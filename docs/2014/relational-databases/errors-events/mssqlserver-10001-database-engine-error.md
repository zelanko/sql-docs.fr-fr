---
title: MSSQLSERVER_10001 | Microsoft Docs
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
- 10001 (Database Engine error)
ms.assetid: f8fd2d8d-a4af-4b6a-ba51-9123b7e4c9bf
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 08bbafd03c8db19e605dca8e985d351cfc4dbf0b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141599"
---
# <a name="mssqlserver10001"></a>MSSQLSERVER_10001
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10001|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|HR_E_UNEXPECTED|  
|Texte du message|Le fournisseur rapporte une défaillance catastrophique inattendue.|  
  
## <a name="explanation"></a>Explication  
 Le traitement de la requête distribuée a rencontré une erreur générique lors de l'appel du fournisseur OLE DB.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Collectez les événements de trace OLE DB à l’aide de [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] et fournissez ces données au support technique du fournisseur OLE DB.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles et autorisations du générateur de SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  