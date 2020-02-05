---
title: MSSQLSERVER_3437 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3437 (Database Engine error)
ms.assetid: b38216e2-b650-43bd-97af-061d54f60031
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c0e4b8a9e7e8dacb2369af4c9f43000ba1a9702
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68132313"
---
# <a name="mssqlserver_3437"></a>MSSQLSERVER_3437
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|3437|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|NODTC|  
|Texte du message|Une erreur s'est produite lors de la récupération de la base de données '%.*ls'. Impossible de se connecter à MS DTC pour vérifier l'état d'avancement de la transaction %S_XID. Corrigez MS DTC et réexécutez la récupération.|  
  
## <a name="explanation"></a>Explication  
Une ou plusieurs transactions distribuées utilisant MS DTC ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator) étaient incomplètes lorsque la base de données a été fermée. La récupération de cette base de données a échoué car [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas se connecter à MS DTC pour terminer ou restaurer les transactions.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Pour récupérer cette base de données, vous devez d'abord résoudre le problème avec MS DTC. Pour analyser ce problème, examinez les journaux des événements Windows. Si vous ne parvenez pas à résoudre le problème avec MS DTC et à récupérer la base de données, restaurez une sauvegarde de la base de données.  
  
