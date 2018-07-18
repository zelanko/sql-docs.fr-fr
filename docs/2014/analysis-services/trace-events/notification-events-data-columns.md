---
title: Événements de notification, colonnes de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Notification Events event category
ms.assetid: 0ecf06da-1586-415a-9da8-60d4c634f030
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6a436f613b39f5beb18a7dea40349ce24ded1bf5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37204069"
---
# <a name="notification-events-data-columns"></a>Colonnes de données d'événements de notification
  Les événements de notification sont des événements qui ne sont pas directement générés par les utilisateurs de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Par exemple, des notifications se déclenchent suite à la mise à jour par les utilisateurs des tables sous-jacentes pour la mise en cache proactive.  
  
 La catégorie d'événement Événements de notification a la classe d'événements suivante :  
  
|**ID d'événement**|**Nom d'événement**|**Description de l'événement**|  
|------------------|--------------------|---------------------------|  
|39|Notification|Événement de notification.|  
|40|Définis par l'utilisateur|Événement défini par l'utilisateur.|  
  
 Le tableau suivant répertorie les colonnes de données de la classe d'événements.  
  
## <a name="notification"></a>Notification  
  
|**Nom de la colonne**|**ID de la colonne**|**Type de colonne**|**Description de la colonne**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0| 1|Classe d'événements utilisée pour catégoriser les événements.|  
|EventSubclass| 1| 1|La sous-classe d'événements fournit des informations supplémentaires sur chaque classe d'événements. Les éléments suivants sont des paires de nom de sous-classe Id/sous-classe valide :<br /><br /> 0 : début de la mise en cache proactive<br />1 : fin de la mise en cache proactive<br />2 : boîte noire démarrée<br />3 : boîte noire arrêtée<br />4 : propriétés de configuration mises à jour<br />5 : trace SQL<br />6 : objet créé<br />7 : objet supprimé<br />8 : objet modifié<br />9 : début de l’interrogation de la mise en cache proactive<br />10 : fin de l’interrogation de la mise en cache proactive<br />11 : début de l’instantané de la boîte noire<br />12 : fin de l’instantané de la boîte noire<br />13 : mise en cache proactive : objet notifiable mis à jour<br />14 : traitement différé : début du traitement<br />15 : traitement différé : traitement terminé<br />16 : début de l’événement SessionOpened<br />17 : fin de l’événement SessionOpened<br />18 : début de l’événement SessionClosing<br />19 : fin de l’événement SessionClosing<br />20 : début de l’événement CubeOpened<br />21 : fin de l’événement CubeOpened<br />22 : début de l’événement CubeClosing<br />23 : fin de l’événement CubeClosing<br />24 : arrêt de transaction demandé|  
|CurrentTime|2|5|Contient l'heure actuelle de l'événement de notification, le cas échéant. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|StartTime|3|5|Contient l'heure de début de l'événement, le cas échéant. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|EndTime|4|5|Contient l'heure de fin de l'événement. Cette colonne n'est pas remplie pour les classes d'événements de démarrage, comme SQL:BatchStarting ou SP:Starting. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|Duration|5|2|Contient le temps (en millisecondes) utilisé par l'événement.|  
|IntegerData|10| 1|Contient les données entières associées à l'événement de notification. Lorsque la colonne EventSubclass contient la valeur 8, les valeurs sont :<br /><br /> 1 = Créé<br /><br /> 2 = Supprimé<br /><br /> 3 = Propriétés de l'objet modifié<br /><br /> 4 = Propriétés modifiées de l'enfant de l'objet<br /><br /> 6 = Enfant ajouté<br /><br /> 7 = Enfant supprimé<br /><br /> 8 = Objet complètement traité<br /><br /> 9 = Objet partiellement traité<br /><br /> 10 = Objet non traité<br /><br /> 11 = Objet complètement optimisé<br /><br /> 12 = Objet partiellement optimisé<br /><br /> 13 = Objet non optimisé|  
|ObjectID|11|8|Contient l'ID d'objet pour lequel cette notification est émise ; il s'agit d'une valeur de chaîne.|  
|ObjectType|12| 1|Contient le type d'objet associé à l'événement de notification.|  
|ObjectName|13|8|Contient le nom d'objet associé à l'événement de notification.|  
|ObjectPath|14|8|Contient le chemin d'accès à l'objet associé à l'événement de notification. Le chemin d'accès est retourné sous la forme d'une liste de parents séparés par une virgule commençant par le parent de l'objet.|  
|ObjectReference|15|8|Contient la référence d'objet de l'événement de fin du rapport de progression. La référence d'objet est encodée en langage XML en fonction de tous les parents en utilisant des balises pour décrire l'objet.|  
|ConnectionID|25| 1|Contient l'ID de connexion unique associé à l'événement de notification.|  
|DatabaseName|28|8|Contient le nom de la base de données dans laquelle l'événement de notification s'est produit.|  
|NTUserName|32|8|Contient le nom d'utilisateur Windows associé à l'événement de notification.|  
|NTDomainName|33|8|Domaine Windows auquel appartient l'utilisateur.|  
|SessionID|39|8|Contient l'ID de session associé à l'événement de notification.|  
|NTCanonicalUserName|40|8|Contient le nom d'utilisateur Windows associé à l'événement de notification. Le nom d'utilisateur a la forme canonique. engineering.microsoft.com/software/user, par exemple.|  
|SPID|41| 1|Contient l'ID de processus serveur (SPID, Server Process ID) qui identifie de manière unique la session utilisateur associée à l'événement de notification. Le SPID correspond directement au GUID de session utilisé par XMLA.|  
|TextData|42|9|Contient les données texte associées à l'événement de notification.|  
|ServerName|43|8|Contient le nom de l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur laquelle l'événement de notification s'est produit.|  
|RequestProperties|45|9|Contient les propriétés de la demande XMLA.|  
  
## <a name="user-defined"></a>Définis par l'utilisateur  
  
|**Nom de la colonne**|**ID de la colonne**|**Type de colonne**|**Description de la colonne**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0| 1|Classe d'événements utilisée pour catégoriser les événements.|  
|EventSubclass| 1| 1|Sous-classe d'événement spécifique de l'utilisateur qui fournit des informations supplémentaires sur chaque classe d'événements.|  
|CurrentTime|2|5|Contient l'heure actuelle de l'événement de notification, le cas échéant. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|IntegerData|10| 1|Informations d'événement définies par l'utilisateur.|  
|ConnectionID|25| 1|Contient l'ID de connexion unique associé à l'événement de notification.|  
|DatabaseName|28|8|Contient le nom de la base de données dans laquelle l'événement de notification s'est produit.|  
|NTUserName|32|8|Contient le nom d'utilisateur Windows associé à l'événement de notification.|  
|NTDomainName|33|8|Domaine Windows auquel appartient l'utilisateur.|  
|SessionID|39|8|Contient l'ID de session associé à l'événement de notification.|  
|NTCanonicalUserName|40|8|Contient le nom d'utilisateur Windows associé à l'événement de notification. Le nom d'utilisateur a la forme canonique. engineering.microsoft.com/software/user, par exemple.|  
|SPID|41| 1|Contient l'ID de processus serveur (SPID, Server Process ID) qui identifie de manière unique la session utilisateur associée à l'événement de notification. Le SPID correspond directement au GUID de session utilisé par XMLA.|  
|TextData|42|9|Contient les données texte associées à l'événement de notification.|  
|ServerName|43|8|Contient le nom de l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur laquelle l'événement de notification s'est produit.|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements de notification, catégorie d’événement](notification-events-event-category.md)  
  
  
