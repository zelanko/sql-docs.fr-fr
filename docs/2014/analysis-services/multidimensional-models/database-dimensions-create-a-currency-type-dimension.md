---
title: Créer une Dimension de type devise | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], currency
- currency [Analysis Services]
- converting currency
- currency dimensions [Analysis Services]
ms.assetid: b1f037d1-ce47-4e47-a1c2-5ec9e781cff6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dc9b89f4c1d3a1a44d5a568a47d16276639bb4cf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140389"
---
# <a name="create-a-currency-type-dimension"></a>Créer une dimension de type monétaire
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], une dimension de type monétaire est une dimension dont les attributs représentent une liste de devises utilisée dans les rapports financiers.  
  
 Une dimension monétaire permet d'ajouter des fonctions de conversion monétaire à un cube dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Pour ajouter une conversion monétaire à un cube, utilisez l'Assistant Business Intelligence pour définir une commande de script MDX (Multidimensional Expressions) qui convertit les mesures monétaires en valeurs correspondant aux paramètres régionaux de l'application cliente. Pour créer ce script MDX, vous devez fournir les informations suivantes à l'Assistant Business Intelligence :  
  
-   Une dimension monétaire qui représente les devises sources. (Cette dimension est la dimension monétaire source.)  
  
-   Un groupe de mesures qui représente les taux de change à utiliser.  
  
 À partir de ces informations, l'Assistant Business Intelligence crée un processus de conversion monétaire qui identifie la dimension monétaire de destination appropriée (la dimension monétaire qui représente les devises de destination). Selon le nombre de conversions monétaires nécessaires à la solution décisionnelle, l'Assistant Business Intelligence peut définir plusieurs dimensions monétaires de destination. Pour plus d’informations sur la définition de conversions monétaires, consultez [Conversions monétaires &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md).  
  
 Pour définir une dimension comme dimension monétaire, affectez la `Type` propriété de la dimension à `Currency`.  
  
## <a name="dimension-structure"></a>Structure de la dimension  
 Une dimension monétaire contient au moins un attribut clé qui identifie les devises dans la table de la dimension monétaire. La valeur de l'attribut clé est différente dans les dimensions monétaires source et de destination :  
  
-   Pour définir un attribut comme attribut clé d'une dimension monétaire source, affectez à la propriété `Type` de l'attribut la valeur `CurrencySource`.  
  
-   Pour définir un attribut comme dimension monétaire de destination, affectez la `Type` propriété de l’attribut à `CurrencyDestination`.  
  
 Pour les rapports, les dimensions monétaires source et de destination peuvent contenir éventuellement les attributs suivants :  
  
-   Un attribut de nom de devise  
  
     Pour définir un attribut comme attribut de nom de devise, affectez à la propriété `Type` de l'attribut la valeur `CurrencyName`.  
  
-   Un attribut de source de devise  
  
     Pour définir un attribut comme attribut de source de devise, affectez à la propriété `Type` de l'attribut la valeur `CurrencySource`.  
  
-   Un code ISO (International Standards Organization) de devise  
  
     Pour définir un attribut comme attribut de code ISO de devise, affectez la `Type` propriété de l’attribut à `CurrencyIsoCode`.  
  
 Pour plus d’informations sur les types d’attributs, consultez [Configurer des types d’attributs](attribute-properties-configure-attribute-types.md).  
  
## <a name="defining-account-intelligence-with-the-business-intelligence-wizard"></a>Définition de l'intelligence comptable avec l'Assistant Business Intelligence  
 Après avoir défini une dimension de comptes et ajouté la dimension à un cube, vous pouvez utiliser l'Assistant Business Intelligence pour ajouter des fonctions d'intelligence comptable, telles que l'identification et le mappage de types de comptes, à la dimension. Pour plus d’informations, consultez [Ajouter de l’intelligence comptable à une dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs et hiérarchies d’attributs](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [L’Assistant Business Intelligence F1](../business-intelligence-wizard-f1-help.md)   
 [Types de dimensions](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
