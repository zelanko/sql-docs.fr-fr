---
title: Annulation de commandes (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- connections [XML for Analysis]
- associated connections [XML for Analysis]
- XML for Analysis, canceling
- associated sessions [XML for Analysis]
- canceling connections
- canceling commands
- canceling sessions
- SPID
- XMLA, canceling
- server process IDs [XML for Analysis]
- sessions [XML for Analysis]
ms.assetid: b59f8197-c33d-4e65-9022-848ccba540f5
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5129dd84cdd120b778fb55986374d27055b5904c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041230"
---
# <a name="canceling-commands-xmla"></a>Annulation de commandes (XMLA)
  En fonction des autorisations d’administration de l’utilisateur qui émet la commande, le [Annuler](../xmla/xml-elements-commands/cancel-element-xmla.md) commande en XML pour Analysis (XMLA) peut annuler une commande sur une session, une session, une connexion, un processus de serveur ou une session associée ou connexion.  
  
## <a name="canceling-commands"></a>Annulation de commandes  
 Un utilisateur peut annuler la commande en cours d'exécution dans le contexte de la session explicite active en envoyant une commande `Cancel` sans aucune propriété spécifiée.  
  
> [!NOTE]  
>  Une commande en cours d'exécution dans une session implicite ne peut pas être annulée par un utilisateur.  
  
### <a name="canceling-batch-commands"></a>Annulation de commandes Batch  
 Si un utilisateur annule une commande `Batch`, toutes les commandes qu'il reste à exécuter dans la commande `Batch` sont annulées. Si la commande `Batch` était transactionnelle, les commandes qui ont été exécutées avant l'exécution de la commande `Cancel` sont annulées.  
  
## <a name="canceling-sessions"></a>Annulation de sessions  
 En spécifiant un identificateur de session pour une session explicite dans le [SessionID](../xmla/xml-elements-properties/id-element-xmla.md) propriété de la `Cancel` de commande, un administrateur de base de données ou un administrateur de serveur peut annuler une session, y compris la commande en cours d’exécution . Un administrateur de base de données ne peut annuler les sessions que pour les bases de données pour lesquelles il dispose d'autorisations administratives.  
  
 Un administrateur de base de données peut récupérer les sessions actives pour une base de données spécifiée en récupérant l'ensemble de lignes de schéma DISCOVER_SESSIONS. Pour récupérer l’ensemble de lignes de schéma DISCOVER_SESSIONS, l’administrateur de base de données utilise le code XMLA `Discover` (méthode) et spécifie l’identificateur de la base de données appropriée pour le type de restriction session_current_database dans la [Restrictions](../xmla/xml-elements-properties/restrictions-element-xmla.md) propriété de la `Discover` (méthode).  
  
## <a name="canceling-connections"></a>Annulation de connexions  
 En spécifiant un identificateur de connexion dans le [ConnectionID](../xmla/xml-elements-properties/connectionid-element-xmla.md) propriété de la `Cancel` de commande, un administrateur de serveur peut annuler toutes les sessions associées à une connexion donnée, y compris toutes les commandes en cours d’exécution, et Annuler la connexion.  
  
> [!NOTE]  
>  Si l’instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne peut pas localiser et annuler les sessions associées à une connexion, telles que lorsque la pompe à données ouvre plusieurs sessions en fournissant une connectivité HTTP, l’instance ne peut pas annuler la connexion. Si ce cas est rencontré pendant l'exécution d'une commande `Cancel`, une erreur se produit.  
  
 Un administrateur de serveur peut récupérer les connexions actives pour une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en récupérant l'ensemble de lignes de schéma DISCOVER_CONNECTIONS à l'aide de la méthode XMLA `Discover`.  
  
## <a name="canceling-server-processes"></a>Annulation de processus serveur  
 En spécifiant un identificateur de processus serveur (SPID) dans le [SPID](../xmla/xml-elements-properties/spid-element-xmla.md) propriété de la `Cancel` de commande, un administrateur de serveur peut annuler les commandes associées à un SPID donné.  
  
## <a name="canceling-associated-sessions-and-connections"></a>Annulation de sessions et de connexions associées  
 Vous pouvez définir le [CancelAssociated](../xmla/xml-elements-properties/cancelassociated-element-xmla.md) propriété à true pour annuler les connexions, les sessions et les commandes associées à la connexion, la session ou le SPID spécifié dans le `Cancel` commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode Discover &#40;XMLA&#41;](../xmla/xml-elements-methods-discover.md)   
 [Développement avec XMLA dans Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  