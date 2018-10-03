---
title: Groupes de mesures liés | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- linked measure groups [Analysis Services]
- referencing measure groups
- Linked Measure Group Wizard
- measure groups [Analysis Services], linked
- linked dimensions [Analysis Services]
ms.assetid: 7f838452-8669-4194-8e15-7afdc7f15251
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a1377552b3e50fe5c536ae0d7d854346ccb062d1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140349"
---
# <a name="linked-measure-groups"></a>Groupes de mesures liés
  Un groupe de mesures lié est basé sur un autre groupe de mesures situé dans un autre cube de la même base de données ou d'une autre base de données Analysis Services. Utilisez un groupe de mesures lié si vous voulez réutiliser un jeu de mesures, et les valeurs de données correspondantes, dans plusieurs cubes.  
  
 Microsoft recommande que les groupes de mesures liés et d'origine se trouvent dans des solutions exécutées sur le même serveur. Liaison à un groupe de mesures sur un serveur distant sera déconseillée dans une version ultérieure (voir [Analysis Services déconseillées dans SQL Server 2014](../deprecated-analysis-services-features-in-sql-server-2014.md)).  
  
> [!IMPORTANT]  
>  Les groupes de mesures liés sont en lecture seule. Pour récupérer les dernières modifications, vous devez supprimer et recréer tous les groupes de mesures liés en fonction de l'objet source modifié. Pour cette raison, groupes de mesures et la zone de collage entre les projets est une approche lieu que vous devez comme au cas où futures de modifications au groupe de mesures seront requises.  
  
## <a name="usage-limitations"></a>Limites d'utilisation  
 Comme indiqué précédemment, une contrainte importante de l'utilisation des mesures liées est l'impossibilité de personnaliser une mesure directement liée. Les modifications apportées au type de données, au format, à la liaison de données et à la visibilité, ainsi que l'appartenance des éléments au groupe de mesures lui-même, sont autant de modifications qui doivent être effectuées dans le groupe de mesures d'origine.  
  
 D'un point de vue opérationnel, les groupes de mesures liés sont identiques aux autres groupes de mesures lorsque des applications clientes y accèdent et ils sont interrogés de la même façon que les autres groupes de mesures.  
  
 Lorsqu'un cube contenant un groupe de mesures lié est interrogé, la liaison est établie et résolue durant le premier test de calcul du cube de destination. En raison de ce comportement, tous les calculs stockés dans le groupe de mesures lié ne sont pas résolus tant que la requête n'est pas évaluée. Autrement dit, les mesures calculées et les cellules calculées ne sont pas héritées du cube source et doivent être recréées dans le cube de destination.  
  
 La liste suivante résume les restrictions d'utilisation.  
  
-   Vous ne pouvez pas créer un groupe de mesures lié à partir d'un autre groupe de mesures lié.  
  
-   Vous ne pouvez pas ajouter ou supprimer des mesures dans un groupe de mesures lié. L'appartenance est définie uniquement dans le groupe de mesures d'origine.  
  
-   Les groupes de mesures liés ne prennent pas en charge l'écriture différée.  
  
-   Les groupes de mesures liés ne peuvent pas être utilisés dans des relations plusieurs-à-plusieurs, en particulier lorsque ces relations sont dans des cubes différents. Cela peut entraîner des agrégations ambiguës. Pour plus d’informations, consultez [Quantités incorrectes de mesures liées dans les cubes contenant des relations plusieurs-à-plusieurs](http://social.technet.microsoft.com/wiki/contents/articles/22911.incorrect-amounts-for-linked-measures-in-cubes-containing-many-to-many-relationships-ssas-troubleshooting.aspx).  
  
 Les mesures contenues dans un groupe de mesures lié ne s’organisent directement que conjointement à des dimensions liées extraites de la même base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Toutefois, vous pouvez utiliser les membres calculés pour associer les informations de groupes de mesures liés aux autres dimensions non liées de votre cube. Vous pouvez également utiliser une relation indirecte, telle qu'une référence ou une relation plusieurs-à-plusieurs, pour lier des dimensions non liées à un groupe de mesures lié.  
  
## <a name="create-or-modify-a-linked-measure"></a>Créer ou modifier une mesure liée  
 Utilisez [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] pour créer un groupe de mesures lié.  
  
1.  Finalisez toutes les modifications apportées au groupe de mesures d'origine dans le cube source, afin de ne pas avoir à recréer les groupes de mesures liés ultérieurement dans les cubes suivants. Vous pouvez renommer un objet lié, mais vous ne pouvez pas modifier les autres propriétés.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le cube auquel vous ajoutez le groupe de mesures lié. Le cube s'ouvre dans le Concepteur de cube.  
  
3.  Dans le Concepteur de cube, dans le volet Mesures ou Dimensions, cliquez avec le bouton droit n’importe où dans le volet, puis sélectionnez **Nouvel objet lié**. L'Assistant Objet lié démarre.  
  
4.  Dans la première page, spécifiez la source de données. Cette étape détermine l'emplacement du groupe de mesures d'origine. La valeur par défaut est le cube actuel dans la base de données active, mais vous pouvez choisir une autre base de données Analysis Services.  
  
5.  Dans la page suivante, choisissez le groupe de mesures ou la dimension que vous souhaitez lier. Les objets de dimensions et de cube, tels que les groupes de mesures, sont répertoriés séparément. Seuls les objets qui sont absents du cube actuel sont disponibles.  
  
6.  Cliquez sur **Terminer** pour créer l’objet lié. Les objets liés apparaissent dans le volet Mesures et Dimensions, signalés par l'icône de lien.  
  
## <a name="secure-a-linked-measure"></a>Sécuriser une mesure liée  
 Une fois le lien défini, l'accès aux mesures d'un groupe de mesures lié est géré de la même façon que l'accès aux autres groupes de mesures. Un objet lié apparaît à côté de ses homologues non liés dans le Concepteur de rôle. Pour plus d’informations sur la gestion de la sécurité d’un groupe de mesures, consultez [Octroyer des autorisations de cube ou de modèle &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md).  
  
 Pour définir ou utiliser un groupe de mesures lié, les Windows compte de service pour le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance doit appartenir à un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] rôle de base de données a `ReadDefinition` et `Read` droits sur la source d’accès [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] l’instance à la source du cube et mesure au groupe, ou doit appartenir à la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] rôle Administrateurs pour la source de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir des dimensions liées](define-linked-dimensions.md)  
  
  
