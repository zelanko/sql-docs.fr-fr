---
title: Utilisation des annotations sql:identity et sql:guid
description: Apprenez à utiliser le sql:identity et sql:guid annotations dans un schéma XSD pour définir le comportement d’un updategram XML.
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
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388106"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a>Utilisation des annotations sql:identity et sql:guid
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Vous pouvez spécifier le **sql:identity** et **sql:guid** annotations dans un schéma XSD sur n’importe quel nœud qui cartes à une colonne de base de données dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Alors que le format updategram prend en charge le **updg:at-identity** et **updg:guid** attributs, le format DiffGram ne fonctionne pas. **L’attribut updg: à l’identité** définit le comportement dans la mise à jour d’une colonne de type IDENTITY. **L’attribut updg:guid** vous permet d’obtenir une valeur GUID et de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’utiliser dans la mise à jour. Pour plus d’informations et des échantillons de travail, voir [l’insertion de données à l’aide de mises à jour XML &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
 Le **sql:identity** et **sql:guid** annotations étendre cette fonctionnalité à DiffGrams.  
  
 Lorsque vous exécutez un DiffGram, il est d'abord converti en un code de mise à jour (updategram), puis le code de mise à jour (updategram) est exécuté. En spécifiant les annotations **sql:identity** et **sql:guid** dans le schéma XSD, vous définissez en fait le comportement d’un updategram. Par conséquent, toutes les annotations sont décrites dans le contexte d'un code de mise à jour (updategram). Les annotations peuvent être utilisées à la fois pour les DiffGrams et les codes de mise à jour (updategram) ; toutefois, les codes de mise à jour (updategram) offrent déjà un moyen plus puissant pour gérer l'identité et les valeurs GUID.  
  
 **L’identité sql et** **sql:guid** annotations peuvent être définies sur un élément de contenu complexe.  
  
## <a name="sqlidentity-annotation"></a>Annotation sql:identity  
 Vous pouvez spécifier **l’annotation d’identité sql:identity** dans le schéma XSD sur n’importe quel nœud qui cartographie une colonne de base de données de type IDENTITY. La valeur spécifiée pour cette annotation définit la façon dont la colonne de type IDENTITY est mise à jour (soit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]en utilisant la valeur fournie dans la mise à jour pour modifier la colonne, soit en ignorant la valeur, auquel cas une valeur générée est utilisée pour cette colonne).  
  
 **L’annotation sql:identité** peut être attribuée à deux valeurs:  
  
 ignore  
 Ordonne au code de mise à jour (updategram) d'ignorer toute valeur fournie dans le code de mise à jour (updategram) pour cette colonne et de compter sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour générer la valeur d'identité.  
  
 useValue  
 Ordonne au code de mise à jour (updategram) d'utiliser la valeur fournie dans le code de mise à jour (updategram) pour mettre à jour la colonne de type IDENTITY. Un code de mise à jour (updategram) ne vérifie pas si la colonne est une valeur d'identité ou pas.  
  
 Si la mise à jour spécifie une valeur pour la colonne de type IDENTITY, le **sql: identity"useValue"** doit être spécifié dans le schéma.  
  
## <a name="sqlguid-annotation"></a>Annotation sql:guid  
 Un code de mise à jour (updategram) peut faire en sorte que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère une valeur GUID, puis utiliser cette valeur dans le code de mise à jour (updategram). Dans le contexte de DiffGrams, vous pouvez utiliser **l’annotation sql:guid** pour spécifier s’il faut utiliser une valeur GUID générée par SQL Server ou utiliser la valeur fournie dans le updategram pour cette colonne.  
  
 L’annotation **sql:guid** peut être attribué deux valeurs:  
  
 generate  
 Spécifie que le GUID généré par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être utilisé pour cette colonne de l'opération de mise à jour.  
  
 useValue  
 Spécifie que la valeur spécifiée dans le code de mise à jour (updategram) doit être utilisée pour la colonne. Il s’agit de la valeur par défaut.  
  
  
