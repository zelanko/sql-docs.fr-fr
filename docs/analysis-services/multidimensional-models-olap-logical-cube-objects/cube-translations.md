---
title: Traductions de cube | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
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
helpviewer_keywords:
- multiple language support [Analysis Services]
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- cubes [Analysis Services], translations
- OLAP objects [Analysis Services], translations
- translations [Analysis Services], cubes
ms.assetid: 4e4fd6a4-d324-4508-b75a-2a57de9ab8ff
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ecd500f3b661f6f6d59746c907ed60a5a31ff495
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="cube-translations"></a>Traductions de cube
  Une traduction est un mécanisme simple permettant de modifier les étiquettes et les légendes affichées d'une langue à une autre. Chaque traduction est définie comme une paire de valeurs : une chaîne avec le texte traduit et un nombre avec l'ID de langue. Les traductions sont disponibles pour tous les objets dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les valeurs d'attribut peuvent également être traduites pour les dimensions. L'application cliente est chargée de rechercher le paramètre de langue que l'utilisateur a défini et bascule pour afficher toutes les légendes et les étiquettes dans cette langue. Un objet peut avoir autant de traductions que vous le souhaitez.  
  
 Un objet <xref:Microsoft.AnalysisServices.Translation> simple est composé d'un numéro d'ID de langue et de la légende traduite. Le numéro d’ID de langue est une **entier** avec l’ID de langue. La légende traduite est le texte traduit.  
  
 Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], une traduction de cube est une représentation spécifique à la langue du nom d’un objet de cube, par exemple une légende ou un dossier d’affichage. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend également en charge les traductions des noms de dimension et de membre.  
  
 Les traductions permettent au serveur de prendre en charge les applications clientes qui autorisent l'emploi de plusieurs langues. Il arrive fréquemment que les données de cube soient visualisées par des utilisateurs de différents pays. Il est utile de pouvoir traduire différents éléments d'un cube dans une autre langue pour que ces utilisateurs puissent afficher et comprendre les métadonnées du cube. Par exemple, un utilisateur situé en France peut accéder à un cube à partir d'une station de travail utilisant des paramètres régionaux français, il peut voir les valeurs des propriétés des objets en français. De la même façon, un utilisateur d'une entreprise en Allemagne qui accède au même cube depuis une station de travail utilisant les paramètres régionaux allemands peut voir les valeurs des propriétés des objets en allemand.  
  
 Les informations de classement et de langue pour l'ordinateur client sont stockées sous la forme d'un identificateur local (LCID). Lors de la connexion, le client envoie cet identificateur à l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. L'instance utilise l'identificateur pour déterminer l'ensemble de traductions à utiliser lors de la fourniture des métadonnées des objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à chaque utilisateur professionnel. Si un objet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne contient pas la traduction spécifiée, la langue par défaut est utilisée pour retourner le contenu au client.  
  
## <a name="see-also"></a>Voir aussi  
 [Traductions de dimension](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [Prise en charge de la traduction dans Analysis Services](../../analysis-services/translation-support-in-analysis-services.md)   
 [Globalisation conseils et meilleures pratiques &#40; Analysis Services &#41;](../../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  

