---
title: Concepts XMLA | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, concepts
ms.assetid: 816183a7-d2f7-4e14-8e5b-2a4c1798fbc1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0da9467d293c0081309accd99fb46d7589fb4b8b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62736573"
---
# <a name="xmla-concepts"></a>Concepts XMLA
  La norme ouverte XMLA (XML for Analysis) prend en charge l'accès aux sources de données qui résident sur Internet. [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] implémente XMLA selon la spécification XMLA [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 1,1.  
  
 XMLA est un protocole XML basé sur SOAP ( Simple Object Access Protocol) conçu spécifiquement pour offrir un accès universel à n'importe quelle source de données multidimensionnelle standard résidant sur le Web. XMLA élimine également le besoin de déployer un composant client qui expose des interfaces COM (Component Object Model [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ) ou .NET Framework. XMLA est optimisé pour Internet, lorsque les va-et-vient vers le serveur sont coûteux en termes de temps et de ressources et que les connexions avec état à une source de données peuvent limiter les connexions utilisateur sur le serveur.  
  
 XMLA est le protocole natif de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], utilisé pour toute interaction entre une application cliente et une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]de. 
  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend entièrement en charge XML for Analysis 1.1 et fournit également des extensions pour prendre en charge les fonctionnalités de gestion des métadonnées, de gestion des sessions et de verrouillage. AMO (Analysis Management Objects) et ADOMD.NET utilisent tous deux le protocole XMLA pour communiquer avec une instance d'[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="handling-xmla-communications"></a>Gestion des communications XMLA  
 La norme ouverte XMLA décrit deux méthodes généralement accessibles : `Discover` et `Execute`. Ces méthodes utilisent l'architecture client et serveur faiblement couplée prise en charge par XML pour gérer les informations entrantes et sortantes sur une instance d'[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 La méthode `Discover` obtient des informations et des métadonnées auprès d'un service Web. Ces informations peuvent consister notamment en une liste de sources de données disponibles ou des informations sur les fournisseurs de sources de données. Les propriétés définissent et mettent en forme les données obtenues à partir d'une source de données. La méthode `Discover` est une méthode commune destinée à définir les nombreux types d'informations qu'une application cliente peut exiger des sources de données sur les instances [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Les propriétés et l'interface générique offrent une extensibilité sans qu'il soit nécessaire de réécrire les fonctions existantes d'une application cliente.  
  
 La méthode `Execute` permet aux applications d'exécuter des commandes spécifiques au fournisseur sur les sources de données XMLA.  
  
 Bien que le protocole XMLA soit optimisé pour les applications Web, il peut également être utilisé pour les applications orientées réseau local. Les applications suivantes peuvent bénéficier de cette API XML :  
  
-   applications client/serveur qui ont besoin d'une technologie flexible entre les clients et le serveur ;  
  
-   les applications client/serveur destinées à plusieurs systèmes d'exploitation ;  
  
-   les clients qui n'ont pas besoin d'un état significatif pour augmenter la capacité du serveur.  
  
## <a name="xmla-and-the-unified-dimensional-model"></a>XMLA et UDM  
 XMLA est le protocole utilisé par les applications décisionnelles qui emploient la méthodologie UDM (Unified Dimensional Model).  
  
  
