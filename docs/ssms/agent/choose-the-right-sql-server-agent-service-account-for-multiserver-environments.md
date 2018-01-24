---
title: Choisir le compte Agent pour les environnements multiserveurs | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, service accounts
- multiserver environments [SQL Server], SQL Server Agent service account behavior
ms.assetid: a07e2f38-281c-495b-965b-13fad03ba548
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3d9ccc867f1b4e54ef3d304277a5b0ad6725765c
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="choose-the-right-sql-server-agent-service-account-for-multiserver-environments"></a>Choisir le compte de service SQL Server Agent correct pour les environnements multiserveurs
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Le compte Windows que vous choisissez pour le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent peut affecter le comportement d’un environnement multiserveur de la manière suivante :  
  
-   Si vous exécutez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent avec un compte n'appartenant pas au groupe Administrateurs local de Windows, l'inscription des serveurs cibles en serveurs maîtres risque d'échouer. Si tel est le cas, le message d'erreur suivant apparaît :  
  
    « Échec de l'inscription ».  
  
    Redémarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] et les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent pour résoudre ce problème.  
  
-   Lorsque vous exécutez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent avec le compte système local, les opérations de serveur maître/serveur cible sont prises en charge uniquement si les serveurs maître et cible résident sur le même ordinateur. Si vous optez pour cette configuration, le message suivant apparaît lorsque vous inscrivez des serveurs cibles sur un serveur maître :  
  
    « Vérifiez que le compte de démarrage de l'agent pour *<nom_ordinateur_serveur_cible>* dispose des autorisations pour se connecter en tant que serveur cible. »  
  
    Vous pouvez ignorer ce message d'information. L'opération d'enregistrement doit se terminer correctement.  
  
Pour plus d’informations sur le choix d’un compte pour le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, consultez [Sélectionner un compte pour le service SQL Server Agent](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md).  
  
