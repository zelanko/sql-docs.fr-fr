---
title: Configurer des alertes afin d’informer les administrateurs de stratégie en cas d’échec de stratégie | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, configure alerts
ms.assetid: e8e60159-d5b0-49d5-91f3-af8e9cb994c1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1009a79aa85394e4fd406744a308f55a9413ed5c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48162325"
---
# <a name="configure-alerts-to-notify-policy-administrators-of-policy-failures"></a>Configurer des alertes afin d'informer les administrateurs de stratégie en cas d'échec de stratégie
  Lorsque des stratégies de Gestion basée sur des stratégies sont exécutées dans l'un des trois modes d'évaluation automatisés, en cas de violation de stratégie, un message est écrit dans le journal des événements. Pour être informé de l'écriture de ce message dans le journal des événements, vous pouvez créer une alerte afin de détecter le message et d'exécuter une action. L'alerte doit détecter les messages comme indiqué dans le tableau suivant.  
  
|Mode d'exécution|Numéro de message|  
|--------------------|--------------------|  
|Sur modification - Empêcher<br /><br /> (si automatique)|34050|  
|Sur modification - Empêcher<br /><br /> (si À la demande)|34051|  
|Selon planification|34052|  
|Sur modification|34053|  
  
 Pour configurer une alerte en réponse aux messages d'erreur de la Gestion basée sur des stratégies, consultez les rubriques suivantes :  
  
-   [Créer un opérateur](../../ssms/agent/create-an-operator.md)  
  
-   [Créer une alerte utilisant un numéro d'erreur](../../ssms/agent/create-an-alert-using-an-error-number.md)  
  
-   [Affecter des alertes à un opérateur](../../ssms/agent/assign-alerts-to-an-operator.md)  
  
## <a name="permissions"></a>Permissions  
 Lorsque des stratégies sont évaluées à la demande, elles s'exécutent dans le contexte de sécurité de l'utilisateur. Pour écrire dans le journal des erreurs, l'utilisateur doit posséder l'autorisation ALTER TRACE ou être membre du rôle serveur fixe sysadmin. Les stratégies évaluées par un utilisateur qui dispose de moins de privilèges n'écrivent pas dans le journal des événements et ne déclenchent pas d'alerte.  
  
 Les modes d'exécution automatisés s'exécutent comme membre du rôle sysadmin. Cela permet à la stratégie d'écrire dans le journal des erreurs et de déclencher une alerte.  
  
## <a name="additional-considerations-about-alerts"></a>Considérations supplémentaires relatives aux alertes  
 Tenez compte des considérations supplémentaires relatives aux alertes :  
  
-   Des alertes sont déclenchées uniquement pour les stratégies activées. Comme les stratégies **À la demande** ne peuvent pas être activées, aucune alerte n’est déclenchée pour les stratégies exécutées sur demande.  
  
-   Si l'action que vous souhaitez effectuer inclut l'envoi d'un message électronique, vous devez configurer un compte de messagerie. Nous vous recommandons d'utiliser la Messagerie de base de données. Pour plus d’informations sur la manière de configurer la messagerie de base de données, consultez [Créer un compte de messagerie de base de données](../database-mail/create-a-database-mail-account.md).  
  
  
