---
title: MSSQLSERVER_8525 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
f1_keywords:
- "8525"
helpviewer_keywords:
- 8525 (Database Engine error)
ms.assetid: 297867c1-691e-4d6b-a3be-a7575015ecfa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 605bb1ae8ff8cd3fb3e5c0e7a096de7aa646730c
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68101500"
---
# <a name="mssqlserver_8525"></a>MSSQLSERVER_8525
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|8525|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique||  
|Texte du message|La transaction distribuée est terminée. Inscrivez cette session, soit dans une nouvelle transaction, soit dans une transaction NULL.|  
  
## <a name="explanation"></a>Explication  
Le modèle de programmation permettant d’utiliser Distributed Transaction Coordinator avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requiert des applications à inscrire explicitement dans une transaction distribuée et à désinscrire explicitement d’une transaction distribuée.  
  
Cette erreur se produit lorsque les quatre conditions suivantes sont réunies :  
  
-   L'application est inscrite dans une transaction distribuée.  
  
-   La transaction est terminée, validée ou restaurée, pour une raison quelconque.  
  
-   L'application utilisateur n'est pas explicitement désinscrite d'une transaction distribuée ni explicitement inscrite dans une nouvelle transaction distribuée.  
  
-   L'application tente d'effectuer une opération transactionnelle qui n'est ni la désinscription d'une transaction distribuée existante ni l'inscription dans une nouvelle transaction distribuée. Il peut s'agir par exemple de l'émission d'une requête ou du démarrage d'une transaction locale.  
  
L'état d'erreur 1 est utilisé lorsque l'application effectue une opération qui permet de créer des transactions locales et l'état 2 est utilisé lorsque l'application tente une inscription dans une session associée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Une fois qu'une application est inscrite dans une transaction distribuée, l'application doit être explicitement désinscrite de la transaction distribuée ou inscrite dans une autre transaction distribuée. Cela entraînera la désinscription implicite d'une transaction inscrite antérieure. Pour obtenir la syntaxe exacte relative à la désinscription ou à l'inscription dans une transaction distribuée, consultez le manuel de l'interface de programmation de l'application.  
  
