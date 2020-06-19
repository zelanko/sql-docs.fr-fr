---
title: Notifier l’opérateur, tâche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.notifyoperatortask.f1
helpviewer_keywords:
- Notify Operator task
- notifications [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 6c816c68-c6d6-44e4-bb34-c8e060a958a1
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 9ee8ee285d395425e925f2d5ec1e8a169d4ac5fa
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84918409"
---
# <a name="notify-operator-task"></a>tâche de notification d'opérateur
  La tâche Notifier l'opérateur envoie des messages de notification aux opérateurs d'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Un opérateur d'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est un alias d'une personne ou d'un groupe qui peut recevoir des notifications électroniques. Pour plus d'informations sur les opérateurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez [Opérateurs](../../ssms/agent//operators.md).  
  
 La tâche Notifier l’opérateur permet à un package de notifier un ou plusieurs opérateurs par e-mail, radiomessagerie ou **envoi réseau**. Chaque opérateur peut être notifié par différentes méthodes. Par exemple, l’opérateur A est notifié par e-mail et radiomessagerie, tandis que l’opérateur B est notifié par radiomessagerie et **envoi réseau**. Les opérateurs qui reçoivent des notifications depuis la tâche de notification d'opérateur doivent être membres de sa collection **OperatorNotify** .  
  
 La tâche Notifier l'opérateur est la seule tâche de maintenance de base de données qui n'encapsule pas d'instruction Transact-SQL ou de commande DBCC.  
  
## <a name="configuration-of-the-notify-operator-task"></a>Configuration de la tâche Notifier l'opérateur  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Cette tâche se trouve dans la section **Tâches du plan de maintenance** de la **boîte à outils** du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Tâche Notifier l’opérateur &#40;Plan de maintenance&#41;](../../relational-databases/maintenance-plans/notify-operator-task-maintenance-plan.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
  
