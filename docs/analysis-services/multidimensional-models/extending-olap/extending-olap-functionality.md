---
title: "Étendre les fonctionnalités OLAP | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 49a17ff3-94e9-4969-84fc-37d49e63933b
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 20749b47397d4cd1826fbdca65be78e7f1905025
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="extending-olap-functionality"></a>Étendre les fonctionnalités OLAP
  En tant que programmeur, vous pouvez étendre Analysis Services en entrant des assemblys, des extensions personnalisées et des procédures stockées pour fournir les fonctionnalités que vous souhaitez utiliser et rediriger dans plusieurs applications de base de données. Les assemblys sont utilisés pour étendre les fonctionnalités de modèles multidimensionnels en ajoutant de nouvelles procédures et fonctions au langage MDX ou au moyen du complément de personnalisation.  
  
 Les procédures stockées peuvent être utilisées pour appeler des routines externes, ce qui simplifie le développement et l'implémentation de la base de données Analysis Services grâce au développement d'un code commun qui est stocké dans un seul emplacement. Les procédures stockées peuvent être utilisées pour ajouter à vos applications des fonctionnalités métier qui ne sont pas fournies par les fonctionnalités natives de MDX.  
  
 Les personnalisations sont des objets personnalisés que vous ajoutez à un cube pour fournir un comportement qui varie selon l'utilisateur. Les personnalisations ne sont pas des objets permanents dans le cube. Il s'agit d'objets que l'application cliente applique dynamiquement pendant la session de l'utilisateur. Voici quelques exemples : modifier la devise d'une valeur monétaire en fonction de la personne qui accède aux données en fournissant des indicateurs de performance clés individualisés, ou créer une liste ciblée de suggestions pour les clients standard qui achètent en ligne.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Extension d’OLAP par des personnalisations](../../../analysis-services/multidimensional-models/extending-olap/extending-olap-through-personalizations.md)  
  
 [Extensions de personnalisation de Analysis Services](../../../analysis-services/multidimensional-models/extending-olap/analysis-services-personalization-extensions.md)  
  
 [Définition de procédures stockées](../../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  

