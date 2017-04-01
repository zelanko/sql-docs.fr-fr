---
title: "Configurer des alertes afin d&#39;informer les administrateurs de strat&#233;gie en cas d&#39;&#233;chec de strat&#233;gie | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "gestion basée sur des stratégies, configuration d’alertes"
ms.assetid: e8e60159-d5b0-49d5-91f3-af8e9cb994c1
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# Configurer des alertes afin d&#39;informer les administrateurs de strat&#233;gie en cas d&#39;&#233;chec de strat&#233;gie
  Lorsque des stratégies de Gestion basée sur des stratégies sont exécutées dans l'un des trois modes d'évaluation automatisés, en cas de violation de stratégie, un message est écrit dans le journal des événements. Pour être informé de l'écriture de ce message dans le journal des événements, vous pouvez créer une alerte afin de détecter le message et d'exécuter une action. L'alerte doit détecter les messages comme indiqué dans le tableau suivant.  
  
|Mode d'exécution|Numéro de message|  
|--------------------|--------------------|  
|Sur modification - Empêcher<br /><br /> (si automatique)|34050|  
|Sur modification - Empêcher<br /><br /> (si À la demande)|34051|  
|Selon planification|34052|  
|Sur modification|34053|  
  
 Pour configurer une alerte en réponse aux messages d'erreur de la Gestion basée sur des stratégies, consultez les rubriques suivantes :  
  
-   [Créer un opérateur](../../ssms/agent/create-an-operator.md)  
  
-   [Créer une alerte utilisant un numéro d'erreur](../../ssms/agent/create-an-alert-using-an-error-number.md)  
  
-   [Affecter des alertes à un opérateur](../../ssms/agent/assign-alerts-to-an-operator.md)  
  
## Autorisations  
 Lorsque des stratégies sont évaluées à la demande, elles s'exécutent dans le contexte de sécurité de l'utilisateur. Pour écrire dans le journal des erreurs, l'utilisateur doit posséder l'autorisation ALTER TRACE ou être membre du rôle serveur fixe sysadmin. Les stratégies évaluées par un utilisateur qui dispose de moins de privilèges n'écrivent pas dans le journal des événements et ne déclenchent pas d'alerte.  
  
 Les modes d'exécution automatisés s'exécutent comme membre du rôle sysadmin. Cela permet à la stratégie d'écrire dans le journal des erreurs et de déclencher une alerte.  
  
## Considérations supplémentaires relatives aux alertes  
 Tenez compte des considérations supplémentaires relatives aux alertes :  
  
-   Des alertes sont déclenchées uniquement pour les stratégies activées. Comme les stratégies **À la demande** ne peuvent pas être activées, aucune alerte n’est déclenchée pour les stratégies exécutées sur demande.  
  
-   Si l'action que vous souhaitez effectuer inclut l'envoi d'un message électronique, vous devez configurer un compte de messagerie. Nous vous recommandons d'utiliser la Messagerie de base de données. Pour plus d’informations sur la manière de configurer la messagerie de base de données, consultez [Créer un compte de messagerie de base de données](../../relational-databases/database-mail/create-a-database-mail-account.md).  
  
  