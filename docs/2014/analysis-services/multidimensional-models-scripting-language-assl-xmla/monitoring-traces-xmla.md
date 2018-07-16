---
title: Surveillance de Traces (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, traces
- XMLA, traces
- monitoring traces [XMLA]
- traces [Analysis Services]
ms.assetid: cdbfb984-18bd-4c4e-8fb7-d64ce298ed35
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d9df7fd3e22c8e63873584491c7f2051e8897efa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241619"
---
# <a name="monitoring-traces-xmla"></a>Surveillance de traces (XMLA)
  Vous pouvez utiliser la [s’abonner](../xmla/xml-elements-commands/subscribe-element-xmla.md) commande XML for Analysis (XMLA) pour surveiller une trace existante définie sur une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. La commande `Subscribe` retourne les résultats d'une trace sous la forme d'un ensemble de lignes.  
  
## <a name="specifying-a-trace"></a>Spécification d'une trace  
 Le [objet](../xmla/xml-elements-properties/object-element-xmla.md) propriété de la `Subscribe` commande doit contenir une référence d’objet à un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance ou une trace sur un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance. Si la propriété `Object` n'est pas spécifiée ou si aucun identificateur de trace n'y est `Object` spécifié, la commande `Subscribe` surveille la trace de session par défaut pour la session explicite spécifiée dans l'en-tête SOAP de la commande.  
  
## <a name="returning-results"></a>Retour de résultats  
 La commande `Subscribe` retourne un ensemble de lignes contenant les événements de trace capturés par la trace spécifiée. Le `Subscribe` commande retourne les résultats de trace jusqu'à ce que la commande est annulée par le [Annuler](../xmla/xml-elements-commands/cancel-element-xmla.md) commande.  
  
 Cet ensemble de lignes se compose des colonnes répertoriées dans le tableau suivant.  
  
|colonne|Data type|Description|  
|------------|---------------|-----------------|  
|EventClass|Entier|Classe d'événements de l'événement reçu par la trace.|  
|EventSubclass|Entier long|Sous-classe d'événements de l'événement reçu par la trace.|  
|CurrentTime|DATETIME|Heure de début de l'événement, le cas échéant. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|StartTime|DATETIME|Heure de début de l'événement, le cas échéant. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|EndTime|DATETIME|Heure de fin de l'événement, si elle est disponible. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».<br /><br /> Cette colonne n'est pas remplie pour les classes d'événements qui décrivent le lancement d'un processus ou d'une action.|  
|Duration|Entier long|Durée totale (en millisecondes) de l'événement.|  
|CPUTime|Entier long|Temps processeur total (en millisecondes) écoulé pour l'événement.|  
|JobID|Entier long|Identificateur de travail du processus.|  
|SessionID|String|Identificateur de la session pour laquelle l'événement s'est produit.|  
|SessionType|String|Type de la session pour laquelle l'événement s'est produit.|  
|ProgressTotal|Entier long|Nombre total ou progression signalé par l'événement.|  
|IntegerData|Entier long|Données entières associées à l'événement. Le contenu de cette colonne dépend de la classe et de la sous-classe d'événements de l'événement.|  
|ObjectID|String|Identificateur de l'objet pour lequel l'événement s'est produit.|  
|ObjectType|String|Type de l'objet spécifié dans ObjectName.|  
|ObjectName|String|Nom de l'objet pour lequel l'événement s'est produit.|  
|ObjectPath|String|Chemin d'accès hiérarchique de l'objet pour lequel l'événement s'est produit. Le chemin d'accès est représenté par une chaîne délimitée par des virgules correspondant aux identificateurs d'objet des parents de l'objet spécifiés dans ObjectName.|  
|ObjectReference|String|Représentation XML de la référence de l'objet spécifié dans ObjectName.|  
|NestLevel|Entier|Niveau de la transaction pour laquelle l'événement s'est produit.|  
|NumSegments|Entier long|Nombre de segments de données affectés ou atteints par la commande pour laquelle l'événement s'est produit.|  
|Severity|Entier|Niveau de gravité d'une exception relative à l'événement. La colonne peut contenir l'une des valeurs suivantes :<br /><br /> Valeur : 0 = succès<br /><br /> Valeur : 1 = les informations<br /><br /> Valeur : 2 = avertissement<br /><br /> Valeur : 3 = Erreur|  
|Réussi|Booléen|Indique si une commande a abouti ou échoué.|  
|Error|Entier long|Numéro d'erreur de l'événement, le cas échéant.|  
|ConnectionID|String|Identificateur de la connexion pour laquelle l'événement s'est produit.|  
|DatabaseName|String|Nom de la base de données pour laquelle l'événement s'est produit.|  
|NTUserName|String|Nom d'utilisateur Windows de l'utilisateur associé à l'événement.|  
|NTDomainName|String|Domaine Windows de l'utilisateur associé à l'événement.|  
|ClientHostName|String|Nom de l'ordinateur sur lequel l'application cliente est exécutée. Cette colonne est remplie des valeurs transmises par l'application cliente.|  
|ClientProcessID|Entier long|Identificateur de processus de l'application cliente.|  
|ApplicationName|String|Nom de l'application cliente qui a créé la connexion à l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Cette colonne est remplie des valeurs transmises par l'application cliente et non du nom affiché du programme.|  
|NTCanonicalUserName|String|Nom d'utilisateur canonique Windows de l'utilisateur associé à l'événement.|  
|SPID|String|ID de processus serveur (SPID) de la session pour laquelle l'événement s'est produit. La valeur de cette colonne correspond directement à l'ID de session spécifié dans l'en-tête SOAP du message XMLA pour lequel l'événement s'est produit.|  
|TextData|String|Les données de texte associées à l’événement. Le contenu de cette colonne dépend de la classe et de la sous-classe d'événements de l'événement.|  
|ServerName|String|Nom de l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour laquelle l'événement s'est produit.|  
|RequestParameters|String|Paramètres de la requête paramétrable ou de la commande XMLA pour laquelle l'événement s'est produit.|  
|RequestProperties|String|Propriétés de la méthode XMLA pour laquelle l'événement s'est produit.|  
  
## <a name="see-also"></a>Voir aussi  
 [Développement avec XMLA dans Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
