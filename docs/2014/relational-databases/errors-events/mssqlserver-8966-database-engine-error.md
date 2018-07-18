---
title: MSSQLSERVER_8966 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 8966 (Database Engine error)
ms.assetid: 6b1150fd-9dfd-4df9-8f08-8eca237667db
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8bf378f38acb4efd25d4cd62ccab0613dfc9f94d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37418168"
---
# <a name="mssqlserver8966"></a>MSSQLSERVER_8966
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|8966|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC3_FAILED_TO_READ_AND_LATCH_PAGE|  
|Texte du message|Impossible de lire et de verrouiller la page P_ID avec le type de verrou TYPE. Échec de OPERATION.|  
  
## <a name="explanation"></a>Explication  
 La lecture de la page a échoué ou un verrou n'a pas pu être pris en compte sur une page PFS ou GAM. Le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut contenir des messages relatifs au dépassement de délai d’attente de verrous ou d’autres messages associés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez les éventuels messages associés dans le journal des erreurs SQL et résolvez ces erreurs.  
  
  
