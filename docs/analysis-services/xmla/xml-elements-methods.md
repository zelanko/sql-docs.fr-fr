---
title: Méthodes (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a479bd17bfd0c7a617baea4cbabffaa08fa68936
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="xml-elements---methods"></a>Éléments XML - méthodes
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Le protocole XML for Analysis (XMLA) utilise deux méthodes, **Discover** et **Execute**, pour offrir un moyen standard pour les applications d’accéder aux informations sur une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Ces méthodes étant appelées à l'aide du protocole SOAP (Simple Object Access Protocol), elles acceptent des entrées et affichent les sorties au format XML. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implémente les deux méthodes conformément à la spécification XML for Analysis 1.1.  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques suivantes décrivent les méthodes XMLA mises en œuvre par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Méthode| Description|  
|------------|-----------------|  
|[Méthode Discover &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)|Récupère des informations (notamment la liste des bases de données disponibles) ou des détails concernant un objet spécifique à partir d'une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les données récupérées avec le **Discover** méthode varie selon les valeurs des paramètres passés à ce dernier.|  
|[Exécuter la méthode &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)|Transmet des commandes XMLA à une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Ceci inclut des demandes qui impliquent un transfert de données (par exemple, la récupération ou la mise à jour de données sur le serveur).|  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments XML & #40 ; XMLA & #41 ;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Types de données XML & #40 ; XMLA & #41 ;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [Éléments XML & #40 ; XMLA & #41 ;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)  
  
  
