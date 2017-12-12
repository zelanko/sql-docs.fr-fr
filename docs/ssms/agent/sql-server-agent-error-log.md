---
title: Journal des erreurs de SQL Server Agent | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- messages [SQL Server], SQL Server Agent
- errors [SQL Server], logs
- SQL Server Agent, errors
ms.assetid: 0b2d6e6e-cd2d-4b8b-9fa2-2bbd2fc0da41
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 65ae66be5c0d6f68cc977ca7046cb0b56fe3db00
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="sql-server-agent-error-log"></a>Journal des erreurs de SQL Server Agent
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent crée un journal des erreurs qui, par défaut, enregistre les avertissements et les erreurs. Le journal contient :  
  
-   Des messages d’avertissement qui fournissent des informations sur des problèmes potentiels, tels que « Le travail \<*nom_travail*> a été supprimé en cours d’exécution ».  
  
-   Des messages d'erreur dont la solution nécessite habituellement l'intervention d'un administrateur système, tels que « Impossible de démarrer la session de messagerie ». Les messages d’erreur peuvent être envoyés à un utilisateur ou un ordinateur spécifique via **net send**.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] conserve jusqu’à neuf journaux des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Chaque journal des erreurs archivé possède un suffixe indiquant son ancienneté relative. Par exemple, le suffixe .1 signale le journal des erreurs le plus récemment archivé alors que le suffixe .9 indique qu'il s'agit du plus ancien journal des erreurs existant.  
  
Par défaut, les messages de trace d'exécution ne sont pas écrits dans le journal d'erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, parce qu'ils risquent de le remplir. Lorsque le fichier d'erreurs est plein, votre possibilité de sélectionner et analyser les erreurs plus difficiles se trouve réduite. Le journal étant une charge supplémentaire de travail pour le serveur, il est important de bien réfléchir à ce que la capture de messages de trace d’exécution dans le journal des erreurs vous apporte. Il est en général préférable de capturer tous les messages uniquement au moment de corriger un problème donné.  
  
Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent n'est pas activé, vous pouvez modifier l'emplacement du journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Lorsque le journal est vide, il ne peut pas être ouvert. Vous pouvez parcourir le journal [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent à n'importe quel moment sans devoir interrompre [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
**Pour afficher le journal des erreurs SQL Server Agent**  
  
-   [Afficher le journal des erreurs SQL Server Agent &#40;SQL Server Management Studio&#41;](../../ssms/agent/view-sql-server-agent-error-log-sql-server-management-studio.md)  
  
**Pour renommer le journal des erreurs SQL Server Agent**  
  
-   [Renommer un journal d’erreurs SQL Server Agent &#40;SQL Server Management Studio&#41;](../../ssms/agent/rename-a-sql-server-agent-error-log-sql-server-management-studio.md)  
  
**Pour envoyer des messages d'erreur SQL Server Agent**  
  
-   [Envoyer des messages d'erreur SQL Server Agent](../../ssms/agent/send-sql-server-agent-error-messages.md)  
  
**Pour écrire des messages de trace d'exécution dans le journal des erreurs SQL Server Agent**  
  
-   [Écrire des messages de trace d’exécution dans le journal des erreurs SQL Server Agent &#40;SQL Server Management Studio&#41;](../../ssms/agent/write-execution-trace-messages-to-sql-server-agent-log-ssms.md)  
  
