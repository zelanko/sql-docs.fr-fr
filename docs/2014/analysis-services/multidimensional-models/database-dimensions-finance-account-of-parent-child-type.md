---
title: Créer un compte finance de dimension de type parent-enfant | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], account
- account dimensions [Analysis Services]
- adding account intelligence
- account intelligence [Analysis Services]
ms.assetid: 2ba74e81-5b4b-407e-acdf-deb2f6accf0a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2ad3c9733003a22b2d75b483e792e097ae229233
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547131"
---
# <a name="create-a-finance-account-of-parent-child-type-dimension"></a>Créer un compte Finance de la dimension de type parent-enfant
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , une dimension de type compte est une dimension dont les attributs représentent un graphique de comptes à des fins de création de rapports financiers.  
  
 Une dimension de comptes permet de gérer dans le temps et de manière sélective le comportement de l'agrégation dans les comptes. Un compte de dimensions permet également d'utiliser un mécanisme standard pour résoudre la plupart des problèmes d'agrégation non standard associés généralement aux solutions décisionnelles qui gèrent des données financières. Si vous ne disposiez pas d'un tel mécanisme standard, la résolution des problèmes d'agrégation non standard nécessiterait des formules de cumul personnalisées, des membres calculés ou des scripts d'expression multidimensionnelle (MDX, Multidimensional Expressions).  
  
 Pour définir une dimension sous la forme d'une dimension de comptes, affectez à la propriété `Type` de la dimension la valeur `Accounts`.  
  
## <a name="dimension-structure"></a>Structure de la dimension  
 Une dimension de comptes contient au moins deux attributs :  
  
-   Attribut clé : attribut qui identifie les comptes individuels dans la table de dimension pour la dimension de compte.  
  
-   Attribut de compte : attribut parent qui décrit la façon dont les comptes sont organisés hiérarchiquement dans la dimension Account.  
  
     Pour définir un attribut comme attribut de compte, affectez à la propriété `Type` de l'attribut la valeur `Account` et à la propriété `Usage`, la valeur `Parent`.  
  
 Les dimensions de comptes peuvent éventuellement contenir les attributs suivants :  
  
-   Attribut de type de compte : attribut qui définit le type de compte pour chaque compte de la dimension. Les noms des membres de l’attribut de type de compte sont associés aux types de comptes définis pour la base de données ou le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , et indiquent la fonction d’agrégation utilisée par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour ces comptes. Vous pouvez également utiliser des opérateurs unaires ou des formules de cumul personnalisées pour déterminer le comportement d'agrégation des attributs de comptes, mais les types de comptes permettent d'appliquer aisément un comportement cohérent à un graphique de comptes sans avoir à modifier la base de données relationnelle sous-jacente.  
  
     Pour définir un attribut de type de compte, affectez à la propriété `Type` de l'attribut la valeur `AccountType`.  
  
-   Attribut de nom de compte : attribut utilisé à des fins de création de rapports. Pour définir un attribut de nom de compte, affectez à la propriété `Type` de l'attribut la valeur `AccountName`.  
  
-   Attribut de numéro de compte : attribut utilisé à des fins de création de rapports. Pour définir un attribut de numéro de compte, affectez à la propriété `Type` de l'attribut la valeur `AccountNumber`.  
  
 Pour plus d’informations sur les types d’attributs, consultez [Configurer des types d’attributs](attribute-properties-configure-attribute-types.md).  
  
## <a name="adding-account-intelligence-with-the-business-intelligence-wizard"></a>Ajout de l'intelligence comptable avec l'Assistant Business Intelligence  
 Après avoir défini une dimension de comptes et ajouté la dimension à un cube, vous pouvez utiliser l’Assistant Business Intelligence pour ajouter des fonctions d’intelligence comptable, telles que l’identification et le mappage de types de comptes, à la dimension. Pour plus d’informations, consultez [Ajouter de l’intelligence comptable à une dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs et hiérarchies d’attributs](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Aide (F1) de l’Assistant Business Intelligence](../business-intelligence-wizard-f1-help.md)   
 [Types de dimensions](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
