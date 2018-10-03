---
title: Type de données permission (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Permission Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Permission
helpviewer_keywords:
- Permission data type
ms.assetid: 5f309544-59f8-4432-b1eb-b7c1a049f8df
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8d12fb71a8ed19ca083e8ec506fba6338f6b58a7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48101940"
---
# <a name="permission-data-type-assl"></a>Type de données Permission (ASSL)
  Définit un type de données primitif abstrait qui fournit des informations sur une autorisation individuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Permission>  
   <Name>...</Name>  
   <ID>...</ID>  
   <CreatedTimestamp>...</CreateTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <RoleID>...</RoleID>  
   <Description>...</Description>  
   <Process>...</Process>  
   <ReadDefinition>...</ReadDefinition>  
   <Read>...</Read>  
   <Write>...</Write>  
   <Annotations>...</Annotations>  
</Permission>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|None|  
|Types de données dérivés|[CubePermission](../objects/cubepermission-element-assl.md), [DatabasePermission](../objects/databasepermission-element-assl.md), [DimensionPermission](permission-data-type-assl.md), [MiningModelPermission](../objects/miningmodelpermission-element-assl.md), [MiningStructurePermission](../objects/miningstructurepermission-element-assl.md)|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[Annotations](../collections/annotations-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [Description](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [nom](../properties/name-element-assl.md), [Processus](../properties/process-element-assl.md), [en lecture](../properties/read-element-assl.md), [ReadDefinition](../properties/readdefinition-element-assl.md), [RoleID](../properties/roleid-element-assl.md), [écrire](../properties/write-element-assl.md)|  
|Éléments dérivés|None|  
  
## <a name="remarks"></a>Notes  
 `Permission` sert comme type de base abstrait pour un nombre de types d’autorisation dérivés utilisés dans une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Ce type de données a les validations suivantes sous la valeur 2 de DeploymentMode (mode de serveur tabulaire).  
  
-   *Processus* attribut par défaut a la valeur `False`, sauf si l’utilisateur a le **Actualiser** autorisation. Pour les utilisateurs avec le **Actualiser** autorisation la *processus* attribut a la valeur `True`.  
  
-   *ReadDefinition* attribut a la valeur `None`; toute autre valeur génère une erreur.  
  
-   *En lecture* attribut a la valeur `Allowed` pour les utilisateurs avec le **utilisateur** autorisation et `None` lorsque les utilisateurs sont affectés à la **Actualiser** autorisation ; si un utilisateur possède à la fois **Utilisateur** et **Actualiser** autorisations, puis l’attribut est défini sur `Allowed`. Pour les utilisateurs avec des privilèges d'administrateur, la valeur d'attribut est définie sur `Allowed`.  
  
-   *Écrire* attribut a la valeur `None`; toute autre valeur génère une erreur.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément role &#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
