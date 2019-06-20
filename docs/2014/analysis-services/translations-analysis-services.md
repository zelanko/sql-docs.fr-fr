---
title: Traductions (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Business Intelligence Development Studio, translations [Analysis Services]
- translations [Analysis Services], about translations
- object translations [Analysis Services]
- language identifiers [Analysis Services]
- attribute translations [Analysis Services]
- translations [Analysis Services]
ms.assetid: 018471e0-3c82-49ec-aa16-467fb58a6d5f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e97c9ba15aab664e9f0c77f9eb84152f75c3e3d7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66065880"
---
# <a name="translations-analysis-services"></a>Traductions (Analysis Services)
  **[!INCLUDE[applies](../includes/applies-md.md)]**  Multidimensionnel uniquement  
  
 Dans un modèle de données multidimensionnel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , vous pouvez incorporer plusieurs traductions d'une légende pour fournir des chaînes spécifiques aux paramètres régionaux en fonction de l'identificateur LCID. Vous pouvez ajouter des traductions pour le nom de la base de données, les objets du cube et les objets de dimension de base de données.  
  
 La définition d'une traduction crée les métadonnées et la légende traduite à l'intérieur du modèle, mais pour restituer des chaînes localisées dans une application cliente, vous devez définir la propriété `Language` sur l'objet ou passer un paramètre `Locale Identifier` sur la chaîne de connexion (par exemple en définissant `LocaleIdentifier=1036` pour retourner des chaînes en français). Utilisez `Locale Identifier` si vous souhaitez prendre en charge plusieurs traductions simultanées du même objet dans différentes langues. Définir la propriété `Language` fonctionne, mais cela affecte aussi le traitement et les requêtes, ce qui pourrait avoir des conséquences inattendues. Définir `Locale Identifier` constitue le meilleur choix, car il est utilisé uniquement pour retourner des chaînes traduites.  
  
 Une traduction est composée d'un identificateur de paramètres régionaux (LCID), d'une légende traduite pour l'objet (par exemple le nom de la dimension ou de l'attribut) et éventuellement d'une liaison à une colonne qui fournit des valeurs de données dans la langue cible. Vous pouvez avoir plusieurs traductions, mais vous ne pouvez en utiliser qu'une seule pour une connexion donnée. Il n'existe aucune limite théorique quant au nombre de traductions que vous pouvez incorporer dans le modèle, mais chaque traduction ajoute une complexité au test et toutes les traductions doivent partager le même classement. Vous devez donc garder ces contraintes naturelles à l'esprit lors de la conception de votre solution.  
  
> [!TIP]  
>  Vous pouvez utiliser des applications clientes telles qu'Excel, Management Studio et [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] pour retourner des chaînes traduites. Pour plus d'informations, consultez [Globalization Tips and Best Practices &#40;Analysis Services&#41;](globalization-tips-and-best-practices-analysis-services.md) .  
  
## <a name="setting-up-a-model-to-support-translated-members"></a>Définition d'un modèle pour prendre en charge des membres traduits  
 Un modèle de données utilisé dans une solution multilingue nécessite davantage que des légendes traduites (noms de champs et descriptions). Il doit également fournir des valeurs de données exprimées dans différents scripts de langue. L'obtention d'une solution multilingue nécessite d'avoir des attributs individuels liés à des colonnes dans une base de données externe qui retournent les données.  
  
 L'exemple de base de données Adventure Works (multidimensionnelle, ainsi que l'entrepôt de données relationnelles) illustre la fonctionnalité de traduction. L'exemple de modèle comprend des légendes et des descriptions traduites. L'exemple d'entrepôt de données relationnelles contient des colonnes de valeurs traduites qui fournissent des membres d'attributs localisés dans le modèle.  
  
 Pour afficher les valeurs de données traduites accessibles au modèle  
  
1.  Ouvrez le modèle multidimensionnel Adventure Works dans le concepteur.  
  
2.  Dans l’Explorateur de solutions, ouvrez vues des sources de données et double-cliquez sur Adventure Works DW\<version > .dsv.  
  
3.  Recherchez dimDate, dimProduct, dimProductCategory ou dimProductSubcateogry. Toutes ces dimensions contiennent des attributs pour les membres traduits pour le mois, le jour de semaine, le nom de produit, le nom de catégorie, et ainsi de suite.  
  
4.  Cliquez avec le bouton droit sur un champ et sélectionnez **Explorer les données**. Vous verrez des traductions en anglais, espagnol et français de chaque membre.  
  
 Les formats de date, d'heure et de devise ne sont pas implémentés dans les traductions. Pour fournir de manière dynamique des formats spécifiques à une culture en fonction des paramètres régionaux du client, utilisez l'Assistant Conversion monétaire et la propriété `FormatString`. Pour plus d’informations, consultez [Conversions monétaires &#40;Analysis Services&#41;](currency-conversions-analysis-services.md) et [Élément FormatString &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/formatstring-element-assl).  
  
 [Leçon 9 : Définition de Perspectives et traductions](lesson-9-defining-perspectives-and-translations.md) dans le didacticiel Analysis Services vous guidera à travers les étapes de création et test des traductions.  
  
## <a name="defining-translations"></a>Définition des traductions  
 La définition d'une traduction crée un objet `Translation` comme enfant de l'objet de base de données, de dimension ou de cube [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Utilisez [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] pour ouvrir la solution et définir des traductions.  
  
### <a name="add-translations-to-a-cube"></a>Ajouter des traductions à un cube  
 Vous pouvez ajouter des traductions au cube, aux groupes de mesures, aux mesures, à la dimension de cube, aux perspectives, aux indicateurs de performance clés, aux actions, aux jeux nommés et aux membres calculés.  
  
1.  Dans l'Explorateur de solutions, double-cliquez sur le nom du cube pour ouvrir le Concepteur de cube.  
  
2.  Cliquez sur l'onglet **Traductions** . Tous les objets qui prennent en charge les traductions sont répertoriés dans cette page.  
  
3.  Pour chaque objet, spécifiez la langue cible (résolue en interne en un LCID), la légende traduite et la description traduite. La liste des langues est cohérente dans Analysis Services, que vous définissiez la langue du serveur dans Management Studio ou que vous ajoutiez une traduction de remplacement sur un attribut unique.  
  
     N'oubliez pas que vous ne pouvez pas modifier le classement. Un cube utilise essentiellement un seul classement, même si vous prenez en charge plusieurs langues via des légendes traduites (il existe une exception pour les attributs de dimension, décrite ci-dessous). Si les langues ne sont pas triées correctement sous le classement partagé, vous devez effectuer des copies du cube simplement pour répondre à vos spécifications de classement.  
  
4.  Générez et déployez le projet.  
  
5.  Connectez-vous à la base de données à l'aide d'une application cliente, comme Excel, en modifiant la chaîne de connexion pour utiliser l'identificateur de paramètres régionaux. Pour plus d’informations, consultez [Conseils et meilleures pratiques en matière de globalisation &#40;Analysis Services&#41;](globalization-tips-and-best-practices-analysis-services.md) .  
  
### <a name="add-translations-to-a-dimension-and-attributes"></a>Ajouter des traductions à une dimension et à des attributs  
 Vous pouvez ajouter des traductions à des dimensions de base de données, à des attributs, à des hiérarchies et à des niveaux au sein d'une hiérarchie.  
  
 Vous pouvez ajouter manuellement des légendes traduites au modèle à l'aide de votre clavier ou d'une opération copier-coller, mais pour les membres d'attributs de dimension, vous pouvez obtenir les valeurs traduites à partir d'une base de données externe. Plus précisément, la propriété `CaptionColumn` d'un attribut peut être liée à une colonne dans une vue de source de données.  
  
 Au niveau de l'attribut, vous pouvez remplacer les paramètres de classement. Par exemple, vous souhaiterez peut-être ajuster le respect de la largeur ou utiliser un tri binaire pour un attribut spécifique. Dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], le classement est exposé là où les liaisons de données sont définies. Étant donné que vous liez une traduction d'attribut de dimension à une colonne source différente dans la vue de source de données, un paramètre de classement est disponible pour que vous puissiez spécifier le classement utilisé par la colonne source. Pour plus d'informations sur le classement de colonne dans la base de données relationnelle, voir [Set or Change the Column Collation](../relational-databases/collations/set-or-change-the-column-collation.md) .  
  
1.  Dans l'Explorateur de solutions, double-cliquez sur le nom de la dimension pour ouvrir le Concepteur de dimensions.  
  
2.  Cliquez sur l'onglet **Traductions** . Tous les objets de dimension qui prennent en charge les traductions sont répertoriés dans cette page.  
  
     Pour chaque objet, spécifiez la langue cible (résolue en un LCID), la légende traduite et la description traduite. La liste des langues est cohérente dans Analysis Services, que vous définissiez la langue du serveur dans Management Studio ou que vous ajoutiez une traduction de remplacement sur un attribut unique.  
  
3.  Pour lier un attribut à une colonne fournissant des valeurs traduites  
  
    1.  Toujours dans le Concepteur de dimensions | **Traductions**, ajoutez une nouvelle traduction. Choisissez la langue. Une nouvelle colonne apparaît dans la page pour accepter les valeurs traduites.  
  
    2.  Placez le curseur dans une cellule vide adjacente à l'un des attributs. L'attribut ne peut pas être la clé, mais tous les autres attributs sont des options possibles. Vous devriez voir un petit bouton avec un point à l'intérieur. Cliquez sur le bouton pour ouvrir la boîte de dialogue **Traduction de données d'attribut**.  
  
    3.  Entrez une traduction de la légende. Elle sert d'étiquette de données dans le langage cible, par exemple comme nom de champ dans une liste de champs de tableau croisé dynamique.  
  
    4.  Choisissez la colonne source qui fournit les valeurs traduites des membres d'attribut. Seules les colonnes pré-existantes dans la table ou la requête liée à la dimension sont disponibles. Si la colonne n'existe pas, vous devez modifier la vue de source de données, la dimension et le cube pour sélectionner la colonne.  
  
    5.  Choisissez le classement et l'ordre de tri, le cas échéant.  
  
4.  Générez et déployez le projet.  
  
5.  Connectez-vous à la base de données à l'aide d'une application cliente, comme Excel, en modifiant la chaîne de connexion pour utiliser l'identificateur de paramètres régionaux. Pour plus d’informations, consultez [Conseils et meilleures pratiques en matière de globalisation &#40;Analysis Services&#41;](globalization-tips-and-best-practices-analysis-services.md).  
  
### <a name="add-a-translation-of-the-database-name"></a>Ajouter une traduction du nom de base de données  
 Au niveau de la base de données, vous pouvez ajouter des traductions pour le nom et la description de la base de données. Le nom traduit de la base de données peut être visible sur les connexions clientes qui spécifient le LCID de la langue, mais cela dépend de l'outil. Par exemple, l'affichage de la base de données dans Management Studio ne montre pas le nom traduit, même si vous spécifiez l'identificateur de paramètres régionaux sur la connexion. L'API utilisée par Management Studio pour se connecter à Analysis Services ne lit pas la propriété `Language`.  
  
1.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet | **Modifier la base de données** pour ouvrir le Concepteur de base de données.  
  
2.  Dans Traductions, spécifiez la langue cible (résolue en un LCID), la légende traduite et la description traduite. La liste des langues est cohérente dans Analysis Services, que vous définissiez la langue du serveur dans Management Studio ou que vous ajoutiez une traduction de remplacement sur un attribut unique.  
  
3.  Dans la page Propriétés de la base de données, affectez à la propriété `Language` le même LCID que celui que vous avez spécifié pour la traduction. Si vous le souhaitez, vous pouvez aussi définir la propriété `Collation` si la valeur par défaut n'est plus justifiée.  
  
4.  Générez et déployez la base de données.  
  
## <a name="resolving-translations"></a>Résolution des traductions  
 Si une application cliente demande un identificateur de paramètres régionaux, l'instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] tente de résoudre les données et les métadonnées des objets [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] au LCID correspondant le plus proche. Si l’application cliente ne spécifie pas de langue par défaut ou si elle spécifie l’identificateur local neutre (0) ou l’identificateur de langue de traitement par défaut (1024), alors [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilise la langue par défaut de l’instance pour renvoyer les données et les métadonnées des objets [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Scénarios de globalisation pour données multidimensionnelles Analysis Services](globalization-scenarios-for-analysis-services-multiidimensional.md)   
 [Langues et classements &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md)   
 [Définir ou modifier le classement des colonnes](../relational-databases/collations/set-or-change-the-column-collation.md)   
 [Conseils et meilleures pratiques en matière de globalisation &#40;Analysis Services&#41;](globalization-tips-and-best-practices-analysis-services.md)  
  
  
