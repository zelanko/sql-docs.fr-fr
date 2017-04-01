---
title: "Source XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.xmlsource.f1"
helpviewer_keywords: 
  - "sources [Integration Services], XML"
  - "source XML [Integration Services]"
  - "Éditeur de source XML"
ms.assetid: 68c27ea5-e93d-4e26-bfb2-d967ca0a5282
caps.latest.revision: 47
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 47
---
# Source XML
  La source XML lit un fichier de données XML et remplit les colonnes de la sortie source avec les données.  
  
 Les données des fichiers XML sont fréquemment organisées de façon hiérarchique. Par exemple, un fichier de données XML peut représenter des catalogues et des éléments dans des catalogues. Avant que les données puissent entrer dans le flux de données, la relation des éléments du fichier de données XML doit être déterminée et une sortie doit être générée pour chaque élément du fichier.  
  
## <a name="schemas"></a>Schémas  
 La source XML utilise un schéma pour interpréter les données XML. La source XML prend en charge l'utilisation d'un fichier XSD (XML Schema Definition) ou de schémas inclus pour convertir les données XML dans un format tabulaire. Si vous configurez la source XML à l’aide de la boîte de dialogue **Éditeur de source XML** , l’interface utilisateur peut générer un fichier XSD à partir du fichier de données XML spécifié.  
  
> [!NOTE]  
>  Les DTD ne sont pas pris en charge.  
  
 Les schémas ne peuvent prendre en charge qu'un seul espace de noms ; ils ne prennent pas en charge les collections de schémas.  
  
> [!NOTE]  
>  La source XML ne valide pas les données du fichier XML par rapport au fichier XSD.  
  
## <a name="xml-source-editor"></a>Éditeur de source XML  
 Les données des fichiers XML sont fréquemment organisées de façon hiérarchique. La boîte de dialogue **Éditeur de source XML** utilise le schéma spécifié pour générer les sorties de la source XML. Vous pouvez spécifier un fichier XSD, utiliser un schéma inclus ou générer un fichier XSD à partir du fichier de données XML spécifié. Le schéma doit être disponible au moment de la conception.  
  
 La source XML génère des structures tabulaires à partir des données XML en créant une sortie pour chaque élément contenant d'autres éléments dans les fichiers XML. Par exemple, si les données XML représentent des catalogues et des éléments dans des catalogues, la source XML crée une sortie pour les catalogues et une sortie pour chaque type d'élément contenu dans ces catalogues. La sortie de chaque élément contient des colonnes de sortie pour les attributs de cet élément.  
  
 Pour fournir des informations sur les relations hiérarchiques des données dans les sorties, la source XML ajoute dans celles-ci une colonne qui identifie l'élément parent de chaque élément enfant. Dans l'exemple des catalogues contenant différents types d'éléments, à chaque élément correspond une valeur de colonne qui identifie le catalogue auquel il appartient.  
  
 La source XML crée une sortie pour chaque élément, mais vous n'êtes pas obligé d'utiliser toutes les sorties. Vous pouvez supprimer toute sortie que vous ne souhaitez pas utiliser ou simplement ne pas la connecter à un composant en aval.  
  
 La source XML génère également les noms de sortie, afin que ceux-ci ne soient pas ambigus. Ces noms peuvent être longs et ne pas identifier les sorties de façon très utilisable pour vous. Vous pouvez renommer les sorties, sous réserve que leurs noms demeurent uniques. Vous pouvez également modifier le type de données et la longueur des colonnes de sortie.  
  
 Pour chaque sortie, la source XML ajoute une sortie d'erreur. Par défaut, les colonnes situées dans les sorties d'erreur ont le type de données chaîne Unicode (DT_WSTR) et une longueur de 255 caractères ; toutefois, vous pouvez reconfigurer leur type de données et leur longueur.  
  
 Si le fichier de données XML contient des éléments qui ne figurent pas dans le fichier XSD, ces éléments sont ignorés et aucune sortie correspondante n'est générée. Par contre, s'il manque dans le fichier de données XML des éléments représentés dans le fichier XSD, la sortie contient des colonnes comportant des valeurs NULL.  
  
 Quand les données sont extraites du fichier de données XML, elles sont converties en un type de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Toutefois, la source XML ne peut pas convertir les données XML en types de données DT_TIME2 ou DT_DBTIMESTAMP2, car elle ne prend pas en charge ces types de données. Pour plus d’informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Le fichier XSD ou le schéma inclus peuvent spécifier le type de données des éléments mais, s’ils ne le font pas, la boîte de dialogue **Éditeur de source XML** affecte le type de données chaîne Unicode (DT_WSTR) à la colonne de sortie qui contient l’élément et définit pour celle-ci une longueur de 255 caractères.  
  
 Si le schéma spécifie la longueur maximale d'un élément, la longueur de la colonne de sortie prend cette valeur. Si la longueur maximale est supérieure à la longueur prise en charge par le type de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans lequel l’élément est converti, les données sont tronquées à la longueur maximale du type de données. Par exemple, si une chaîne a une longueur de 5000, elle est tronquée au 4000e caractère car la longueur maximale du type de données DT_WSTR est de 4000 caractères ; de même, les données de type octet sont tronquées au 8000e caractère, car la longueur maximale du type de données DT_BYTES est de 4000 caractères. Si le schéma ne spécifie aucune longueur maximale, la longueur par défaut des colonnes, indépendamment de leur type de données, est de 255. La troncation des données dans la source XML est gérée de la même manière que dans les autres composants de flux de données. Pour plus d’informations, consultez [Gestion des erreurs dans les données](../../integration-services/data-flow/error-handling-in-data.md).  
  
 Vous pouvez modifier le type de données et la longueur de la colonne. Pour plus d’informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="configuration-of-the-xml-source"></a>Configuration de la source XML  
 La source XML prend en charge trois modes différents d'accès aux données. Vous pouvez spécifier l'emplacement du fichier de données XML, la variable qui contient cet emplacement ou celle qui contient les données XML.  
  
 La source XML inclut les propriétés personnalisées **XMLData** et **XMLSchemaDefinition**, qui peuvent être mises à jour par des expressions de propriété lors du chargement du package. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41;](../../integration-services/expressions/integration-services-ssis-expressions.md), [Expressions de propriété dans des packages](../../integration-services/expressions/use-property-expressions-in-packages.md) et [Propriétés personnalisées des sources XML](../../integration-services/data-flow/xml-source-custom-properties.md).  
  
 La source XML prend en charge plusieurs sorties standard et plusieurs sorties d'erreur.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] inclut la boîte de dialogue **Éditeur de source XML** pour configurer la source XML. Cette boîte de dialogue est disponible dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de source XML** , cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur de source XML &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/xml-source-editor-connection-manager-page.md)  
  
-   [Éditeur de source XML &#40;page Colonnes&#41;](../../integration-services/data-flow/xml-source-editor-columns-page.md)  
  
-   [Éditeur de source XML &#40;page Sortie d’erreur&#41;](../../integration-services/data-flow/xml-source-editor-error-output-page.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../Topic/Common%20Properties.md)  
  
-   [Propriétés personnalisées des sources XML](../../integration-services/data-flow/xml-source-custom-properties.md)  
  
 Pour plus d’informations sur la définition des propriétés, cliquez sur l’une des rubriques suivantes :  
  
-   [Définir les propriétés d’un composant de flux de données](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a>Tâches associées  
 [Extraire des données à l’aide de la source XML](../../integration-services/data-flow/extract-data-by-using-the-xml-source.md)  
