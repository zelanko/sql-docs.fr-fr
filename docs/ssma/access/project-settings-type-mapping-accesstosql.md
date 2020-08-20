---
description: Paramètres du projet (mappage de type) (AccessToSQL)
title: Paramètres du projet (mappage de type) (AccessToSQL) | Microsoft Docs
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
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 48054f25a5c7156a6d9d25d4770d19437d9dbadf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454301"
---
# <a name="project-settings-type-mapping-accesstosql"></a>Paramètres du projet (mappage de type) (AccessToSQL)
Les paramètres de projet de mappage de type vous permettent de définir des mappages de types par défaut pour le projet SSMA. Vous pouvez également spécifier des mappages de type pour des objets de base de données individuels. Pour plus d’informations, consultez [mappage des types de données source et cible](mapping-source-and-target-data-types-accesstosql.md).  
  
Le mappage de type est disponible dans les boîtes de dialogue **paramètres du projet** et **paramètres du projet par défaut** :  
  
-   Utilisez la boîte de dialogue **paramètres du projet** pour définir les options de configuration du projet actif. Pour accéder aux paramètres de mappage de type, dans le menu **Outils** , sélectionnez **paramètres du projet**, puis cliquez sur **mappage de type** dans le volet gauche.  
  
-   Utilisez la boîte de dialogue **paramètres du projet par défaut** pour définir les options de configuration de tous les projets. Pour accéder aux paramètres de mappage de type, dans le menu **Outils** , sélectionnez **paramètres de projet par défaut**, sélectionnez le type de projet de migration pour lequel les paramètres doivent être affichés/Changed à partir de la liste déroulante de la **version cible** de la migration, puis cliquez sur **mappage de type** dans le volet gauche.  
  
## <a name="options"></a>Options  
**Type de source**  
Type de données Access à mapper.  
  
**Type de cible**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Type de données cible ou SQL Azure pour le type de données Access spécifié.  
  
Le tableau suivant montre le mappage par défaut entre les types de données source et cible.  
  
|Type de données Access|Type de données de SQL Server|  
|--------------------|------------------------|  
|**binaire [ \* .. \* ]**|**varbinary [ \* ]**|  
|**boolean**|**bit**|  
|**byte**|**tinyint**|  
|**accès**|**money**|  
|**date**|**datetime**|  
|**decimal**|**float**|  
|**double**|**float**|  
|**guid**|**uniqueidentifier**|  
|**integer**|**smallint**|  
|**long**|**int**|  
|**autorise**|**varbinary(max)**|  
|**mémo**|**nvarchar(max)**|  
|**MEMO** -pour Access 97|**varchar(max)**|  
|**single**|**real**|  
|**texte [ \* .. \* ]**|**nvarchar [ \* ]**|  
|**texte [ \* .. \* ]** -pour Access 97|**VARCHAR [ \* ]**|  
  
**Ajouter**  
Cliquez pour ajouter un type de données à la liste de mappage.  
  
**Modifier**  
Cliquez pour modifier un type de données dans la liste mappage.  
  
**Remove**  
Cliquez pour supprimer le mappage de type de données sélectionné de la liste de mappage.  
  
**Rétablir les valeurs par défaut**  
Cliquez pour réinitialiser tous les mappages de type de données aux paramètres SSMA par défaut.  
  
## <a name="see-also"></a>Voir aussi  
[Mappage de types de données sources et cibles](mapping-source-and-target-data-types-accesstosql.md)  
[Référence de l’interface utilisateur (accès)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
