---
title: Journal des erreurs de SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- messages [SQL Server], SQL Server Agent
- errors [SQL Server], logs
- SQL Server Agent, errors
ms.assetid: 0b2d6e6e-cd2d-4b8b-9fa2-2bbd2fc0da41
author: stevestein
ms.author: sstein
ms.openlocfilehash: 29bc8faa8fbd897a9bbb3a51c1042d48e84ff977
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058769"
---
# <a name="sql-server-agent-error-log"></a>Journal des erreurs de SQL Server Agent
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent crée un journal des erreurs qui, par défaut, enregistre les avertissements et les erreurs. Le journal contient :  
  
-   Messages d’avertissement qui fournissent des informations sur les problèmes potentiels, tels que « la tâche \<*job_name*> a été supprimée pendant son exécution ».  
  
-   Des messages d'erreur dont la solution nécessite habituellement l'intervention d'un administrateur système, tels que « Impossible de démarrer la session de messagerie ». Les messages d’erreur peuvent être envoyés à un utilisateur ou un ordinateur spécifique via **net send**.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve jusqu’à neuf journaux des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Chaque journal des erreurs archivé possède un suffixe indiquant son ancienneté relative. Par exemple, le suffixe .1 signale le journal des erreurs le plus récemment archivé alors que le suffixe .9 indique qu'il s'agit du plus ancien journal des erreurs existant.  
  
 Par défaut, les messages de trace d'exécution ne sont pas écrits dans le journal d'erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, parce qu'ils risquent de le remplir. Lorsque le fichier d'erreurs est plein, votre possibilité de sélectionner et analyser les erreurs plus difficiles se trouve réduite. Le journal étant une charge supplémentaire de travail pour le serveur, il est important de bien réfléchir à ce que la capture de messages de trace d’exécution dans le journal des erreurs vous apporte. Il est en général préférable de capturer tous les messages uniquement au moment de corriger un problème donné.  
  
 Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent n'est pas activé, vous pouvez modifier l'emplacement du journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Lorsque le journal est vide, il ne peut pas être ouvert. Vous pouvez parcourir le journal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent à n'importe quel moment sans devoir interrompre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 **Pour afficher le journal des erreurs SQL Server Agent**  
  
-   [Afficher le journal des erreurs SQL Server Agent &#40;SQL Server Management Studio&#41;](view-sql-server-agent-error-log-sql-server-management-studio.md) 
  
 **Pour renommer le journal des erreurs SQL Server Agent**  
  
-   [Renommer un journal d’erreurs SQL Server Agent &#40;SQL Server Management Studio&#41;](rename-a-sql-server-agent-error-log-sql-server-management-studio.md)  
  
 **Pour envoyer des messages d'erreur de SQL Server Agent**  
  
-   [Send SQL Server Agent Error Messages](send-sql-server-agent-error-messages.md)  
  
 **Pour écrire des messages de trace d'exécution dans le journal des erreurs SQL Server Agent**  
  
-   [Écrire des messages de trace d’exécution dans le journal des erreurs SQL Server Agent &#40;SQL Server Management Studio&#41;](write-execution-trace-messages-to-sql-server-agent-log-ssms.md)  
  
  
