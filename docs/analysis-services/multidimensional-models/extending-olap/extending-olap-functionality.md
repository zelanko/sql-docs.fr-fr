---
title: Étendre les fonctionnalités OLAP | Documents Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0c162058798051fc57ecb57038e6914969ef39f9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="extending-olap-functionality"></a>Étendre les fonctionnalités OLAP
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  En tant que programmeur, vous pouvez étendre Analysis Services en entrant des assemblys, des extensions personnalisées et des procédures stockées pour fournir les fonctionnalités que vous souhaitez utiliser et rediriger dans plusieurs applications de base de données. Les assemblys sont utilisés pour étendre les fonctionnalités de modèles multidimensionnels en ajoutant de nouvelles procédures et fonctions au langage MDX ou au moyen du complément de personnalisation.  
  
 Les procédures stockées peuvent être utilisées pour appeler des routines externes, ce qui simplifie le développement et l'implémentation de la base de données Analysis Services grâce au développement d'un code commun qui est stocké dans un seul emplacement. Les procédures stockées peuvent être utilisées pour ajouter à vos applications des fonctionnalités métier qui ne sont pas fournies par les fonctionnalités natives de MDX.  
  
 Les personnalisations sont des objets personnalisés que vous ajoutez à un cube pour fournir un comportement qui varie selon l'utilisateur. Les personnalisations ne sont pas des objets permanents dans le cube. Il s'agit d'objets que l'application cliente applique dynamiquement pendant la session de l'utilisateur. Voici quelques exemples : modifier la devise d'une valeur monétaire en fonction de la personne qui accède aux données en fournissant des indicateurs de performance clés individualisés, ou créer une liste ciblée de suggestions pour les clients standard qui achètent en ligne.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Extension d’OLAP par des personnalisations](../../../analysis-services/multidimensional-models/extending-olap/extending-olap-through-personalizations.md)  
  
 [Extensions de personnalisation de Analysis Services](../../../analysis-services/multidimensional-models/extending-olap/analysis-services-personalization-extensions.md)  
  
 [Définition de procédures stockées](../../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
