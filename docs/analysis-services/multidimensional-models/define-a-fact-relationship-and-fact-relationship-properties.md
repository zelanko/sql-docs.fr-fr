---
title: Définir une relation de faits et les propriétés de relation de faits | Documents Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4206cdda1b608b8cb22adaca531b917e80b94571
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>Définir une relation de fait et des propriétés de relation de fait
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Quand vous définissez une nouvelle dimension de cube ou un nouveau groupe de mesures, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tente de détecter si une relation de dimension de fait existe et attribut la valeur **Fait**au paramètre d’utilisation de la dimension. Vous pouvez afficher ou modifier une relation de dimension de fait sur l'onglet **Utilisation de la dimension** du Concepteur de cube. La relation de fait entre une dimension et un groupe de mesures a les contraintes suivantes :  
  
-   Une dimension de cube ne peut avoir qu'une seule relation de fait avec un groupe de mesures donné.  
  
-   Une dimension de cube peut avoir des relations de fait distinctes avec plusieurs groupes de mesures.  
  
-   L'attribut de granularité de la relation doit correspondre à l'attribut clé (comme le numéro de transaction) de la dimension. Cela crée une relation de type un-à-un entre les faits et la dimension de la table de faits.  
  
  
