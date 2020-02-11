---
title: Composants du serveur du moteur OLAP | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- ports [Analysis Services]
- XML/A listener
- server architecture [Analysis Services]
ms.assetid: 5193c976-9dcd-459c-abba-8c3c44e7a7f2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0537be8bda9c367fc381140183b10ddf383cf16a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68889525"
---
# <a name="olap-engine-server-components"></a>Composants serveur du moteur OLAP
  Le composant serveur de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] est l’application **msmdsrv. exe** , qui s’exécute en tant que service Windows. Cette application intègre des composants de sécurité, un composant d'écoute XMLA (XML for Analysis), un composant processeur de requêtes et de nombreux autres composants internes qui permettent d'effectuer les actions suivantes :  
  
-   Analyser des instructions reçues des clients  
  
-   Gérer des métadonnées  
  
-   Gérer des transactions  
  
-   Effectuer des calculs  
  
-   Stocker des données de dimension et de cellule  
  
-   Créer des agrégations  
  
-   Planifier des requêtes  
  
-   Mettre des objets en cache  
  
-   Gérer des ressources du serveur  
  
## <a name="architectural-diagram"></a>Diagramme architectural  
 Une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] s’exécute comme un service autonome et la communication avec le service s’effectue via XML for Analysis (XMLA), à l’aide de HTTP ou de TCP. AMO est une couche entre l'application utilisateur et l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Cette couche donne accès aux objets d'administration [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. AMO est une bibliothèque de classes qui prend des commandes d’une application cliente et convertit ces commandes en messages XMLA pour l’instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . AMO présente les objets d'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] en tant que classes à l'application de l'utilisateur final, avec des membres de méthode qui exécutent des commandes et des membres de propriété qui contiennent les données des objets [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
 L'illustration suivante présente l'architecture des composants [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], y compris tous les éléments majeurs s'exécutant dans l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] et tous les composants utilisateur qui interagissent avec l'instance. L'illustration montre également que la seule façon d'accéder à l'instance est d'utiliser le composant d'écoute XMLA (XML for Analysis), à l'aide de HTTP ou TCP.  
  
 ![Schéma de l'architecture système Analysis Services](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/analysisservicessystemarchitecture.gif "Schéma de l'architecture système Analysis Services")  
  
## <a name="xmla-listener"></a>Écouteur XMLA  
 Le composant écouteur XMLA gère toutes les communications XMLA entre [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] et ses clients. Le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] `Port` paramètre de configuration dans le fichier msmdsrv. ini peut être utilisé pour spécifier un port sur lequel [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] une instance écoute. La valeur 0 dans ce fichier indique qu' [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] écoute sur le port par défaut. Sauf spécification contraire, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utilise par défaut les ports TCP suivants :  
  
|Port|Description|  
|----------|-----------------|  
|2383|Instance par défaut [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]de.|  
|2382|Redirecteur pour d’autres instances [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]de.|  
|Affectation dynamique au démarrage du serveur|Instance nommée de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
 Pour plus d’informations, consultez [configurer le pare-feu Windows pour autoriser l’accès à la Analysis Services](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Règles d’affectation des noms d’objets &#40;Analysis Services&#41;](object-naming-rules-analysis-services.md)   
 [Architecture physique &#40;Analysis Services-données multidimensionnelles&#41;](understanding-microsoft-olap-physical-architecture.md)   
 [Architecture logique &#40;Analysis Services-données multidimensionnelles&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)  
  
  
