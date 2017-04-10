---
title: "Cr&#233;er une dimension de type mon&#233;taire | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "dimensions [Analysis Services], devise"
  - "devise [Analysis Services]"
  - "conversion de devises"
  - "dimensions de devise [Analysis Services]"
ms.assetid: b1f037d1-ce47-4e47-a1c2-5ec9e781cff6
caps.latest.revision: 16
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Cr&#233;er une dimension de type mon&#233;taire
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], une dimension de type monétaire est une dimension dont les attributs représentent une liste de devises utilisée dans les rapports financiers.  
  
 Une dimension monétaire permet d'ajouter des fonctions de conversion monétaire à un cube dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Pour ajouter une conversion monétaire à un cube, utilisez l'Assistant Business Intelligence pour définir une commande de script MDX (Multidimensional Expressions) qui convertit les mesures monétaires en valeurs correspondant aux paramètres régionaux de l'application cliente. Pour créer ce script MDX, vous devez fournir les informations suivantes à l'Assistant Business Intelligence :  
  
-   Une dimension monétaire qui représente les devises sources. (Cette dimension est la dimension monétaire source.)  
  
-   Un groupe de mesures qui représente les taux de change à utiliser.  
  
 À partir de ces informations, l'Assistant Business Intelligence crée un processus de conversion monétaire qui identifie la dimension monétaire de destination appropriée (la dimension monétaire qui représente les devises de destination). Selon le nombre de conversions monétaires nécessaires à la solution décisionnelle, l'Assistant Business Intelligence peut définir plusieurs dimensions monétaires de destination. Pour plus d’informations sur la définition de conversions monétaires, consultez [Conversions monétaires &#40;Analysis Services&#41;](../../analysis-services/currency-conversions-analysis-services.md).  
  
 Pour définir une dimension comme dimension monétaire, affectez la valeur **Devise** à la propriété **Type** de la dimension.  
  
## Structure de la dimension  
 Une dimension monétaire contient au moins un attribut clé qui identifie les devises dans la table de la dimension monétaire. La valeur de l'attribut clé est différente dans les dimensions monétaires source et de destination :  
  
-   Pour définir un attribut comme attribut clé d’une dimension monétaire source, affectez la valeur **CurrencySource** à la propriété **Type** de l’attribut.  
  
-   Pour définir un attribut comme attribut clé d’une dimension monétaire de destination, affectez la valeur **CurrencyDestination** à la propriété **Type** de l’attribut.  
  
 Pour les rapports, les dimensions monétaires source et de destination peuvent contenir éventuellement les attributs suivants :  
  
-   Un attribut de nom de devise  
  
     Pour définir un attribut comme attribut de nom de devise, affectez la valeur **CurrencyName** à la propriété **Type** de l’attribut.  
  
-   Un attribut de source de devise  
  
     Pour définir un attribut comme attribut de source de devise, affectez la valeur **CurrencySource** à la propriété **Type** de l’attribut.  
  
-   Un code ISO (International Standards Organization) de devise  
  
     Pour définir un attribut comme attribut de code ISO de devise, affectez la valeur **CurrencyIsoCode** à la propriété **Type** de l’attribut.  
  
 Pour plus d’informations sur les types d’attributs, consultez [Configurer des types d’attributs](../../analysis-services/multidimensional-models/configure-attribute-types.md).  
  
## Définition de l'intelligence comptable avec l'Assistant Business Intelligence  
 Après avoir défini une dimension de comptes et ajouté la dimension à un cube, vous pouvez utiliser l'Assistant Business Intelligence pour ajouter des fonctions d'intelligence comptable, telles que l'identification et le mappage de types de comptes, à la dimension. Pour plus d’informations, consultez [Ajouter de l’intelligence comptable à une dimension](../../analysis-services/multidimensional-models/add-account-intelligence-to-a-dimension.md).  
  
## Voir aussi  
 [Attributs et hiérarchies d'attributs](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Aide (F1) de l'Assistant Business Intelligence](../Topic/Business%20Intelligence%20Wizard%20F1%20Help.md)   
 [Types de dimensions](../Topic/Dimension%20Types.md)  
  
  