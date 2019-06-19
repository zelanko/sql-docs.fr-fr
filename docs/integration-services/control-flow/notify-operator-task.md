---
title: Notifier l’opérateur, tâche | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.notifyoperatortask.f1
helpviewer_keywords:
- Notify Operator task
- notifications [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 6c816c68-c6d6-44e4-bb34-c8e060a958a1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2a90017caa4a5c556924756696b61f2686f57ba3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65727530"
---
# <a name="notify-operator-task"></a>tâche de notification d'opérateur

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  La tâche Notifier l'opérateur envoie des messages de notification aux opérateurs d'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Un opérateur d'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est un alias d'une personne ou d'un groupe qui peut recevoir des notifications électroniques. Pour plus d'informations sur les opérateurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez [Opérateurs](../../ssms/agent/operators.md).  
  
 La tâche Notifier l’opérateur permet à un package de notifier un ou plusieurs opérateurs par e-mail, radiomessagerie ou **envoi réseau**. Chaque opérateur peut être notifié par différentes méthodes. Par exemple, l’opérateur A est notifié par e-mail et radiomessagerie, tandis que l’opérateur B est notifié par radiomessagerie et **envoi réseau**. Les opérateurs qui reçoivent des notifications depuis la tâche de notification d'opérateur doivent être membres de sa collection **OperatorNotify** .  
  
 La tâche Notifier l'opérateur est la seule tâche de maintenance de base de données qui n'encapsule pas d'instruction Transact-SQL ou de commande DBCC.  
  
## <a name="configuration-of-the-notify-operator-task"></a>Configuration de la tâche Notifier l'opérateur  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Cette tâche se trouve dans la section **Tâches du plan de maintenance** de la **boîte à outils** du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Tâche Notifier l’opérateur &#40;Plan de maintenance&#41;](../../relational-databases/maintenance-plans/notify-operator-task-maintenance-plan.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
  
