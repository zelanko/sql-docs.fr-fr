---
title: Perspectives | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- ready-only cube view
- OLAP objects [Analysis Services], perspectives
- storing data [Analysis Services], perspectives
- perspectives [Analysis Services]
- cubes [Analysis Services], perspectives
- visibility [Analysis Services]
- storage [Analysis Services], perspectives
ms.assetid: b064171e-b1b4-4f32-95e5-59e1b831c4c9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2856bca26e8a49ffdb2ed5187479434c7762015b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62702624"
---
# <a name="perspectives"></a>perspectives
  Une perspective est une définition qui permet aux utilisateurs de consulter un cube de façon plus simple. Une perspective est un sous-ensemble des fonctionnalités d'un cube. Une perspective permet aux administrateurs de créer des vues d'un cube, aidant ainsi les utilisateurs à se concentrer sur les données les plus pertinentes pour eux. Une perspective contient les sous-ensembles de tous les objets d'un cube. Une perspective ne peut pas inclure les éléments qui ne sont pas définis dans le cube parent.  
  
 Un objet <xref:Microsoft.AnalysisServices.Perspective> simple est composé d’informations de base, de dimensions, de groupes de mesures, de calculs, d’indicateurs de performance clé et d’actions. Les informations de base comprennent le nom et la mesure par défaut de la perspective. Les dimensions sont un sous-ensemble des dimensions du cube. Les groupes de mesures sont un sous-ensemble des groupes de mesures du cube. Les calculs sont un sous-ensemble des calculs du cube. Les indicateurs de performance clé sont un sous-ensemble des indicateurs de performance clé du cube. Les actions sont un sous-ensemble des actions du cube.  
  
 Un cube doit être mis à jour et traité avant que la perspective ne puisse être utilisée.  
  
 Les cubes peuvent être des objets très complexes que les utilisateurs [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]peuvent explorer dans. Un cube unique peut représenter le contenu d'un entrepôt de données entier, avec plusieurs groupes de mesures dans un cube représentant plusieurs tables de faits et avec plusieurs dimensions reposant sur plusieurs tables de dimension. Ce type de cube peut être très complexe et très puissant, mais difficile à utiliser pour ceux qui n'ont besoin d'interagir qu'avec une petite partie du cube afin de répondre à leurs besoins en termes de décisionnel et de rapports.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez utiliser une perspective pour réduire la complexité perçue d’un cube [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]dans. Une perspective définit un sous-ensemble visualisable d'un cube qui fournit des points de vue focalisés sur un domaine d'activité ou sur une application. La perspective contrôle la visibilité des objets contenus dans un cube. Les objets suivants peuvent être affichés ou masqués dans une perspective :  
  
-   Dimensions  
  
-   Attributs  
  
-   Hierarchies  
  
-   les groupes de mesures ;  
  
-   mesures  
  
-   les indicateurs de performance clés (KPI) ;  
  
-   les calculs (membres calculés, jeux nommés et commandes script) ;  
  
-   Actions  
  
 Par exemple, le cube **Adventure Works** de l' [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] exemple [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de base de données contient onze groupes de mesures et vingt-et-une dimensions de cube différentes, représentant les ventes, les prévisions de ventes et les données financières. Une application cliente peut faire directement référence à la totalité du cube, mais ce point de vue peut être trop important si un utilisateur tente d'extraire des informations de base sur les ventes prévisionnelles. Au lieu de cela, le même utilisateur peut utiliser la perspective **Sales targets** pour limiter l’affichage du cube **Adventure Works** aux objets pertinents pour les prévisions de ventes.  
  
 Les objets d'un cube qui ne sont pas visibles pour l'utilisateur via une perspective peuvent cependant être directement référencés et récupérés à l'aide de XML for Analysis, des expressions MDX (Multidimensional Expressions) ou des instructions DMX (Data Mining Extensions). Les perspectives ne restreignent pas l'accès aux objets d'un cube et ne doivent pas être utilisées à cette fin. Elles doivent au contraire servir à optimiser l'expérience de l'utilisateur lorsqu'il accède à un cube.  
  
 Une perspective est une vue en lecture seule du cube ; les objets du cube ne peuvent pas être renommés ni modifiés à l'aide d'une perspective. De la même façon, le comportement ou les fonctionnalités d'un cube, comme l'utilisation de valeurs visibles, ne peuvent pas être modifiés à l'aide d'une perspective.  
  
## <a name="security"></a>Sécurité  
 Les perspectives ne sont pas censées servir de mécanisme de sécurité, mais elles constituent plutôt un outil qui optimise l'expérience de l'utilisateur dans les applications de décisionnel. L'intégralité de la sécurité d'une perspective donnée est héritée du cube sous-jacent. Par exemple, les perspectives ne peuvent pas donner accès aux objets d'un cube auxquels un utilisateur n'a pas déjà accès. La sécurité du cube doit d'abord être résolue, avant que l'utilisateur ne puisse accéder aux objets d'un cube par le biais d'une perspective.  
  
  
