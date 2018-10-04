---
title: Définir une relation de faits et les propriétés de relation de faits | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- fact dimensions [Analysis Services]
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6663b3a488ff073c823ad8f67ef3a1d120c4a268
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48197420"
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>Définir une relation de fait et des propriétés de relation de fait
  Quand vous définissez une nouvelle dimension de cube ou un nouveau groupe de mesures, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tente de détecter si une relation de dimension de fait existe et attribut la valeur `Fact` au paramètre d'utilisation de la dimension. Vous pouvez afficher ou modifier une relation de dimension de fait sur l'onglet **Utilisation de la dimension** du Concepteur de cube. La relation de fait entre une dimension et un groupe de mesures a les contraintes suivantes :  
  
-   Une dimension de cube ne peut avoir qu'une seule relation de fait avec un groupe de mesures donné.  
  
-   Une dimension de cube peut avoir des relations de fait distinctes avec plusieurs groupes de mesures.  
  
-   L'attribut de granularité de la relation doit correspondre à l'attribut clé (comme le numéro de transaction) de la dimension. Cela crée une relation de type un-à-un entre les faits et la dimension de la table de faits.  
  
  
