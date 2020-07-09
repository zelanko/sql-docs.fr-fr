---
title: MSSQLSERVER_17883 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17883 (Database Engine error)
ms.assetid: adaf1c04-e397-4a69-90b8-9353a37277ea
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 57e69fcab91f7f8b30de32d2187ec1d7a86ce179
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780710"
---
# <a name="mssqlserver_17883"></a>MSSQLSERVER_17883
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|17883|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SRV_SCHEDULER_NONYIELDING|  
|Texte du message|Le processus %ld:%ld:%ld (0x%lx) travail 0x%p semble être improductif dans le Planificateur %ld. Heure de création du thread : %I64d. Utilisation approximative de l'UC pour ce thread : noyau %I64d ms, utilisateur %I64d ms. Utilisation du processus %d%%. Système inactif %d%%. Intervalle : %I64d ms.|  
  
## <a name="explanation"></a>Explication  
Indique un problème possible avec un thread improductif dans un Planificateur.  Il peut s'agir d'un bogue dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou si le nombre de cycles à exécuter par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est insuffisant.  Cette erreur peut se résoudre si le thread finit par être productif.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Si la charge excessive sur le système réduit la charge en général, contactez le service de support technique Microsoft.  
  
