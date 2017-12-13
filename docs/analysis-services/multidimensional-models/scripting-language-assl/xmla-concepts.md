---
title: Concepts XMLA | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: XMLA, concepts
ms.assetid: 816183a7-d2f7-4e14-8e5b-2a4c1798fbc1
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5dca0d0e247a985194109651ad14810d98a570e9
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="xmla-concepts"></a>Concepts XMLA
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]La norme XML for Analysis (XMLA) Ouvrez prend en charge l’accès aux sources de données qui résident sur le World Wide Web. [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] implémente XMLA selon la spécification XMLA 1.1.  
  
 XMLA est un protocole XML basé sur SOAP ( Simple Object Access Protocol) conçu spécifiquement pour offrir un accès universel à n'importe quelle source de données multidimensionnelle standard résidant sur le Web. XMLA élimine également la nécessité de déployer un composant client qui expose le modèle COM (Component Object) ou [!INCLUDE[msCoName](../../../includes/msconame-md.md)] interfaces de .NET Framework. XMLA est optimisé pour Internet, lorsque les va-et-vient vers le serveur sont coûteux en termes de temps et de ressources et que les connexions avec état à une source de données peuvent limiter les connexions utilisateur sur le serveur.  
  
 XMLA est le protocole natif pour [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]utilisé pour toutes les interactions entre une application cliente et une instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend entièrement en charge XML for Analysis 1.1 et fournit également des extensions pour prendre en charge les fonctionnalités de gestion des métadonnées, de gestion des sessions et de verrouillage. AMO (Analysis Management Objects) et ADOMD.NET utilisent tous deux le protocole XMLA pour communiquer avec une instance d'[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="handling-xmla-communications"></a>Gestion des communications XMLA  
 La norme ouverte XMLA décrit deux méthodes généralement accessibles : **Discover** et **Execute**. Ces méthodes utilisent l'architecture client et serveur faiblement couplée prise en charge par XML pour gérer les informations entrantes et sortantes sur une instance d'[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Le **Discover** méthode obtient des informations et des métadonnées à partir d’un service Web. Ces informations peuvent consister notamment en une liste de sources de données disponibles ou des informations sur les fournisseurs de sources de données. Les propriétés définissent et mettent en forme les données obtenues à partir d'une source de données. Le **Discover** méthode est une méthode courante pour définir les nombreux types d’informations d’une application cliente peut nécessiter des sources de données sur [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instances. Les propriétés et l'interface générique offrent une extensibilité sans qu'il soit nécessaire de réécrire les fonctions existantes d'une application cliente.  
  
 Le **Execute** méthode permet aux applications d’exécuter des commandes spécifiques au fournisseur sur les sources de données XMLA.  
  
 Bien que le protocole XMLA soit optimisé pour les applications Web, il peut également être utilisé pour les applications orientées réseau local. Les applications suivantes peuvent bénéficier de cette API XML :  
  
-   applications client/serveur qui ont besoin d'une technologie flexible entre les clients et le serveur ;  
  
-   les applications client/serveur destinées à plusieurs systèmes d'exploitation ;  
  
-   les clients qui n'ont pas besoin d'un état significatif pour augmenter la capacité du serveur.  
  
## <a name="xmla-and-the-unified-dimensional-model"></a>XMLA et UDM  
 XMLA est le protocole utilisé par les applications décisionnelles qui emploient la méthodologie UDM (Unified Dimensional Model).  
  
  
