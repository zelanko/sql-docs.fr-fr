---
title: 'À l’aide de le : Identity des Annotations et | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:guid
- annotated XSD schemas, IDENTITY-type columns
- annotated XSD schemas, GUID values
- DiffGrams [SQLXML], annotations
- identity annotation
- XSD schemas [SQLXML], GUID values
- GUIDs [SQLXML]
- guid annotation
- sql:identity
- IDENTITY-type column
- XSD schemas [SQLXML], IDENTITY-type columns
- updategrams [SQLXML], GUID values
ms.assetid: 7661dfd0-6573-4692-a8f1-3597adcd33c4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c6135f1b46e9b2312f01b9ff7a7ebdd08d2d34a8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66013640"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a>Utilisation des annotations sql:identity et sql:guid
  Vous pouvez spécifier le `sql:identity` et `sql:guid` annotations dans un schéma XSD pour n’importe quel nœud qui mappe à une colonne de base de données dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le format de code de mise à jour (updategram) prend en charge les attributs `updg:at-identity` et `updg:guid`, contrairement au format de DiffGram. L'attribut `updg:at-identity` définit le comportement de mise à jour d'une colonne de type IDENTITY. L'attribut `updg:guid` permet d'obtenir une valeur GUID à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et de l'utiliser dans le code de mise à jour (updategram). Pour plus d’informations et pour obtenir des exemples fonctionnels, consultez [insertion de données à l’aide de programmes &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
 Les annotations `sql:identity` et `sql:guid` étendent ces fonctionnalités aux DiffGrams.  
  
 Lorsque vous exécutez un DiffGram, il est d'abord converti en un code de mise à jour (updategram), puis le code de mise à jour (updategram) est exécuté. En spécifiant les annotations `sql:identity` et `sql:guid` dans le schéma XSD, vous définissez en fait le comportement d'un code de mise à jour (updategram). Par conséquent, toutes les annotations sont décrites dans le contexte d'un code de mise à jour (updategram). Les annotations peuvent être utilisées à la fois pour les DiffGrams et les codes de mise à jour (updategram) ; toutefois, les codes de mise à jour (updategram) offrent déjà un moyen plus puissant pour gérer l'identité et les valeurs GUID.  
  
 Les annotations `sql:identity` et `sql:guid` peuvent être définies sur un élément de contenu complexe.  
  
## <a name="sqlidentity-annotation"></a>Annotation sql:identity  
 Vous pouvez spécifier l'annotation `sql:identity` dans le schéma XSD de n'importe quel nœud mappé sur une colonne de base de données de type IDENTITY. La valeur spécifiée pour cette annotation définit comment la mise à jour de la colonne de type d’identité (à l’aide de la valeur fournie dans la mise à jour pour modifier la colonne ou en ignorant la valeur, auquel cas un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-valeur générée est utilisée pour cette colonne).  
  
 Deux valeurs peuvent être assignées à l'annotation `sql:identity` :  
  
 ignore  
 Ordonne au code de mise à jour (updategram) d'ignorer toute valeur fournie dans le code de mise à jour (updategram) pour cette colonne et de compter sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour générer la valeur d'identité.  
  
 useValue  
 Ordonne au code de mise à jour (updategram) d'utiliser la valeur fournie dans le code de mise à jour (updategram) pour mettre à jour la colonne de type IDENTITY. Un code de mise à jour (updategram) ne vérifie pas si la colonne est une valeur d'identité ou pas.  
  
 Si le code de mise à jour (updategram) spécifie une valeur pour la colonne de type IDENTITY, l'annotation `sql:identity="useValue"` doit être spécifiée dans le schéma.  
  
## <a name="sqlguid-annotation"></a>Annotation sql:guid  
 Un code de mise à jour (updategram) peut faire en sorte que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère une valeur GUID, puis utiliser cette valeur dans le code de mise à jour (updategram). Dans le contexte de DiffGrams, vous pouvez utiliser l'annotation `sql:guid` pour spécifier s'il faut utiliser une valeur GUID générée par SQL Server ou utiliser la valeur fournie dans le code de mise à jour (updategram) pour cette colonne.  
  
 Deux valeurs peuvent être assignées à l'annotation `sql:guid` :  
  
 generate  
 Spécifie que le GUID généré par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être utilisé pour cette colonne de l'opération de mise à jour.  
  
 useValue  
 Spécifie que la valeur spécifiée dans le code de mise à jour (updategram) doit être utilisée pour la colonne. Valeur par défaut.  
  
  
