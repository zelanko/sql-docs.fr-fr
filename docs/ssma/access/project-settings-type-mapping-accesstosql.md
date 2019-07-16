---
title: Paramètres du projet (mappage de Type) (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access data types
- data types, default mappings
- default data type mappings
- Project Settings dialog box, Type Mapping
- SQL Server data types
- Type Mapping settings
ms.assetid: b87b9683-abed-4677-8c50-18bdba704655
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 01154cf477435e9dc5335606d0c11a05aecc492b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68066657"
---
# <a name="project-settings-type-mapping-accesstosql"></a>Paramètres du projet (mappage de Type) (AccessToSQL)
Les paramètres de mappage de Type de projet vous permettent de définir des mappages de type par défaut pour le projet SSMA. Vous pouvez également spécifier des mappages de type pour les objets de base de données individuelle. Pour plus d’informations, consultez [Source de mappage et les Types de données cible](mapping-source-and-target-data-types-accesstosql.md).  
  
Mappage de type est disponible dans le **paramètres du projet** et **par défaut des paramètres de projet** boîtes de dialogue :  
  
-   Utilisez le **paramètres du projet** boîte de dialogue pour définir les options de configuration pour le projet actuel. Pour accéder aux paramètres de mappage de type, sur le **outils** menu, sélectionnez **paramètres du projet**, puis cliquez sur **mappage de Type** dans le volet gauche.  
  
-   Utilisez le **par défaut des paramètres de projet** boîte de dialogue pour définir les options de configuration pour tous les projets. Pour accéder aux paramètres de mappage de type, sur le **outils** menu, sélectionnez **par défaut des paramètres de projet**, sélectionnez le type de projet de migration pour lequel les paramètres sont requis pour être affiché / a été remplacée par  **Version cible de migration** liste déroulante, puis cliquez sur **le mappage de Type** dans le volet gauche.  
  
## <a name="options"></a>Options  
**Type de source**  
Le type de données Access à mapper.  
  
**Type de cible**  
La cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou type de données SQL Azure pour le type de données d’accès spécifié.  
  
Le tableau suivant présente le mappage par défaut entre les types de données source et cible.  
  
|Type de données Access|Type de données de SQL Server|  
|--------------------|------------------------|  
|**binaire [\*... \*]**|**varbinary[\*]**|  
|**boolean**|**bit**|  
|**byte**|**tinyint**|  
|**currency**|**money**|  
|**date**|**datetime**|  
|**decimal**|**float**|  
|**double**|**float**|  
|**guid**|**uniqueidentifier**|  
|**entier**|**smallint**|  
|**long**|**int**|  
|**longbinary**|**varbinary(max)**|  
|**memo**|**nvarchar(max)**|  
|**Mémo** : pour Access 97|**varchar(max)**|  
|**single**|**real**|  
|**texte [\*... \*]**|**nvarchar[\*]**|  
|**texte [\*... \*]** : pour Access 97|**varchar[\*]**|  
  
**Ajouter**  
Cliquez pour ajouter un type de données à la liste de mappage.  
  
**Edition**  
Cliquez pour modifier un type de données dans la liste de mappage.  
  
**Supprimer**  
Cliquez pour supprimer le mappage de type de données sélectionnée dans la liste de mappage.  
  
**Rétablir les valeurs par défaut**  
Cliquez pour réinitialiser tous les mappages de type de données pour les valeurs par défaut SSMA.  
  
## <a name="see-also"></a>Voir aussi  
[Mappage de types de données sources et cibles](mapping-source-and-target-data-types-accesstosql.md)  
[Reference(Access) d’Interface utilisateur](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
