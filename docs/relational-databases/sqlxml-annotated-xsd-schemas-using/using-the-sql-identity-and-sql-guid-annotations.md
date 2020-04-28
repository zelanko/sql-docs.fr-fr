---
title: Utilisation des annotations sql:identity et sql:guid
description: 'Découvrez comment utiliser les annotations SQL : Identity et SQL : GUID dans un schéma XSD pour définir le comportement d’un mise à jour XML.'
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
ms.reviewer: ''
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f581c1a5c0d925d48df5a16d95cdb141e2d48f83
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81388106"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a>Utilisation des annotations sql:identity et sql:guid
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Vous pouvez spécifier les annotations **SQL : Identity** et **SQL : GUID** dans un schéma XSD sur tout nœud mappé à une colonne de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]base de données dans. Tandis que le format mise à jour prend en charge les attributs **attribut updg : at-Identity** et **attribut updg : GUID** , le format DiffGram ne le fait pas. L’attribut **attribut updg : at-Identity** définit le comportement de la mise à jour d’une colonne de type Identity. L’attribut **attribut updg : GUID** vous permet d’obtenir une valeur GUID à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] partir de et de l’utiliser dans le mise à jour. Pour plus d’informations et pour obtenir des exemples fonctionnels, consultez [insertion de données à l’aide de XML codes &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
 Les annotations **SQL : Identity** et **SQL : GUID** étendent cette fonctionnalité aux DiffGrams.  
  
 Lorsque vous exécutez un DiffGram, il est d'abord converti en un code de mise à jour (updategram), puis le code de mise à jour (updategram) est exécuté. En spécifiant les annotations **SQL : Identity** et **SQL : GUID** dans le schéma XSD, vous définissez en fait le comportement d’un mise à jour. Par conséquent, toutes les annotations sont décrites dans le contexte d'un code de mise à jour (updategram). Les annotations peuvent être utilisées à la fois pour les DiffGrams et les codes de mise à jour (updategram) ; toutefois, les codes de mise à jour (updategram) offrent déjà un moyen plus puissant pour gérer l'identité et les valeurs GUID.  
  
 Les annotations **SQL : Identity** et **SQL : GUID** peuvent être définies sur un élément de contenu complexe.  
  
## <a name="sqlidentity-annotation"></a>Annotation sql:identity  
 Vous pouvez spécifier l’annotation **SQL : Identity** dans le schéma XSD sur tout nœud mappé à une colonne de base de données de type Identity. La valeur spécifiée pour cette annotation définit le mode de mise à jour de la colonne de type IDENTity (à l’aide de la valeur fournie dans mise à jour pour modifier la colonne ou en ignorant la valeur, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]auquel cas une valeur générée est utilisée pour cette colonne).  
  
 Deux valeurs peuvent être assignées à l’annotation **SQL : Identity** :  
  
 ignore  
 Ordonne au code de mise à jour (updategram) d'ignorer toute valeur fournie dans le code de mise à jour (updategram) pour cette colonne et de compter sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour générer la valeur d'identité.  
  
 useValue  
 Ordonne au code de mise à jour (updategram) d'utiliser la valeur fournie dans le code de mise à jour (updategram) pour mettre à jour la colonne de type IDENTITY. Un code de mise à jour (updategram) ne vérifie pas si la colonne est une valeur d'identité ou pas.  
  
 Si le mise à jour spécifie une valeur pour la colonne de type IDENTity, **SQL : Identity = "useValue"** doit être spécifié dans le schéma.  
  
## <a name="sqlguid-annotation"></a>Annotation sql:guid  
 Un code de mise à jour (updategram) peut faire en sorte que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère une valeur GUID, puis utiliser cette valeur dans le code de mise à jour (updategram). Dans le contexte des DiffGrams, vous pouvez utiliser l’annotation **SQL : GUID** pour spécifier s’il faut utiliser une valeur GUID générée par SQL Server ou utiliser la valeur fournie dans mise à jour pour cette colonne.  
  
 Deux valeurs peuvent être assignées à l’annotation **SQL : GUID** :  
  
 generate  
 Spécifie que le GUID généré par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être utilisé pour cette colonne de l'opération de mise à jour.  
  
 useValue  
 Spécifie que la valeur spécifiée dans le code de mise à jour (updategram) doit être utilisée pour la colonne. Il s'agit de la valeur par défaut.  
  
  
