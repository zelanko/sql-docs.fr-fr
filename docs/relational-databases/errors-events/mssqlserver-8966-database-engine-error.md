---
title: MSSQLSERVER_8966 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8966 (Database Engine error)
ms.assetid: 6b1150fd-9dfd-4df9-8f08-8eca237667db
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d5510ea39e741e8226c976bae517e24eac99dcb7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47632337"
---
# <a name="mssqlserver8966"></a>MSSQLSERVER_8966
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
