---
title: Définir un membre par défaut | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- default members
- attributes [Analysis Services], default members
- members [Analysis Services], default
- DefaultMember property
ms.assetid: db487856-ee21-49c3-aa08-d9136e193374
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3b89100b174df0d70306e42d3ae850cb3257ce52
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144179"
---
# <a name="define-a-default-member"></a>Définir un membre par défaut
  Le membre par défaut d'une hiérarchie d'attributs sert à évaluer les expressions lorsque la hiérarchie d'attributs n'est pas incluse dans une requête. Le membre par défaut est ignoré lorsqu'une requête inclut une hiérarchie d'attributs ou une hiérarchie d'utilisateurs contenant l'attribut qui source la hiérarchie d'attributs. Cela est dû au fait que le membre spécifié dans la requête est utilisé.  
  
 Le membre par défaut pour une hiérarchie d’attribut est défini en spécifiant un membre d’attribut en tant que le `DefaultMember` valeur de propriété pour la hiérarchie d’attribut. Vous pouvez définir cette propriété sous l’onglet Structure de dimension dans le Concepteur de dimensions ou dans le script de calcul du cube sous l’onglet Calcul du Concepteur de cube dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Vous pouvez également spécifier la propriété `DefaultMember` pour un rôle de sécurité (et remplacer le membre par défaut défini sur la dimension) sous l'onglet Données de la dimension lors de la définition de la sécurité de dimension. Pour éviter tout problème de résolution de noms, définissez le membre par défaut dans le script MDX du cube dans les situations suivantes : si le cube fait référence à une dimension de base de données à plusieurs reprises, si la dimension dans le cube a un nom différent de celle dans la base de données ou si vous souhaitez avoir différents membres par défaut dans différents cubes.  
  
 Le membre par défaut d'un attribut sert à évaluer des expressions lorsqu'un attribut n'est pas inclus dans une requête. Le membre par défaut pour un attribut est spécifié par le `DefaultMember` propriété sur l’attribut. Lorsqu'une hiérarchie de dimension est incluse dans une requête, tous les membres par défaut des attributs correspondant aux niveaux de la hiérarchie sont ignorés. Si aucune hiérarchie de dimension n'est incluse dans une requête, les membres par défaut sont utilisés pour tous les attributs de la dimension.  
  
## <a name="resolving-the-default-member-when-no-default-member-is-specified"></a>Résolution du membre par défaut lorsque aucun membre par défaut n'est spécifié  
 Si aucun membre par défaut n’est spécifié pour une hiérarchie d’attribut, et la hiérarchie d’attribut est agrégée (la `IsAggregatable` sur l’attribut est définie sur `True`), le membre (All) est le membre par défaut. Si aucun membre par défaut n’est spécifié et la hiérarchie d’attribut n’est pas agrégée (la `IsAggregatable` sur l’attribut est définie sur `False`), un membre par défaut est sélectionné à partir de niveau supérieur de la hiérarchie d’attribut.  
  
## <a name="specifying-the-default-member"></a>Spécification du membre par défaut  
 Chaque attribut dans une dimension dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a un membre par défaut, que vous pouvez spécifier à l’aide de la `DefaultMember` propriété pour un attribut. Ce paramètre est utilisé pour évaluer les expressions si un attribut est omis dans une requête. Si une requête spécifie une hiérarchie dans une dimension, les membres par défaut des attributs de cette hiérarchie sont ignorés. Si une requête ne spécifie pas une hiérarchie dans une dimension, le `DefaultMember` paramètres pour les attributs de dimension prennent effet.  
  
 Si le `DefaultMember` paramètre pour un attribut est vide et sa `IsAggregatable` est définie sur `True`, le membre par défaut est le membre tous. Si le `IsAggregatable` est définie sur `False`, le membre par défaut est le premier membre de premier niveau visible.  
  
 Le `DefaultMember` paramètre pour un attribut s’applique à toute hiérarchie à laquelle participe l’attribut. Vous ne pouvez pas utiliser des paramètres différents pour des hiérarchies différentes dans une dimension. Par exemple, si le membre [1998] est le membre par défaut d'un attribut [Année], ce paramètre s'applique à toute hiérarchie dans la dimension. Le `DefaultMember` dans ce cas ne peut pas être [1998] dans une hiérarchie et [1997] dans une autre hiérarchie.  
  
 Si vous définissez un membre par défaut pour un niveau particulier d'une hiérarchie qui ne s'agrège pas naturellement, vous devez définir des membres par défaut dans tous les niveaux au-dessus de ce niveau de la hiérarchie. Par exemple, dans la hiérarchie Pays–Climat, vous ne pouvez pas définir un membre par défaut pour Climat, sauf si vous définissez un membre par défaut pour Pays. La violation de cette règle provoque des erreurs lors du traitement des requêtes.  
  
 Lorsque les niveaux d'une hiérarchie s'agrègent naturellement, vous pouvez définir un membre par défaut pour un attribut de la hiérarchie sans tenir compte des autres attributs de cette hiérarchie. Par exemple, dans la hiérarchie Pays–Région–Ville, vous pouvez définir un membre par défaut pour Ville, par exemple [Ville].[Paris] sans définir le membre par défaut de Région ou de Pays.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer le &#40;tous les&#41; niveau pour les hiérarchies d’attributs](database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  