---
title: Propriétés de l’alerte-nouvelle alerte (page général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.general.f1
ms.assetid: f5c11610-62e3-44df-9800-a5dc35be4a09
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ca5b07a0cd6e6282e4d61075d86ca6af6a2abd70
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63062145"
---
# <a name="alert-properties-new-alert-general-page"></a>Propriétés de l’alerte-nouvelle alerte (page général)
  Utilisez cette page pour afficher et modifier les propriétés générales des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alertes de l’agent.  
  
## <a name="options"></a>Options  
 **Nom**  
 Modifiez le nom de l'alerte.  
  
 **Activer**  
 Active l'alerte. Si l'alerte n'est pas activée, les actions spécifiées dans celle-ci n'ont pas lieu.  
  
 **Type**  
 Sélectionnez le type d'alerte :  
  
-   **SQL Server alerte d’événement** répond aux messages dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] le journal des événements Windows.  
  
-   **SQL Server alerte de condition de performance** répond à une condition spécifique dans un compteur de performance.  
  
-   L' **alerte d’événement WMI** répond à un événement de Windows Management Instrumentation (WMI).  
  
## <a name="sql-server-event-alert-options"></a>Options des alertes d'événement SQL Server  
 **Nom de la base de données**  
 Indiquez une base de données pour l’événement, ou sélectionnez **Toutes les bases de données** pour répondre à un message quelle que soit la base de données dans laquelle l’événement a lieu.  
  
 **Numéro d’erreur**  
 Indique que cet événement répond à une erreur. Précisez le numéro de l'erreur.  
  
 **severity**  
 Indique que cet événement répond à un message quelconque d'un niveau de gravité spécifique. Précisez le niveau de gravité.  
  
 **Déclencher une alerte quand le message contient**  
 Filtre les événements d'après une chaîne spécifique. Si cette option est sélectionnée, l'alerte répond uniquement aux événements contenant cette chaîne.  
  
 **Texte du message**  
 Spécifiez la chaîne à utiliser pour filtrer les événements.  
  
## <a name="sql-server-performance-condition-alerts"></a>Alertes de condition de performances de SQL Server  
 **Object**  
 Précisez l'objet de performance à surveiller.  
  
 **Compteur**  
 Précisez le compteur à surveiller au sein de l'objet de performance.  
  
 **Instance**  
 Indiquez l'instance du compteur à surveiller.  
  
 **Alerte si le compteur**  
 Spécifiez le comportement du compteur auquel l'alerte répond. Par exemple, vous pouvez faire en sorte que l’alerte réponde à une baisse de la valeur du compteur **Espace disponible dans tempdb (Ko)** en deçà d’une valeur spécifiée, ou à un dépassement d’une valeur spécifiée par la valeur du compteur **Compilations SQL/s** .  
  
 **Valeur**  
 Spécifiez une valeur pour le compteur.  
  
## <a name="wmi-event-alert-options"></a>Options des alertes d'événement WMI  
 **Espace de noms**  
 Spécifiez l'espace de noms à utiliser pour l'instruction WQL (WMI Query Language). Seuls les espaces de noms résidant sur l'ordinateur qui exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont pris en charge.  
  
 **Requête**  
 Spécifiez l'instruction WQL identifiant l'événement auquel l'alerte répond.  
  
## <a name="see-also"></a>Voir aussi  
 [Alerts](alerts.md)   
 [Utilisation de WQL avec le fournisseur WMI pour les événements de serveur](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)   
 [Créer une alerte en utilisant un numéro d’erreur](create-an-alert-using-an-error-number.md)   
 [Créer une alerte à l'aide d'un niveau de gravité](create-an-alert-using-severity-level.md)  
  
  
