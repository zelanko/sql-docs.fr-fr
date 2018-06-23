---
title: Journal des erreurs de SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- messages [SQL Server], SQL Server Agent
- errors [SQL Server], logs
- SQL Server Agent, errors
ms.assetid: 0b2d6e6e-cd2d-4b8b-9fa2-2bbd2fc0da41
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d5622321e1b947b6f5fb6c31463d9ea7e71d395b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154312"
---
# <a name="sql-server-agent-error-log"></a>Journal des erreurs de SQL Server Agent
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent crée un journal des erreurs qui, par défaut, enregistre les avertissements et les erreurs. Le journal contient :  
  
-   Des messages d’avertissement qui fournissent des informations sur des problèmes potentiels, tels que « Le travail \<*nom_travail*> a été supprimé en cours d’exécution ».  
  
-   Des messages d'erreur dont la solution nécessite habituellement l'intervention d'un administrateur système, tels que « Impossible de démarrer la session de messagerie ». Les messages d’erreur peuvent être envoyés à un utilisateur ou un ordinateur spécifique via **net send**.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve jusqu’à neuf journaux des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Chaque journal des erreurs archivé possède un suffixe indiquant son ancienneté relative. Par exemple, le suffixe .1 signale le journal des erreurs le plus récemment archivé alors que le suffixe .9 indique qu'il s'agit du plus ancien journal des erreurs existant.  
  
 Par défaut, les messages de trace d'exécution ne sont pas écrits dans le journal d'erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, parce qu'ils risquent de le remplir. Lorsque le fichier d'erreurs est plein, votre possibilité de sélectionner et analyser les erreurs plus difficiles se trouve réduite. Le journal étant une charge supplémentaire de travail pour le serveur, il est important de bien réfléchir à ce que la capture de messages de trace d’exécution dans le journal des erreurs vous apporte. Il est en général préférable de capturer tous les messages uniquement au moment de corriger un problème donné.  
  
 Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent n'est pas activé, vous pouvez modifier l'emplacement du journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Lorsque le journal est vide, il ne peut pas être ouvert. Vous pouvez parcourir le journal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent à n'importe quel moment sans devoir interrompre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 **Pour afficher le journal des erreurs SQL Server Agent**  
  
-   [Afficher le journal des erreurs SQL Server Agent &#40;SQL Server Management Studio&#41;](view-sql-server-agent-error-log-sql-server-management-studio.md) 
  
 **Pour renommer le journal des erreurs SQL Server Agent**  
  
-   [Renommer un journal d’erreurs SQL Server Agent &#40;SQL Server Management Studio&#41;](rename-a-sql-server-agent-error-log-sql-server-management-studio.md)  
  
 **Pour envoyer des messages d'erreur SQL Server Agent**  
  
-   [Envoyer des messages d'erreur SQL Server Agent](send-sql-server-agent-error-messages.md)  
  
 **Pour écrire des messages de trace d'exécution dans le journal des erreurs SQL Server Agent**  
  
-   [Écrire des messages de trace d’exécution dans le journal des erreurs SQL Server Agent &#40;SQL Server Management Studio&#41;](write-execution-trace-messages-to-sql-server-agent-log-ssms.md)  
  
  