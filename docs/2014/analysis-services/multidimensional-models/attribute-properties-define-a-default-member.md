---
title: Définir un membre par défaut | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- default members
- attributes [Analysis Services], default members
- members [Analysis Services], default
- DefaultMember property
ms.assetid: db487856-ee21-49c3-aa08-d9136e193374
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 959645223eacec6c000ddbfa23615b7949d10d5a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66077417"
---
# <a name="define-a-default-member"></a>Définir un membre par défaut
  Le membre par défaut d'une hiérarchie d'attributs sert à évaluer les expressions lorsque la hiérarchie d'attributs n'est pas incluse dans une requête. Le membre par défaut est ignoré lorsqu'une requête inclut une hiérarchie d'attributs ou une hiérarchie d'utilisateurs contenant l'attribut qui source la hiérarchie d'attributs. Cela est dû au fait que le membre spécifié dans la requête est utilisé.  
  
 Le membre par défaut d'une hiérarchie d'attributs est défini en spécifiant un membre d'attribut en tant que valeur de propriété `DefaultMember` pour la hiérarchie d'attributs. Vous pouvez définir cette propriété sous l’onglet Structure de dimension dans le Concepteur de dimensions ou dans le script de calcul du cube sous l’onglet Calcul du Concepteur de cube dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Vous pouvez également spécifier la propriété `DefaultMember` pour un rôle de sécurité (et remplacer le membre par défaut défini sur la dimension) sous l'onglet Données de la dimension lors de la définition de la sécurité de dimension. Pour éviter tout problème de résolution de noms, définissez le membre par défaut dans le script MDX du cube dans les situations suivantes : si le cube fait référence à une dimension de base de données à plusieurs reprises, si la dimension dans le cube a un nom différent de celle dans la base de données ou si vous souhaitez avoir différents membres par défaut dans différents cubes.  
  
 Le membre par défaut d'un attribut sert à évaluer des expressions lorsqu'un attribut n'est pas inclus dans une requête. Le membre par défaut d'un attribut est spécifié par la propriété `DefaultMember` de l'attribut. Lorsqu'une hiérarchie de dimension est incluse dans une requête, tous les membres par défaut des attributs correspondant aux niveaux de la hiérarchie sont ignorés. Si aucune hiérarchie de dimension n'est incluse dans une requête, les membres par défaut sont utilisés pour tous les attributs de la dimension.  
  
## <a name="resolving-the-default-member-when-no-default-member-is-specified"></a>Résolution du membre par défaut lorsque aucun membre par défaut n'est spécifié  
 Si aucun membre par défaut n'est spécifié pour une hiérarchie d'attributs et que celle-ci peut être agrégée (la propriété `IsAggregatable` de l'attribut a la valeur `True`), le membre (All) est le membre par défaut. Si aucun membre par défaut n'est spécifié et que la hiérarchie d'attributs ne peut pas être agrégée (la propriété `IsAggregatable` de l'attribut a la valeur `False`), un membre par défaut est sélectionné à partir du niveau supérieur de la hiérarchie d'attributs.  
  
## <a name="specifying-the-default-member"></a>Spécification du membre par défaut  
 Chaque attribut d’une dimension dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a un membre par défaut, que vous pouvez spécifier à l' `DefaultMember` aide de la propriété d’un attribut. Ce paramètre est utilisé pour évaluer les expressions si un attribut est omis dans une requête. Si une requête spécifie une hiérarchie dans une dimension, les membres par défaut des attributs de cette hiérarchie sont ignorés. Si une requête ne spécifie pas de hiérarchie dans une dimension, `DefaultMember` les paramètres des attributs de dimension prennent effet.  
  
 Si le `DefaultMember` paramètre d’un attribut est vide et que `IsAggregatable` sa propriété a la `True`valeur, le membre par défaut est le membre tous. Si la `IsAggregatable` propriété a la valeur `False`, le membre par défaut est le premier membre du premier niveau visible.  
  
 Le `DefaultMember` paramètre d’un attribut s’applique à chaque hiérarchie dans laquelle l’attribut participe. Vous ne pouvez pas utiliser des paramètres différents pour des hiérarchies différentes dans une dimension. Par exemple, si le membre [1998] est le membre par défaut d'un attribut [Année], ce paramètre s'applique à toute hiérarchie dans la dimension. Dans `DefaultMember` ce cas, le paramètre ne peut pas être [1998] dans une hiérarchie et [1997] dans une autre hiérarchie.  
  
 Si vous définissez un membre par défaut pour un niveau particulier d'une hiérarchie qui ne s'agrège pas naturellement, vous devez définir des membres par défaut dans tous les niveaux au-dessus de ce niveau de la hiérarchie. Par exemple, dans la hiérarchie All-pays-climat, vous ne pouvez pas définir un membre par défaut pour climat, sauf si vous définissez un membre par défaut pour les pays. La violation de cette règle provoque des erreurs lors du traitement des requêtes.  
  
 Lorsque les niveaux d'une hiérarchie s'agrègent naturellement, vous pouvez définir un membre par défaut pour un attribut de la hiérarchie sans tenir compte des autres attributs de cette hiérarchie. Par exemple, dans la hiérarchie pays-province-ville, vous pouvez définir un membre par défaut pour City, par exemple [City]. [Montréal] sans définir le membre par défaut pour l’État ou le pays.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer le niveau &#40;Tous&#41; des hiérarchies d’attributs](database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
