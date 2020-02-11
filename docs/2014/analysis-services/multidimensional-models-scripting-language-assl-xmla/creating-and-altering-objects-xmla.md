---
title: Création et modification d’objets (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [XML for Analysis]
- subordinate objects [XML for Analysis]
- XML for Analysis, objects
- modifying objects
- removing objects
- deleting objects
- XMLA, objects
ms.assetid: a2080867-e130-440c-92eb-f768869f34a8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3dcc6eedc97b3d476d79420b4e067883e17f03d2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62702298"
---
# <a name="creating-and-altering-objects-xmla"></a>Création et modification d'objets (XMLA)
  Les objets principaux peuvent être créés, modifiés et supprimés de manière indépendante. Les objets principaux se composent notamment des objets suivants :  
  
-   Serveurs  
  
-   Bases de données  
  
-   Dimensions  
  
-   Cubes  
  
-   les groupes de mesures ;  
  
-   Partitions  
  
-   perspectives  
  
-   Modèles d'exploration de données  
  
-   Rôles  
  
-   Commandes associées à un serveur ou à une base de données  
  
-   Sources de données  
  
 Vous utilisez la [commande CREATE](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) pour créer un objet principal sur une instance [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]de, et la commande [ALTER](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) pour modifier un objet principal existant sur une instance. Les deux commandes sont exécutées à l’aide de la méthode [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) .  
  
## <a name="creating-objects"></a>Création d’objets  
 Lorsque vous créez des objets à l'aide de la méthode `Create`, vous devez tout d'abord identifier l'objet parent qui contient l'objet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à créer. Vous identifiez l’objet parent en fournissant une référence d’objet [](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) dans la propriété ParentObject `Create` de la commande. Chaque référence d'objet contient les identificateurs d'objet nécessaires pour identifier de manière unique l'objet parent pour la commande `Create`. Pour plus d’informations sur les références d’objets, consultez [définition et identification d’objets &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).  
  
 Par exemple, vous devez fournir une référence d'objet à un cube pour créer un groupe de mesures pour le cube. La référence d'objet pour le cube dans la propriété `ParentObject` contient à la fois un identificateur de base de données et un identificateur de cube, car le même identificateur de cube peut très bien être utilisé dans une autre base de données.  
  
 L’élément [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) contient des éléments ASSL (Analysis Services Scripting Language) qui définissent l’objet principal à créer. Pour plus d’informations sur ASSL, consultez [développement avec le langage de script Analysis Services &#40;&#41;ASSL ](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 Si vous définissez l'attribut `AllowOverwrite` de la commande `Create` à true, vous pouvez remplacer un objet principal existant associé à l'identificateur spécifié. Sinon, une erreur se produit si un objet principal associé à l'identificateur spécifié existe déjà dans l'objet parent.  
  
 Pour plus d’informations sur `Create` la commande, consultez [create Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla).  
  
### <a name="creating-session-objects"></a>Création d'objets de session  
 Les objets de session sont des objets temporaires disponibles uniquement pour la session explicite ou implicite utilisée par une application cliente et qui sont supprimés à la fin de la session. Vous pouvez créer des objets de session en `Scope` affectant à `Create` l’attribut de la commande la valeur *session*.  
  
> [!NOTE]  
>  Lors de l' ** utilisation du paramètre de `ObjectDefinition` session, l’élément peut contenir uniquement des éléments [dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)ou [MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL.  
  
## <a name="altering-objects"></a>Modification d'objets  
 Lorsque vous modifiez des objets à l' `Alter` aide de la méthode, vous devez d’abord identifier l’objet à modifier en fournissant une référence d’objet dans la `Alter` propriété d' [objet](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) de la commande. Chaque référence d'objet contient les identificateurs d'objet nécessaires pour identifier de manière unique l'objet pour la commande `Alter`. Pour plus d’informations sur les références d’objets, consultez [définition et identification d’objets &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).  
  
 Par exemple, vous devez fournir une référence d'objet à un cube pour modifier la structure de ce dernier. La référence d'objet pour le cube dans la propriété `Object` contient à la fois un identificateur de base de données et un identificateur de cube, car le même identificateur de cube peut très bien être utilisé dans une autre base de données.  
  
 L'élément `ObjectDefinition` contient des éléments ASSL qui définissent l'objet principal à modifier. Pour plus d’informations sur ASSL, consultez [développement avec le langage de script Analysis Services &#40;&#41;ASSL ](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 Si vous définissez l'attribut `AllowCreate` de la commande `Alter` à true, vous pouvez créer l'objet principal spécifié si l'objet n'existe pas. Sinon, une erreur se produit si un objet principal spécifié n'existe pas déjà.  
  
### <a name="using-the-objectexpansion-attribute"></a>Utilisation de l'attribut ObjectExpansion  
 Si vous modifiez uniquement les propriétés de l’objet principal et que vous ne redéfinissez pas les objets secondaires contenus dans l’objet principal, vous pouvez `ObjectExpansion` définir l’attribut `Alter` de la commande sur *ObjectProperties*. La propriété `ObjectDefinition` ne doit donc contenir que les éléments relatifs aux propriétés de l'objet principal, et la commande `Alter` laisse les objets secondaires associés à l'objet principal inchangés.  
  
 Pour redéfinir des objets mineurs pour un objet principal, vous devez `ObjectExpansion` affecter à l’attribut la valeur *ExpandFull* et la définition de l’objet doit inclure tous les objets secondaires contenus dans l’objet principal. Si la propriété `ObjectDefinition` de la commande `Alter` n'inclut pas explicitement un objet secondaire contenu dans l'objet principal, cet objet secondaire est supprimé.  
  
### <a name="altering-session-objects"></a>Modification d'objets de session  
 Pour modifier les objets de session créés `Create` par la commande, `Scope` affectez à `Alter` l’attribut de la commande la valeur *session*.  
  
> [!NOTE]  
>  Lors de l' ** utilisation du paramètre de `ObjectDefinition` session, l’élément peut contenir uniquement des éléments [dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)ou [MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL.  
  
## <a name="creating-or-altering-subordinate-objects"></a>Création ou modification d'objets subordonnés  
 Bien qu'une commande `Create` ou `Alter` ne crée ou ne modifie qu'un seul objet principal de niveau supérieur, l'objet principal ainsi créé ou modifié peut contenir des définitions dans la propriété `ObjectDefinition` englobante pour les autres objets principaux ou secondaires qui lui sont subordonnés. Par exemple, si vous définissez un cube, vous spécifiez la base de données parente dans `ParentObject`. Ensuite, dans la propriété de la définition du cube `ObjectDefinition`, vous pouvez définir des groupes de mesures pour le cube et, dans chaque groupe de mesures, vous pouvez définir des partitions. Un objet secondaire ne peut être défini que sous l'objet principal qui le contient. Pour plus d’informations sur les objets principaux et secondaires, consultez [objets de base de données &#40;Analysis Services-&#41;de données multidimensionnelles ](../multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="description"></a>Description  
 L’exemple suivant crée une source de données relationnelle qui fait [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] référence [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’exemple de base de données.  
  
### <a name="code"></a>Code  
  
```  
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    </ParentObject>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=localhost;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ImpersonationInfo>  
                <ImpersonationMode>ImpersonateServiceAccount</ImpersonationMode>  
            </ImpersonationInfo>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT0S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Create>  
```  
  
### <a name="description"></a>Description  
 L'exemple suivant modifie la source de données relationnelle créée dans l'exemple précédent pour définir le délai d'expiration de requête de la source de données à 30 secondes.  
  
### <a name="code"></a>Code  
  
```  
<Alter ObjectExpansion="ObjectProperties" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DataSourceID>AdventureWorksDW2012</DataSourceID>  
    </Object>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=fr-dwk-02;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT30S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Alter>  
```  
  
### <a name="comments"></a>Commentaires  
 L' `ObjectExpansion` attribut de la `Alter` commande a été défini sur *ObjectProperties*. Ce paramètre permet à l’élément [ImpersonationInfo](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl) , un objet mineur, d’être exclu de la source de données `ObjectDefinition`définie dans. Par conséquent, les informations d'emprunt d'identité de cette source de données restent définies sur le compte de service, comme spécifié dans le premier exemple.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode Execute &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)   
 [Développement avec le langage de script Analysis Services &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Développement avec XMLA dans Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
